# T1110.001 (bonus): Hydra SSH brute force from Kali

- **Attack:** Hydra against user labtarget over SSH, 6 passwords tried in parallel (5 wrong, 1 correct: hunter2)
- **Detected:** 5x rule 5760 "sshd: authentication failed", level 5, at 11:20:12-11:20:14 UTC
- **Gap found:** the successful login ("Accepted password for labtarget", 11:20:12 UTC) is in /var/log/auth.log but Wazuh raised NO alert for it. Likely cause: the session opened and closed in the same second, alongside 5 other near-simultaneous connections, and the decoder missed that one line.
- **Also:** no brute-force correlation alert fired; only 5 failed attempts, below Wazuh's default threshold.
- **Takeaway:** default Wazuh config detects repeated failures but can silently miss the successful login in a fast, parallel brute force. A real SOC would need log-collection tuning or a dedicated correlation rule for this.
- **Cleanup:** labtarget user removed
