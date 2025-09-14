# 06 – Use Cases

This monitoring stack isn’t just an experiment; it mirrors real-world needs I’ve seen in financial application support. A few examples:

---

### 1. Watching Server Health
In my workplace, we support applications where downtime or slow response means failed customer transactions. With **Windows Exporter + Prometheus + Grafana**, I can see CPU, memory, and disk usage in real time.  
- If CPU stays above 90% for too long, I know a service is overloading and might need scaling or restart.  
- This visibility reduces guesswork when users complain of “the app being slow.”

---

### 2. Tracing Failed Transactions
When customers complain about failed transfers, we often need to know: *was it network, system, or user error?*  
- **Promtail + Loki** centralizes logs, so instead of digging through scattered text files, I can query logs in Grafana.  
- For example, spotting repeated “connection closed” or "database errors" in Promtail logs pointed me toward a specific issue.  

---

### 3. Proactive Incident Response
Instead of waiting for users to call, the stack helps me act early.  
- Prometheus tracks system metrics and, when combined with alerting rules, could notify me before an outage escalates.  
- Example: seeing disk usage trend upwards lets me clean up logs before the database crashes.  

---

### 4. Supporting Multiple Applications
In banking, we manage many channels (USSD, Internet Banking, Reversal services, etc.).  
- Each service has its own quirks, but centralizing logs and metrics means I don’t need to jump into each individual server manually.  
- This makes investigations faster and less error-prone.
