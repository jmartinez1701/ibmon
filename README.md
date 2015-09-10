#
####################
# Service: IBMon
# Script: README
# Usage: README for IBMon
####################

Files
=====
grid.pl:                        Creates the grid file - For Zenoss use only
ib_clear_zenoss_errors.pl:      Clears resolved IB events in Zenoss - For Zenoss use only
ib_counters.sh:                 Consoles into perfmgr, pulls counters, clears counters                  
ib_links.pl:                    Looks for slow/non-optimal links
ib_rosetta.pl:                  Converts error/performance messages to human readable syslog messages
ibmon:                          Init script for daemon
ibmon.conf:                     Configuration file for ibmon scripts
ibmon.pl:                       Calls errors, performance, links, grid and rosetta scripts.  Runs as daemon
ibmon_cleaner.pl:               Cleans up old ibnet_map files
ibmon_init.pm:                  Reads in configuration file to ibmon scripts
README:                         This README file

Requirements:
1) Linux Environment 
2) infiniband-diags, libibmad, libibumad, opensm-libs, opensm(3.3.17-4 or greater)
3) ib-node-name-map created for your system (located at /etc/opensm/ib-node-name-map)

How to run ibmon
1) Install RPM ibmon-X.rpm
2) Configure config file at /etc/sysconfig/ibmon.conf (sample file at /usr/local/ibmon/ibmon.conf.sample)
3) Run: "service ibmon start" OR "/etc/rc.d/init.d/ibmon start" to start ibmon

ibmon service options:
start) Start ibmon daemon
stop) Stop ibmon daemon
status) Check to see if daemon/DST mode running
dst-start) Enable DST* mode for ibmon
dst-stop) Disable DST* mode for ibmon 

*DST: Dedicated Service Time
DST mode can be used when the IB fabric is reserved for administrative work or maintenance.  
(i.e. hardware being replaced, fabric being tested, nodes being added/removed in large 
groups that will alert, etc.).  This mode will prevent the IB errors from reporting due 
to what ever work is going on during this DST.  The daemon though will continue to run to 
collect counters during this time. Note that sleep cycle for ibmon will continue as
normal but when service wakes up to check errors, if DST mode enabled, will ignore the
error checking.

This Infiniband monitoring service was developing at the Los Alamos National Laboratory 
High Performance Computing Division (LANL HPC) and is locally grown and maintained. 
It was originally designed by Susan Coulter for LANL's HPC needs and has been modified for 
more general use.  If you have any questions or comments about the monitoring tools, 
please feel free to contact:

Primary:
Jesse Martinez
Los Alamos National Laboratory HPC Network Admin
jmartinez@lanl.gov

Secondary:
Los Alamos National Laboratory HPC Network Team
hpc3-network@lanl.gov

Enjoy!
