# Monitoring Tools (Grafana, Prometheus, Loki, Windows Exporter)

This repository demonstrates how to set up a monitoring stack using **Grafana**, **Prometheus**, **Loki**, **Promtail**, and **Windows Exporter**.  
It’s a local demo of the same architecture I use in workplace environments to monitor applications and servers.

---

## ⚠️ Disclaimer
For security reasons, all examples here are recreated on my **local machine** with safe, generic configurations.  
No sensitive company data or configurations are included. The steps, however, reflect how the stack works in real-world setups.

---

## 📖 What You Will Find Here
This project walks through the end-to-end process of setting up and running a monitoring stack:

1. [Introduction](docs/01-introduction.md)  
   Why monitoring matters, plus a high-level overview of the stack.  

2. [Setup](docs/02-setup.md)  
   Steps to install Grafana, Prometheus, Loki, Promtail, and Windows Exporter.  

3. [Configuration](docs/03-configuration.md)  
   Example YAML files for Prometheus, Loki, and Promtail with explanations.  

4. [Visualization](docs/04-visualization.md)  
   Building dashboards in Grafana to display system metrics (CPU, memory) and application logs.  

5. [Automation](docs/05-automation.md)  
   Batch and PowerShell scripts to start/stop the stack, plus notes on common issues.  

6. [Use Cases](docs/06-use_cases.md)  
   Real-world scenarios where the stack helps in monitoring and troubleshooting applications.  

7. [Lessons Learned](docs/07-lessons_learned.md)  
   Challenges faced during setup and the fixes applied.  

---

## 🛠 Tools Used
- **Grafana**: Dashboard and visualization platform.  
- **Prometheus**: Metrics collection and querying.  
- **Loki**: Log aggregation system.  
- **Promtail**: Agent that ships logs to Loki.  
- **Windows Exporter**: Exposes Windows system metrics to Prometheus.  


