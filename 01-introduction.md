# Introduction

Imagine sailing a ship across the ocean with no compass, no sonar, and no map.  
The engines might be roaring, the sails might be catching wind, but without feedback, you would not know if you were drifting toward safe harbor or straight into a storm.

That’s what running servers and applications without monitoring feels like.

Modern systems are complex, noisy, and fragile. A CPU spike here, a memory leak there, or a silent error in the logs can snowball into downtime that frustrates users and costs money. To keep things steady, you need instruments — tools that not only capture what’s happening inside your systems but also make sense of the chaos.

This is where a **monitoring stack** comes in.

---

## The Tools in Our Stack

Think of this setup as a control room with different instruments working together:

- **Prometheus** is like your compass — it scrapes metrics such as CPU, memory, and disk usage, telling you where the system is heading.  
- **Windows Exporter** acts as the ship’s sensors — collecting raw system data from Windows servers so Prometheus has something to work with.  
- **Loki** is the ship’s logbook — recording everything said and done, line by line, so you can trace what happened when things go wrong.  
- **Promtail** is the crew member carrying those logs safely back to Loki.  
- **Grafana** is the captain’s dashboard — a wall of gauges, charts, and panels that turn raw data into insight at a glance.

Together, they form a navigation system for modern infrastructure. With them, you do not just sail blindly — you know where you are, where you are going, and what dangers are on the horizon.

---

## What This Project Covers

This documentation shows how to set up this stack step by step on a **local machine**. It mirrors the same architecture used in workplace environments to monitor servers and applications, but without any sensitive configurations. By the end, you’ll have:

- Metrics visualized in Grafana (CPU, memory, disk usage).  
- Logs shipped through Promtail → Loki and explored in Grafana.  
- A working foundation you can expand into larger, production-level monitoring.

Let’s set sail.
