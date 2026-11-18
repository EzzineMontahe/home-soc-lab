# T1136.001-1: Create local account (Linux)

- **Technique (Atomic):** T1136.001
- **Wazuh rule:** 5902 "New user added to the system", level 8
- **MITRE tag shown by Wazuh:** T1136 (parent technique, not the sub-technique)
- **Time to detect:** about 2 seconds
- **Source:** auth log on wazuh-agent
- **Cleanup:** done with -Cleanup, user removed
