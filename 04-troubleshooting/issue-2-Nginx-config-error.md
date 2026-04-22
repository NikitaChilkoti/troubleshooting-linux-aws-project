# Issue 2: Nginx Config Error

## What does this mean?

Nginx fails to start due to a configuration mistake.

---

## What did I do to simulate this error?

Just removed a semicolon after the port from config:

```nginx
proxy_pass http://127.0.0.1:5000
```

---

## What happened?

Nginx failed to restart.

---

## How to debug?

```bash
sudo nginx -t
```

It showed syntax error.

---

## This needs a fix. How to fix it?

Add the missing semicolon:

```nginx
proxy_pass http://127.0.0.1:5000;
```

Then:

```bash
sudo systemctl restart nginx
```

---

## Always test config before restart:

```bash
nginx -t
```
Simulated another issue [related to permission](./issue-3-403-forbidden.md)
