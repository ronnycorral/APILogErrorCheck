# APILogErrorCheck
This is something I had to cobble together to check log files for error messages but we couldn't install the standard tools you would normally use for something like this and it needed to be done by the weekend.
<p>
The logfiles were written to /var/log/syslog/HOSTS/yyyy/mm/dd/(service name)/(IP address)/user.log. The hosts were load balanced EC2 instances that could be created at any time. Since there were no error message standards between the different engineering teams I would be looking for different messages. Oh and this had to be written in Python 2.4 which limited what I was able to do there as well.
<ul>
<li>apilogcheck.conf - config file that defines service to monitor and error messages to look for
<li>apilogcheck - Python script that does a sort of tail -f and a regular expression check of the error messages I was to alert on
<li>watchapilogcheck - Bash script run from cron on a regular basis to make sure instances of apilogcheck were running for the log files we wanted to watch
</ul>
