# Issue 1: 502 bad gateway (Backend down)

## What does this mean?
This error means Nginx is working, but it cannot connect to the backend (Flask)

---

## What I did to simulate this error?

I just stopped the Flask app:

```bash
Ctrl + C
```

---

## What happened?

When the website was opened: It shows '502 Bad Gateway'

---

## How to debug?

Step 1: Check if backend is running

```bash
ps aux | grep python
```

Result: No Flask process found

---

## This needs a fix clearly. How to fix it?

```bash
source venv/bin/activate
python3 app.py
```

---

## Now the website is up and running. Simulated another issue __.
