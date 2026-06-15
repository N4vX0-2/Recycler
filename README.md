# Recycler
A Debian Linux Post Engagement Isolation workspace management system to provide device cleanup after engagement for authorized Cybersecurity Professionals

**Recycler Engagement Isolation** is a lightweight workspace controller for Kali/Debian penetration testing systems that use both:


The goal is simple:

> Keep tools, API keys, licenses, and operator configuration persistent, while forcing client/engagement artifacts into a disposable workspace that can be wiped after each engagement.

This project does **not** install offensive tools. It adds an operational hygiene layers around grouped tools and individually installed tools.

---

## Problem this solves

A vulnerability testing machine tends to accumulate client data in many places:

- scanner output
- shell history
- browser downloads
- Burp/ZAP projects
- Metasploit workspace data
- packet captures
- screenshots
- proof files
- temporary files
- SQLMap output
- Nuclei responses
- notes and working reports

Rebuilding the machine after every engagement is clean but extremely time consuming. Keeping everything on one long-lived machine is convenient but risky.

Recycler creates a middle path by removing the the client engagement data from the systems but keeping the tools, settings, and API keys in place, saving time from wiping, reinstalling, updating, tool installation, updating, installing keys, configuration. 

the middle path:

```text
Persistent system state:
  /pentest/                  PTF-managed/other repo-managed tools
  ~/.secrets/                operator API keys
  ~/.config/                 long-term user/tool config
  ~/.ssh/                    operator SSH material
  ~/tools/                   manually installed tools
  ~/wordlists/               persistent wordlists

Disposable engagement state:
  /pentest/_engagements/<client>/
```

---

## Design principles

1. **Separation beats guessing.**  
   Do not try to detect every possible client artifact after the fact. Put engagement artifacts in one known workspace from the start.

2. **PTF/repo managed kits remains persistent.**  
   Installs and updates tools under its base path, commonly `/pentest`. recycler does not wipe PTF tool directories.

3. **Engagement data is disposable.**  
   Scans, loot, reports, temporary files, packet captures, and logs go under `/pentest/_engagements/<client>/`.

4. **Wrappers beat assumptions.**  
   Many tools support output flags. recycler wrappers consistently send output to the active workspace.

5. **No false secure-deletion claims.**  
   SSDs, snapshots, CoW filesystems, journals, and backups can defeat overwrite-based deletion. recycler is a hygiene/control system, not a forensic destruction guarantee, this system does NOT do forensic destruction, it cleans the system of old engagements. You should Rebuild your system from scratch at regular intervals. 

---

## Repository contents

```text
.
├── README.md
├── install.sh
├── uninstall.sh
├── scripts/
│   ├── recycler.sh
│   └── engagement-reset.sh
├── docs/
│   ├── ARCHITECTURE.md
│   ├── SECURITY_MODEL.md
│   ├── WORKFLOW.md
│   └── TOOL_WRAPPERS.md
├── examples/
│   └── quickstart.md
└── .gitignore
```

---
