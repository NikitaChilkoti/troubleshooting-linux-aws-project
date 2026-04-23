# Nginx Logging Analysis

## What are we doing?

In this section, we learn how to debug issues using Nginx logs.

Instead of guessing what went wrong, we:

* read logs
* understand errors
* fix the problem

---

## Where are Nginx logs stored?

Nginx stores logs at:

```bash
/var/log/nginx/access.log
/var/log/nginx/error.log
```

## Types of Logs

### 1. Access Log

```bash
sudo tail -f /var/log/nginx/access.log
```

This shows:

* incoming requests
* client IP
* status codes (200, 404, etc.)

---

### 2. Error Log (Most Important)

```bash
sudo tail -f /var/log/nginx/error.log
```

This shows:

* server errors
* backend connection issues
* configuration problems

---

## Real Example: 502 Bad Gateway

### Problem

Website shows:

```text
502 Bad Gateway
```

---

### Debug Using Logs

```bash
sudo tail -f /var/log/nginx/error.log
```

Example output:

```text
connect() failed (111: Connection refused)
```

---

### What does this mean?

Nginx tried to connect to the backend, but the backend (Flask) is not running.

---

### How to Fix?

```bash
source venv/bin/activate
python3 app.py
```

---

## Another Example: File Not Found

Error log may show:

```text
No such file or directory
```

This means:

* file path is wrong
* or file does not exist

---

## To see logs in real-time, use this command during debugging:

```bash
sudo tail -f /var/log/nginx/error.log
```
---

## So, logs are the most reliable for spotting the issue. Next up, we should be doing ____
