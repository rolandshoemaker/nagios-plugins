nagios-plugins
=========

various plugins for nagios (or icinga) for monitoring a bunch of random stuff

- check_airport (*perl*) - Monitor average client signal and noise as well as number of clients connected to a airport extreme through snmp - **pretty much done**, don't think it really needs more work (could add warn/crit levels for noise/strength...)
- check_bat (*perl*) - Monitor batter status by monitoring the freedesktop UPower object (only tested on ubuntu) - **pretty much done**, could use command line warn/crit parameters (is currently set inside the script).
- check_hplog (*perl*) - Monitor temperature sensors and fan speeds on HP server hardware - **wip**, need to finish fan stuff and want to add various other power infomation.
- check_interface (*perl*) - Monitor bytes flowing through a network interface - **pretty much done**, don't forsee doing much more work since it's insanely simple, maybe monitor multiple interfaces with one command.
- check_lxc (*python*) - Monitor information about LXC containers running on a host (# running,stopped,frozen,active and total and average memory used by containers) - **pretty much done**, originally intended functionality is done (check number running,stopped,active, and frozen as well as total memory used, average memory, and filtering of containers. I would like to add more cgroup information later though...
- check_squid (*perl*) - Monitor if a squid3 proxy is working and if the check is run on the server running the proxy check how many active connections there are - **pretty much done**, could probably use some cleanup. 
