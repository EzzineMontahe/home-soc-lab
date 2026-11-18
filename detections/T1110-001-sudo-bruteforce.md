# T1110.001-5: SUDO brute force (Debian)

- **Technique (Atomic):** T1110.001 Password Guessing
- **Wazuh rules:** 5503 "PAM: User login failed" (level 5, tagged T1110.001, Credential Access), plus 5401 "Failed attempt to run sudo" (level 5)
- **Time to detect:** about 4 seconds (start 20:12:38 UTC, first alert 20:12:42 UTC)
- **Limit:** only 3 wrong guesses, so no high-level brute-force correlation alert fired
- **Cleanup:** done with -Cleanup, user art removed
