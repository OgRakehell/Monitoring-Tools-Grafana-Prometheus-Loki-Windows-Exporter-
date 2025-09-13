# Installation

If monitoring is our ship’s navigation system, then installation is the part where we bring each instrument on board and bolt it into place.  
The tools don’t do much on their own — they only shine when wired together.  
We’ll start by installing each component, one piece at a time.

---

## Step 1: Install Prometheus
Prometheus is the metrics collector.

1. Download from the [official Prometheus releases page](https://prometheus.io/download/).
2. Extract the archive to a folder (e.g., `C:\prometheus`).
3. Inside the folder, you’ll see:
   - `prometheus.exe` (the main binary)
   - `prometheus.yml` (the default config file)
4. Run Prometheus with:
   ```powershell
   prometheus.exe --config.file=prometheus.yml
5. Open http://localhost:9090
 to confirm Prometheus is running.

---
## Step 2: Install Windows Exporter
Windows Exporter exposes system metrics to Prometheus.

1. Download the latest .msi installer from the Windows Exporter releases
.

2. Run the installer and accept defaults.

3. Confirm it’s running by visiting http://localhost:9182/metrics
   
You should see raw text output like windows_cpu_time_total.

---
### Step 3: Install Loki  

Loki stores and indexes logs.  

1. **Download** from the [Loki releases](https://github.com/grafana/loki/releases).  
2. **Extract** to a folder (e.g., `C:\loki`).  
3. You’ll need a configuration file (`loki-config.yml`) which we’ll edit in the next section.  
4. **Run Loki** with:  
   ```bash
   loki-windows-amd64.exe --config.file=loki-config.yml

---

### Step 4: Install Promtail

Promtail ships logs to Loki.

- Download from the [Loki releases page](https://github.com/grafana/loki/releases) (look for the Promtail binary).
- Extract to a folder (e.g., `C:\promtail`).
- Edit `promtail-config.yml` (we’ll cover this in detail later).
- Run Promtail with:

  ```powershell
  promtail-windows-amd64.exe --config.file=promtail-config.yml

---
### Step 5: Install Grafana

Grafana visualizes metrics and logs.

1. Download the Windows installer from the [Grafana website](https://grafana.com/grafana/download).
2. Run the installer (defaults are fine).
3. Open Grafana at: [http://localhost:3000](http://localhost:3000)
4. **Default login credentials**:  
   - Username: `admin`  
   - Password: `admin` (you’ll be prompted to change it)
  
---
## Recap

- **Prometheus** is running at `:9090`.  
- **Windows Exporter** is serving metrics at `:9182`.  
- **Loki** is running at `:3100`.  
- **Promtail** is forwarding logs to Loki.  
- **Grafana** is ready at `:3000`.  

With all tools installed, we’re ready to connect them through configuration.






