# 07 – Lessons Learned

Setting up these tools wasn’t perfectly smooth. A few hurdles stood out:

---

### 1. YAML Indentation Errors
Prometheus and Loki configs are written in YAML. One misplaced space and the service refuses to start.  
- Lesson: use an editor with YAML linting.

---

### 2. Path Confusion on Windows
At first, my batch script didn’t work because `start` treated quoted paths as window titles, not commands.  
- Fix: add an empty title argument (`start "" cmd /k ...`).  

---

### 3. Port Conflicts
Grafana runs on port 3000 by default. I already had another service using it, so Grafana failed silently.  
- Fix: update `defaults.ini` or start with `--homepath` and custom port.  

---

### 4. Logs Without Context
When Promtail started sending logs, it was just raw lines. Without labels like `job=`, queries in Loki were messy.  
- Fix: add proper `labels` in Promtail config, making logs searchable by application.  

---

### 5. Keeping Services Running
Initially, I ran each binary manually. Forgetting one meant missing data.  
- Fix: batch scripts automated startup and shut down, which felt like a mini DevOps win.

---

## Reflection
These small frustrations were useful. Each time I debugged, I understood not just *how* to run the stack, but *why* it behaves the way it does. That confidence matters more than blindly copying configs.
