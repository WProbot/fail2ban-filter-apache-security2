Fail2Ban Filter for Apache2 ModSecurity2
========================================

Note: _This will only work if you have full access to your web server's `/etc/fail2ban/` files._

How to use:

* Install, enable, and configure [ModSecurity2](https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_security-with-apache-on-debian-ubuntu) to your web server.
* Copy [/filter.d/apache-security2.conf](https://github.com/wpkc/fail2ban-filter-apache-security2/blob/master/filter.d/apache-security2.conf) from this repository to `/etc/fail2ban/filter.d/`
* Add a `[apache-security2]` section to the Jails section of your `/etc/fail2ban/jail.local` file...
```python
	[apache-security2]
	port     = http,https
	logpath  = %(apache_error_log)s
	maxretry = 4
	enabled = true
```
* Restart Fail2Ban: `service fail2ban restart`


Additional Notes:

* If using CloudFlare on the web site, please see the [fail2ban-action-cloudflare-restv4](https://github.com/wpkc/fail2ban-action-cloudflare-restv4) repository for an updated CloudFlare action configuration file.

More info: <https://www.kazimer.com/update-fail2ban-apache-security-conf-filter-for-security2-module/>
