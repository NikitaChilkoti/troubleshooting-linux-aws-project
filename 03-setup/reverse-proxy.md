# Right now, our Flask app is running on:

```text
http://your-ip:5000
```
But in real-world applications users should NOT access backend directly.

Instead, we use **Nginx as a reverse proxy**

---

## What is a Reverse Proxy?

To state it in the easiest way, see Nginx sits in front of your app and receives requests from users, and then it forwards them to the backend

---

## The Change is in the Architecture

Before:
```text
User → Flask (port 5000)
```

After:
```text
User → Nginx (port 80) → Flask (port 5000)
```

---

## Step 1: Create Nginx Config File

```bash
sudo nano /etc/nginx/sites-available/flask_app
```

---

## Step 2: Add Configuration

Paste this:

```nginx
server {
    listen 80;

    server_name _;

    location / {
        proxy_pass http://127.0.0.1:5000;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

---

## What does this config do?

* `listen 80` → Nginx listens on port 80
* `proxy_pass` → sends request to Flask (port 5000)
* headers → pass client info

---

## Step 3: Enable Config

```bash
sudo ln -s /etc/nginx/sites-available/flask_app /etc/nginx/sites-enabled/
```

---

## Step 4: Remove Default Config

```bash
sudo rm /etc/nginx/sites-enabled/default
```

Prevents conflict
---

## Step 5: Test Configuration

```bash
sudo nginx -t
```

You should see:

```text
syntax is ok
test is successful
```

---

## Step 6: Restart Nginx

```bash
sudo systemctl restart nginx
```

---

## Step 7: Run Flask App

```bash
source venv/bin/activate
python3 app.py
```

---

## Step 8: Test in Browser

Open:

```text
http://your-public-ip
```

P.S. No Port `:5000`

---

## Expected Result

You should see:

```text
Flask App Running
```

---

## What We Learned

* How reverse proxy works
* How Nginx connects to backend
* Why backend ports should not be public

---

## Common Issues

| Issue       | Cause | Fix  |
| ---------- | ---- | ------- |
| 502 bad gateway | Flask is not running | `ps aux | grep python` |
| 

---

## Important Note

In real production:

* Nginx handles traffic
* Flask app runs in background
* backend is not exposed publicly

---

## Finally we now have a production-like architecture.

```text
User → Nginx → Flask
```

---
Next step is Simulating real-world failures and debugging them
