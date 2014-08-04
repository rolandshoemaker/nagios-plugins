#!/usr/bin/perl

use warnings;
use strict;

use lib qw( /usr/lib/nagios/plugins );
use utils qw(%ERRORS $TIMEOUT &print_revision &support &usage);
use List::Util qw(sum);
use Getopt::Std;

sub mean_snmp() {
	my @attrs;

	for (my $i = 0; $i < scalar(@_); $i++) {
		my @line = split(' ', $_[$i]);
		push(@attrs, $line[scalar(@line)-1]);
	}

	if (scalar(@attrs) >= 1) {
		return &mean(@attrs);	
	}
}

sub mean {
	return sum(@_)/@_;
}

my %opts = ();
getopts("snH:", \%opts);

if (!defined $opts{H}) {
	print "host (-H) is required\n";
	exit(1);
}

my @stats;
if (defined $opts{H}) {
	@stats = `snmpwalk -v 2c -m AIRPORT-BASESTATION-3-MIB -c public $opts{H} SNMPv2-SMI::enterprises.63.501.3.2.1`;
	my @clientstr = split(' ',$stats[0]);
	my $clients = $clientstr[scalar(@clientstr)-1];
	@stats = [];
	@stats = `snmpwalk -v 2c -m AIRPORT-BASESTATION-3-MIB -c public $opts{H} SNMPv2-SMI::enterprises.63.501.3.2.2.1.6`;
	my $stren = &mean_snmp(@stats);
	@stats = [];
	@stats = `snmpwalk -v 2c -m AIRPORT-BASESTATION-3-MIB -c public $opts{H} SNMPv2-SMI::enterprises.63.501.3.2.2.1.7`;
	my $noise = &mean_snmp(@stats);
	print "WIRELESS - Clients: ".$clients.", Average Strength: ".$stren." dB, Average Noise: ".$noise." dB|clients=".$clients."; strength=".$stren."dB; noise=".$noise."dB;";
	exit $ERRORS{'OK'};
}

