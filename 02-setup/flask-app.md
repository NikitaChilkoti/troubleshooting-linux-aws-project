## Flask App

## What are we doing?

In this step, we are creating a simple backend application using Python.

This app will:
run on port 5000
respond to browser requests

Later, Nginx will connect to this app.

## Before that what is Flask?

Flask is a lightweight Python web framework. It basically helps Python talk to the browser.

---

## Step 1: Create Project Folder

```bash
mkdir app
cd app
```

---

## Step 2: Create Virtual Environment

```bash
python3 -m venv venv
```

---

## Step 3: Activate Virtual Environment

```bash
source venv/bin/activate
```

You will see:

```bash
(venv) ubuntu@...
```

---

## Why are we using venv?

It creates an isolated environment so that:
system Python is not affected
dependencies don’t conflict

---

## Step 4: Install Flask

```bash
pip install flask
```

---

## Common Issue (Important Learning)

If you try installing Flask without venv, you may see:

```text
externally-managed-environment error
```

So the fix is to use virtual environment (as above)

---

## Step 5: Create App File

```bash
nano app.py
```

Paste this:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Flask App Running"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

## Step 6: Run the App

```bash
python3 app.py
```

---

## Step 7: Test in Browser

Open:

```text
http://your-public-ip:5000
```

You should see:
Flask App Running

---

## If It Doesn’t Work

### Issue: Site not opening

Fix:
Check AWS Security Group
Add rule:

| Type       | Port | Source  |
| ---------- | ---- | ------- |
| Custom TCP | 5000 | Your IP |

---

### Issue: Flask not found

Cause:
Virtual environment not activated

Fix:

```bash
source venv/bin/activate
```

---

## We Learned

* How to run a backend app
* How ports work (5000)
* Why virtual environments are used
* How to fix dependency issues

---

## P.S.

This Flask server is not production-ready.
It is only for learning.

Later:
Nginx will act as the real server.

---

## Final Result

We now have a running backend service on port 5000.

---

Next step is to Connect Flask with Nginx, that's Reverse Proxy.
