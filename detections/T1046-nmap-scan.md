# T1046: Network Service Scanning (Nmap)

- **Attack:** nmap from Kali against wazuh-agent, two variants
- **Variant 1 (plain SYN scan):** nmap -sS -p- 192.168.56.108 — NO alert generated. A clean SYN scan with no distinguishing payload evades signature-based detection entirely. Real limitation, not a config mistake: this is a known weakness of IDS signatures vs behavioral/threshold-based scan detection, which this lab does not implement.
- **Variant 2 (OS/service fingerprinting):** nmap -sS -sV -O -p- 192.168.56.108 — detected. Suricata rule 86601 "SURICATA ICMPv4 unknown code" fired (ICMP type 8, code 9) from the malformed ICMP probes -O sends to fingerprint the OS. Level 3.
- **MITRE tag shown by Wazuh:** none. Same situation as the T1053.003 test — the T1046 label comes from the Atomic/MITRE mapping, not a Wazuh-native classification.
- **Setup:** Suricata 6.0.4 installed on wazuh-agent, watching enp0s8, 53,488 ET Open rules. Wazuh agent reads /var/log/suricata/eve.json as a localfile (json format) and forwards to the manager, which already ships a built-in Suricata ruleset (rules 86600-86612).
- **Takeaway:** a real SOC needs threshold/anomaly-based scan detection (e.g. Suricata's stream/flow thresholding or a dedicated port-scan detector) to catch a clean scan — signatures alone miss it.
