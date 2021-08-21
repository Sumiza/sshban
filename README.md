# sshban
Couldn't install fail2ban on a specific server but was getting annoyed by someone trying to access it. If you can use fail2ban (https://github.com/fail2ban/fail2ban) I would very much recommend it, but this is an option if need to ban ssh brute force attempts.

* Bans IPs that fail with wrong passwords/users/sshkeys.<br />
* Uses iptables (might update for nftables) to drop IPs.<br />
* Uses Journalctl to ready the last x minutes of the ssh log.
* Can run it every minute with cron but would suggest 5+ minutes.

```
Settings:
checktime=60    #-- Check the last minutes of log for failed login attempts - 60 = 1 hour / 720 = 12 hours / 1440 = 24 hours
tries=3         #-- Allowed login tries (+one try counts as a disconnect from server) in checktime
bantime=720     #-- Time for IP to stay banned in minutes  - 0 to never remove
```
Custom iptables rules: its safe to add any other IPs to block or white list in iptables, it only removes ones with a comment that has "Bantime:"
