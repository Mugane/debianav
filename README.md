# DebianAV
Bash script to set up Antivirus &amp; Antimalware services on Debian/Ubuntu

## Features
- Installs and configures ClamAV, chrootkit, rkhunter, & LMD
- Sets up daily scan jobs and alerts via a `/usr/local/bin/scan_jobs.sh` script file
- Installs a MailGun SMTP proxy over postfix in order to send email alerts of scan results when problems are found.
- Daily scan results are logged to  `/var/log/chkrootkit_scan.log`, `/var/log/rkhunter.log` and  `/var/log/lmd_scan.log`

## Parameters
Global parameters can be used, or the script will prompt for them.

You will need to set up mailgun SMTP credentials (typically at https://app.mailgun.com/app/sending/domains/[your.mailgun.domain]/credentials).

Use the following code to set the variables in the parent shell:
```
export $MAILGUN_SMTP_USER=[mailgun email address]
export $MAILGUN_SMTP_PASS=[mailgun smtp password]
export $ALERT_EMAIL=[mailgun email address]
export $SCAN_HOUR=[0-23]
```

## Usage
```
sudo curl -sLO https://raw.githubusercontent.com/Mugane/debianav/main/av.sh
sudo chmod +x av.sh
sudo ./av.sh
```

## Future features
Features planned for addition in the future:
- fail2ban `sudo tail -f /var/log/fail2ban.log` & ufw
- other utilities? htop?
- logs and offsite logging (especially immutable logging)
