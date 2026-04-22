# Health Check Script (Recovery based automation)

## What are we doing?

Even if our Flask service is set up with systemd, failures can still happen.

So we create a simple script that:

* checks if the service is running
* restarts it if it is down

---

## Step 1: Create Script File

```bash
nano ~/app/health-check.sh
```

---

## Step 2: Add Script

```
#!/bin/bash

if systemctl is-active --quiet flask-app
then
  echo "Flask is running"
else
  echo "Flask is down. Restarting..."
  sudo systemctl start flask-app
fi 
```

---

## What does this script do?

* `systemctl is-active` → checks service status
* if running → do nothing
* if not running → restart service

---

## Step 3: Make Script Executable

```bash
chmod +x ~/app/health-check.sh
```

---

## Step 4: Test the Script

Stop the service:

```bash
sudo systemctl stop flask-app
```

Run script:

```bash
./app/health-check.sh
```

Then check:

```bash
sudo systemctl status flask-app
```

The service should be running again.

---

## Step 5: Automate Using Cron

Open crontab:

```bash
crontab -e
```

Add this line:

```bash
* * * * * /home/ubuntu/app/health-check.sh
```

---

## What does this mean?

* `* * * * *` → runs every minute
* script will check service regularly

---

## Why This is Important

In real systems:

* services can crash
* manual fixing is not reliable

Automation ensures:

* faster recovery
* minimal downtime

---

## Common Issues

### Script not running

Check cron:

```bash
crontab -l
```

---

### Permission issues

Make sure script is executable:

```bash
chmod +x ~/app/health-check.sh
```

---

### Service not restarting

Check logs:

```bash
sudo journalctl -u flask-app
```

---

## Finally, the service is monitored and auto-restarted, thus improving system reliability. Next I will update tommorrow.
