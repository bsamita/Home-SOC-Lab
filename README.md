# Home SOC Lab

![Lab Status](https://img.shields.io/badge/status-active-success)
![Platform](https://img.shields.io/badge/platform-Linux-blue)

A fully functional Security Operations Center built for hands-on learning and threat detection practice.

## Objectives

- Build practical SOC analyst skills
- Understand SIEM configuration and log analysis
- Practice incident detection and response
- Learn network traffic analysis
- Create custom detection rules

## 🏗️ Architecture
```
                    Internet
                       |
                  [pfSense]
                       |
        +--------------+---------------+
        |              |               |
   [Wazuh SIEM]  [Security Onion]  [Endpoints]
        |              |               |
    Log Analysis   IDS/IPS      Generate Events
```

## 🛠️ Technologies

| Component | Purpose | Version |
|-----------|---------|---------|
| Wazuh | SIEM & Log Analysis | 4.x |
| Security Onion | Network Monitoring | 2.x |
| pfSense | Firewall & Routing | 2.7.x |
| Suricata | IDS/IPS | Latest |
| Zeek | Network Analysis | Latest |
| Wireshark | Packet Analysis | Latest |

## 📁 Repository Structure
```
Home-SOC-Lab/
├── README.md
├── architecture/
│   ├── network-diagram.png
│   └── data-flow.md
├── configs/
│   ├── pfsense/
│   │   ├── firewall-rules.txt
│   │   └── interface-config.md
│   ├── wazuh/
│   │   ├── ossec.conf
│   │   ├── custom-rules.xml
│   │   └── agent-deployment.md
│   └── security-onion/
│       └── setup-notes.md
├── detection-rules/
│   ├── brute-force-detection.xml
│   ├── port-scan-alert.xml
│   └── suspicious-powershell.xml
├── incident-scenarios/
│   ├── scenario-01-brute-force.md
│   ├── scenario-02-malware-detection.md
│   └── scenario-03-data-exfiltration.md
├── screenshots/
│   ├── wazuh-dashboard.png
│   ├── security-onion-alerts.png
│   └── traffic-analysis.png
└── docs/
    ├── installation-guide.md
    ├── troubleshooting.md
    └── lessons-learned.md
```

## 🚀 Getting Started

### Prerequisites
- VirtualBox or VMware
- Minimum 16GB RAM
- 100GB free disk space
- Basic Linux knowledge

### Installation Steps

1. **Set up pfSense**
```bash
   # Download pfSense ISO
   # Create VM with 2 NICs (WAN + LAN)
   # Follow installation wizard
```
   [Detailed Guide](docs/installation-guide.md)

2. **Deploy Wazuh SIEM**
```bash
   curl -sO https://packages.wazuh.com/4.x/wazuh-install.sh
   bash wazuh-install.sh -a
```
   [Wazuh Configuration](configs/wazuh/)

3. **Install Security Onion**
   - Download Security Onion ISO
   - Deploy as standalone or distributed
   - Configure network sensors
   
   [Security Onion Setup](configs/security-onion/setup-notes.md)

## 📊 Key Features

### Custom Detection Rules
- Failed SSH login attempts (10+ in 5 minutes)
- Port scanning detection
- Suspicious PowerShell execution
- File integrity monitoring
- Malware hash detection

### Incident Scenarios
Simulated attacks for practice:
- **Scenario 1:** Brute Force Attack Detection
- **Scenario 2:** Malware Download & Execution
- **Scenario 3:** Data Exfiltration via DNS Tunneling

[View All Scenarios](incident-scenarios/)

## 📈 What I Learned

- **SIEM Configuration:** Log source integration, parsing, and normalization
- **Alert Tuning:** Reducing false positives while maintaining detection coverage
- **Firewall Management:** Rule creation, traffic shaping, VPN configuration
- **Network Analysis:** Protocol analysis, traffic baselining, anomaly detection
- **Incident Response:** Triage, investigation, containment procedures

## 🔍 Sample Alerts

### Brute Force Detection
```xml
<rule id="100001" level="10">
  <if_sid>5503</if_sid>
  <match>authentication failed</match>
  <same_source_ip />
  <description>Multiple failed login attempts detected</description>
  <group>authentication_failures,</group>
</rule>
```

### Port Scan Alert
```
Alert: Possible port scan detected
Source IP: 192.168.1.100
Target: 192.168.1.50
Ports: 22, 80, 443, 3389, 8080
Time window: 30 seconds
```

## 🎓 Resources Used

- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Security Onion Docs](https://docs.securityonion.net/)
- [pfSense Guide](https://docs.netgate.com/pfsense/)
- MITRE ATT&CK Framework
- SANS SOC Training Materials

## 🔮 Future Improvements

- [ ] Add threat intelligence feeds (MISP, AlienVault OTX)
- [ ] Implement automated response playbooks
- [ ] Create custom Wazuh decoders for application logs
- [ ] Set up honeypots for attacker behavior analysis
- [ ] Integrate with SOAR platform (TheHive)
- [ ] Add cloud log collection (AWS CloudTrail)

## 📝 Blog Posts

I've written detailed articles about this lab:
- [Building a Home SOC Lab from Scratch](link-to-blog)
- [Wazuh SIEM: Custom Rule Creation Guide](link-to-blog)
- [Detecting Brute Force Attacks with SIEM](link-to-blog)

## 📧 Contact

Questions? Suggestions? Reach out:
- LinkedIn: https://www.linkedin.com/in/bsamita/
- Email: brownsamita@gmail.com

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

**⭐ If you find this useful, please star the repo!**
