# Visualization in Grafana

If installation was bringing instruments on board, and configuration was wiring them up, then visualization is the moment you finally see the compass, radar, and gauges in action.  
This is where raw data becomes insight — where numbers and logs transform into decisions.

---

## Step 1: Connect Prometheus to Grafana
1. Open Grafana at [http://localhost:3000](http://localhost:3000).  
2. Login with your credentials (`admin` / `admin` by default).  
3. Go to **Configuration → Data Sources → Add data source**.  
4. Select **Prometheus**.  
5. Set the URL to your Prometheus instance (`http://localhost:9090`).  
6. Click **Save & Test** — you should see “Data source is working.”

---

## Step 2: Connect Loki to Grafana
1. Go back to **Configuration → Data Sources → Add data source**.  
2. Select **Loki**.  
3. Set the URL to your Loki instance (`http://localhost:3100`).  
4. Click **Save & Test**.

---

## Step 3: Build a Dashboard for Metrics
1. Go to **Create → Dashboard → Add Panel**.  
2. In the **Query** section, select **Prometheus**.  
3. Example query: `windows_cpu_time_total` (shows CPU usage).  
4. Customize visualization type (graph, gauge, or bar chart).  
5. Repeat for memory, disk usage, or other metrics.  
6. Save the dashboard with a meaningful name (`System Metrics`).

---

## Step 4: Explore Logs from Loki
1. Go to **Explore** in Grafana.  
2. Select **Loki** as the data source.  
3. Query for logs, e.g., `{job="windows-logs"}`.  
4. You can filter by log level (`ERROR`, `INFO`) or keyword to find specific events.  
5. Add panels to your dashboard showing recent errors or warnings.

---

## Step 5: Organize Your Dashboard
- Use **rows** or **folders** to separate metrics and logs.  
- Add **titles, colors, and thresholds** to make critical metrics stand out.  
- Your dashboard should give a clear overview at a glance — like a ship’s bridge, showing engine load, radar, and alerts all in one view.

---

## Recap
Now you can:
- See CPU, memory, and disk usage in Grafana.  
- View logs collected by Loki, filtered and searchable.  
- Combine metrics and logs on a single dashboard for a full picture of your system.

Visualization turns raw numbers and text into actionable intelligence — the part where monitoring truly becomes useful.
