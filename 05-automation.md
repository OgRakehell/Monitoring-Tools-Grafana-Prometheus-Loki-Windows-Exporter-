# 05 – Automation

Imagine having to start or stop each monitoring component by hand every morning — tedious and error-prone. Automation lets you boot the whole stack with one double-click (or one command). Below are ready-to-use scripts and tips.

---

## start-monitoring.bat
> Save as `scripts/start-monitoring.bat`

```bat
@echo off
echo Starting Monitoring Stack...

:: NOTE: Use an empty title ("") after start to avoid issues with paths that contain spaces.

:: Start Prometheus
start "" cmd /k "cd /d C:\monitoring\prometheus && prometheus.exe --config.file=prometheus.yml"

:: Start Loki
start "" cmd /k "cd /d C:\monitoring\loki && loki-windows-amd64.exe --config.file=loki-local-config.yaml"

:: Start Promtail
start "" cmd /k "cd /d C:\monitoring\promtail && promtail-windows-amd64.exe --config.file=promtail-local-config.yaml"

:: Start Grafana (adjust path to grafana-server.exe if different)
start "" cmd /k "cd /d C:\monitoring\grafana\bin && grafana-server.exe"

echo All services started.
pause

```
Notes

- Replace C:\monitoring\... with your actual install paths.

- start "" supplies a blank window title which prevents start from interpreting a quoted path as the title.

- cmd /k opens a cmd window and keeps it open so you can see logs. Use cmd /c if you want the window to close after process exits.

---
## stop-monitoring.bat

Save as `scripts/stop-monitoring.bat`

```bat
@echo off
echo Stopping Monitoring Stack...

taskkill /IM prometheus.exe /F
taskkill /IM loki-windows-amd64.exe /F
taskkill /IM promtail-windows-amd64.exe /F
taskkill /IM grafana-server.exe /F

echo All processes terminated (if running).
pause
```
Notes

taskkill /F force kills processes. Use carefully.

If you used different binary names (e.g., loki.exe), update the names accordingly.
