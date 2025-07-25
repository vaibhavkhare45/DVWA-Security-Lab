# 🔍 Attack Summary: DVWA Brute Force Login with Hydra

## Objective

Demonstrate a **brute force attack** against a login form on DVWA using `hydra` in a safe test environment.

---

## Environment Setup

- **Attacker VM**: Kali Linux
- **Target VM**: OWASP Broken Web Apps (BWA) – DVWA enabled
- **Network Mode**: NAT / Host-only (same subnet)
---

## Attack Flow

1. Set up DVWA on the target machine, and lower its security level to `Low`.
2. Access DVWA from Kali via `http://<target-ip>/dvwa/`.
3. Create two custom wordlists:
   - `users.txt` with sample usernames
   - `passwd.txt` with sample passwords
4. Use the `hydra` tool with the correct POST request syntax to automate login attempts.
5. Monitor the output to capture successful username/password combinations.

---

## Hydra Command Used

```bash
"hydra -L users.txt -P passwd.txt 192.168.52.128 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"
