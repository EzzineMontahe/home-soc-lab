# home-soc-lab

A home Security Operations Center lab: detect simulated attacks with Wazuh, map them to MITRE ATT&CK, and (planned) turn alerts into prioritised service-desk tickets.

Everything runs in VirtualBox on one laptop. Attacks are run only against my own lab VMs.

## Lab setup

| VM | Role |
|---|---|
| wazuh-server | Wazuh 4.14 all-in-one (manager, indexer, dashboard), Ubuntu Server 22.04 |
| wazuh-agent | Monitored Ubuntu host with the Wazuh agent and Atomic Red Team |

## Detection results

| Test | MITRE ID | Wazuh rule | Level | Time to detect |
|---|---|---|---|---|
| T1136.001-1 Create local account | T1136 (as tagged by Wazuh) | 5902 | 8 | ~2 s |
| T1110.001-5 Sudo brute force | T1110.001 | 5503, 5401 | 5 | ~4 s |

Details per test are in [detections/](detections/).

## Roadmap

- [x] Wazuh server and agent
- [x] Atomic Red Team tests 1 and 2
- [ ] Cron persistence test (T1053.003)
- [ ] SSH brute force with Hydra
- [ ] Alerts to n8n, tickets with priority
- [ ] Suricata (network scan detection)
- [ ] Ansible deployment, Grafana dashboard, IP-block response playbook
