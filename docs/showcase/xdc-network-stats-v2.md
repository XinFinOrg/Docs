---
title: XDC Network Stats v2 - 3D Globe Monitor
description: Introducing the next generation of XDC Network monitoring with real-time 3D visualization
---

# XDC Network Stats v2 🌐

**Live:** [stats.xdc.network/v2](https://stats.xdc.network/v2/)

The XDC Network Stats v2 brings a completely redesigned monitoring experience with an interactive 3D globe visualization, real-time metrics, and enhanced node tracking capabilities.

![XDC Stats v2 Preview](../assets/stats-v2-preview.png)

---

## ✨ Key Features

### 🌍 Interactive 3D Globe Visualization

The centerpiece of v2 is the stunning 3D globe that visualizes the XDC Network's global node distribution in real-time:

- **Geographic Node Display** — See exactly where XDC nodes are running worldwide
- **Live Connection Lines** — Watch block propagation paths across the network
- **Zoom & Rotate** — Explore the network from any angle
- **Node Clustering** — Easily identify high-density regions

### 📊 Real-Time Metrics Dashboard

At-a-glance network health indicators:

| Metric | Description |
|--------|-------------|
| **Block Height** | Current block number, updated in real-time |
| **Active Nodes** | Total connected nodes across the network |
| **TPS** | Transactions per second (current throughput) |
| **XDC/USD** | Live price feed integration |

### 🖥️ Enhanced Node Monitoring

- **Node Health Status** — Green/yellow/red indicators for each node
- **Latency Tracking** — Response times for each node
- **Peer Connections** — See how nodes are interconnected
- **Block Propagation Time** — Track how fast blocks spread across the network
- **Uptime Statistics** — Historical availability data

### 🔔 Alert System (Coming Soon)

- Custom threshold alerts
- Email/Telegram notifications
- Downtime tracking

---

## 🆚 v1 vs v2 Comparison

| Feature | v1 (Classic) | v2 (New) |
|---------|--------------|----------|
| Visualization | Table list | 3D Interactive Globe |
| Node locations | Not shown | Geographic mapping |
| Real-time updates | Basic | WebSocket streaming |
| Mobile support | Limited | Fully responsive |
| Block propagation | Time only | Visual path tracing |
| Performance | Good | Optimized with WebGL |

---

## 🛣️ Roadmap & Upcoming Features

### Phase 1 (Current)
- [x] 3D Globe visualization
- [x] Real-time block/node metrics
- [x] Basic node list
- [x] Price feed integration

### Phase 2 (Q1 2026)
- [ ] **Historical Analytics** — Charts showing network growth over time
- [ ] **Masternode Dashboard** — Dedicated view for masternode operators
- [ ] **API Access** — Public API for developers to query network stats
- [ ] **Dark/Light Theme** — User preference support

### Phase 3 (Q2 2026)
- [ ] **Subnet Monitoring** — Track XDC subnet networks
- [ ] **Validator Leaderboard** — Performance rankings
- [ ] **Block Explorer Integration** — Click-through to XDCScan
- [ ] **Custom Dashboards** — User-configurable widgets
- [ ] **Mobile App** — Native iOS/Android apps

### Phase 4 (Future)
- [ ] **AI-Powered Insights** — Anomaly detection and predictions
- [ ] **Network Comparison** — Compare XDC with other networks
- [ ] **Governance Tracking** — Monitor on-chain governance

---

## 💬 We Want Your Feedback!

The XDC Stats v2 is built for the community. We want to hear from you:

### What features would you like to see?

**Share your ideas:**

- 🐦 **Twitter/X:** Tag [@XinFin_Official](https://twitter.com/XinFin_Official) with #XDCStats
- 💬 **Discord:** [XDC Community Discord](https://discord.gg/xdc)
- 📧 **Email:** stats-feedback@xdc.network
- 🐙 **GitHub:** [Open an issue](https://github.com/XDCFoundation/XDCNetworkStats/issues/new)

### Community Suggestions Under Consideration

Based on early feedback, we're exploring:

1. **Gas Tracker** — Real-time gas prices and recommendations
2. **Whale Alerts** — Large transaction notifications
3. **DeFi Dashboard** — TVL and protocol metrics
4. **NFT Activity** — Network NFT statistics
5. **Bridge Monitor** — Cross-chain bridge status

---

## 🔧 For Developers

### Embedding Stats Widget

Want to embed XDC stats on your site? (Coming soon)

```html
<iframe 
  src="https://stats.xdc.network/v2/embed" 
  width="400" 
  height="300"
  frameborder="0">
</iframe>
```

### API Endpoints (Planned)

```
GET /api/v2/stats          # Current network stats
GET /api/v2/nodes          # Node list with details
GET /api/v2/blocks/recent  # Recent blocks
WS  /api/v2/live           # WebSocket stream
```

---

## 🚀 Try It Now

Experience the future of XDC Network monitoring:

**[→ Launch XDC Stats v2](https://stats.xdc.network/v2/)**

---

## 📜 Changelog

### v2.0.0 (January 2026)
- Initial v2 release
- 3D Globe visualization
- Real-time WebSocket updates
- Responsive design

### v1.x (Legacy)
- Classic table view available at [stats.xdc.network](https://stats.xdc.network)

---

*Last updated: January 2026*

*Have questions? Join the [XDC Community](https://xdc.network/community) or reach out on [Discord](https://discord.gg/xdc).*
