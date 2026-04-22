# Run Flask as a Service (systemd)

## What are we doing?

Right now, we run Flask manually:

```bash
python3 app.py
```

The problem is-

* It stops when terminal closes 
* It is not reliable 

---

## What is systemd?

systemd is a tool in Linux that manages services.

It helps us:

* start services
* stop services
* restart services
* run them automatically

---

## Step 1: Create Service File

```bash
sudo nano /etc/systemd/system/flask-app.service
```

---

## Step 2: Add Configuration

```ini
[Unit]
Description=Flask Application
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/app
ExecStart=/home/ubuntu/app/venv/bin/python /home/ubuntu/app/app.py
Restart=always

[Install]
WantedBy=multi-user.target
```

What does this mean?

* `WorkingDirectory` → where your app is
* `ExecStart` → how to start app
* `Restart=always` → auto-restart if it fails

---

## Step 3: Reload systemd

```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
```

---

## Step 4: Start Service

```bash
sudo systemctl start flask-app
```

---

## Step 5: Enable on Boot

```bash
sudo systemctl enable flask-app
```

---

## Step 6: Check Status

```bash
sudo systemctl status flask-app
```

You should see:

```text
active (running)
```

---

## Step 7: Test It

Close terminal OR stop Flask manually.

Refresh website, and it should still work.

---

## Common Issues

### Service not starting

Check logs:

```bash
sudo journalctl -u flask-app
```

---

### Wrong path

Make sure:

* WorkingDirectory is correct
* Python path is correct

---

## Finally, Flask is running as a background service. Next we will add automation via [Health check script]
