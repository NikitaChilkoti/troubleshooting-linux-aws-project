# Issue 3: 403 Forbidden (Permission Issue)

## What does this mean?

The server is running, but access to file is denied.

---

## What did I do to simulate this?

```bash
sudo chmod 000 /var/www/html/index.html
```
So I removed the permissions.

---

## What happened?

Browser showed:

```text
403 Forbidden
```

---

## How to debug?

```bash
ls -l /var/www/html
```

No read permissions

---

## How to fix it?

```bash
sudo chmod 644 /var/www/html/index.html
```

---

## If it is a 403 error, then definitely issue is with granted file permissions. 

Always check:

```bash
ls -l
```

---
## Wanted to look at other issue aspects, so simulated another issue on port mismatch
