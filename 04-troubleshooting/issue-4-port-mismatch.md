# Issue 4: Port Mismatch

## What does this mean?

Backend is running, but on a different port than expected.

---

## What I did to simulate this?

Changed Flask port to 5001

---

## What happened?

Website showed:

```text
502 Bad Gateway
```

---

## How to debug?

Check running ports:

```bash
ss -tulpn | grep python
```

Found app running on port 5001

---

## Checked Nginx config:

```nginx
proxy_pass http://127.0.0.1:5000;
```

---

## How to fix it?

Matched ports:

* Either change Flask to 5000
* Or update Nginx config

---

## So, 502 is not always backend down, it can be wrong port too.

---
