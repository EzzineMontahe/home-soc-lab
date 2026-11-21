# T1053.003-3: Cron persistence, script added to /etc/cron.d

- **Technique (Atomic):** T1053.003 Scheduled Task/Job: Cron
- **Detected by:** Wazuh syscheck (file integrity monitoring), rule 554 "File added to the system", level 5
- **MITRE tag shown by Wazuh:** none. The T1053.003 label comes from the Atomic test, not from Wazuh
- **Detection time:** within seconds, file added at 21:57:19 UTC (exact time to detect not measured)
- **Finding:** with the default config, the test was NOT detected. Wazuh scans /etc only every 12 hours (frequency 43200). 
- **Fix:** real-time monitoring of the cron folders, see [configs/ossec-syscheck-cron.xml](../configs/ossec-syscheck-cron.xml)
- **Cleanup:** file removed manually (sudo rm), because the Atomic cleanup needs root
