# HP_health_LED_check
A system health LED check script for HP servers. 
Possible reporting to both NHC and Icinga.
Uses ipmitool to poll for result.

Symbolic link needs to be created in NHC script directory and nhc_check_health_led() function configured to be called in nhc.conf to be run by NHC.
Symbolic link needs to be created in Icinga script directory and configured to be called with proper flags in icinga.conf to be run by Icinga.

Script needs to be called by either Icinga or crontab with -c flag to make it possible for NHC to run it.
Every five minutes is a good minimum. 
This is because NHC reads a file with the statuscode rather than asking ipmitool for the result everytime, since it will likely timeout otherwise.


Flags
 -i to read LED status and report to icinga
 -c to create statusfile for NHC
 -p to define path for LED status dir
