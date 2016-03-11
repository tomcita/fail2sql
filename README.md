
Fail2SQL v1.0 by Jordan Tomkinson <jordan@moodle.com> modify by Tomcita

============
Installation
============

1. Create a MySQL database called fail2ban
2. Create fail2ban MySQL user to access fail2ban database (needs INSERT, UPDATE, DELETE)
3. Create table by piping fail2ban.sql into mysql (mysql -u fail2ban -p fail2ban < fail2ban.sql)
4. Edit fail2sql and change home path and sql login details at the top of the file.
5. Update Geo IP Database (./fail2ban -u)
6. Tell fail2ban to call fail2sql by appending to actionban in your action script.

Example for /etc/fail2ban/action.d/iptables.conf

actionban = iptables -I fail2ban-<name> 1 -s <ip> -j DROP
            /usr/local/fail2sql/fail2sql <name> <protocol> <port> <ip>

=====
Usage
=====

fail2sql [-h|-l|-c|-u]
	-h: The help page
	-l: List entries in the database (max 50 showed)
	-c: Clear the database and start fresh
	-u: Update GeoIP database (downloads from maxmind)


=======
Contact
=======

You can contact me at jordan@moodle.com


