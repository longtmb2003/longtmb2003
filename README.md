<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&height=260&color=gradient&text=Long%20Tran&fontColor=ffffff&fontSize=52&fontAlignY=38&desc=Backend%20Engineer%20%7C%20Real-time%20%26%20Distributed%20Systems&descAlignY=58" alt="Long Tran — Backend Engineer" />

<img src="https://readme-typing-svg.demolab.com?font=Inter&weight=600&size=22&duration=3500&pause=1800&center=true&vCenter=true&width=820&lines=Building+reliable+real-time+systems.;Designing+event-driven+backend+architectures.;Go+%C2%B7+Java+%C2%B7+Spring+Boot+%C2%B7+WebSockets+%C2%B7+Redis;Learning+by+shipping+production-minded+software." alt="Typing introduction" />

<br />

<a href="https://longtmb2003.github.io">
  <img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" />
</a>
<a href="https://www.linkedin.com/in/long-tmb/">
  <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
</a>
<a href="https://github.com/longtmb2003">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github" alt="GitHub" />
</a>

</div>

---

# 👋 Hi, I'm Long

I'm a **backend engineer** based in **Ho Chi Minh City, Vietnam**, focused on **distributed systems**, **real-time services**, and **event-driven architecture**.

I enjoy problems where correctness under concurrency, reliability, and system boundaries matter: designing clean APIs, isolating domain logic, coordinating live state, and operating services under production-like conditions.

My backend toolkit spans **Java / Spring Boot** and **Go**, with hands-on work across WebSockets, Kafka, gRPC, PostgreSQL, Redis, Docker, and CI/CD.

---

# 🎯 Current Focus

<table>
<tr>
<td valign="top" width="50%">

**Building**

- GoCaro, a production-minded real-time game platform
- Actor-style WebSocket services and event-driven workflows
- Social, tournament, progression, and virtual-economy systems

</td>
<td valign="top" width="50%">

**Going deeper on**

- Distributed systems and failure recovery
- Clean / Hexagonal Architecture
- Observability, abuse prevention, and cloud-native delivery

</td>
</tr>
</table>

---

# 🚀 Featured Project — GoCaro

## 🎮 Real-time Multiplayer Gomoku Platform

GoCaro has grown from a two-player WebSocket demo into a full multiplayer platform. Players can enter anonymously, upgrade their account without losing progress, compete in casual or ranked matches, reconnect after a dropped connection, join tournaments, challenge friends, chat, and build a spirit collection.

🌐 **Live:** [gocaro.cyou](https://gocaro.cyou)<br />
📦 **Source:** [Go backend](https://github.com/longtmb2003/GoCaro-Backend) · [Vue frontend](https://github.com/longtmb2003/GoCaro-Frontend)

**Backend:** `Go 1.26` · `Gin` · `gorilla/websocket` · `PostgreSQL / pgx` · `Redis` · `JWT` · `Prometheus`<br />
**Frontend:** `Vue 3` · `TypeScript` · `Pinia` · `Tailwind CSS 4` · `Vite 8`

### 🏛️ System Architecture

```mermaid
flowchart LR
    PLAYER["Web / Mobile Browser"]
    EDGE["Cloudflare Tunnel<br/>Caddy Reverse Proxy"]

    subgraph CLIENT["Vue 3 SPA"]
        UI["Pages · Components"]
        STATE["Pinia Stores · Composables"]
        SOCKET["REST + WebSocket Clients"]
        UI --> STATE --> SOCKET
    end

    subgraph API["Go Backend"]
        TRANSPORT["REST Handlers<br/>WebSocket Gateways"]
        SERVICES["Application Services<br/>Auth · Social · Economy · Tournament"]
        MATCHMAKER["Casual / Ranked Matchmaker<br/>Ready Check · Reservations"]
        ROOMS["Room Manager<br/>One Actor per Match"]
        CORE["MatchCore<br/>Rules · Turns · Win Detection"]
        EVENTS["Domain Event Bus"]

        TRANSPORT --> SERVICES
        TRANSPORT --> MATCHMAKER
        MATCHMAKER --> ROOMS --> CORE
        ROOMS --> EVENTS --> SERVICES
    end

    POSTGRES[("PostgreSQL<br/>Durable State")]
    REDIS[("Redis<br/>Presence · Pub/Sub · Job Locks")]
    METRICS["Prometheus Metrics"]

    PLAYER --> EDGE --> CLIENT
    SOCKET -->|HTTPS / WSS| TRANSPORT
    SERVICES --> POSTGRES
    SERVICES --> REDIS
    MATCHMAKER --> REDIS
    API --> METRICS
```

The core match state is owned by a **single room goroutine**. Commands enter through channels, the isolated `MatchCore` applies game rules, and immutable domain events fan out to persistence and realtime protocol adapters. This keeps the domain independent from HTTP, WebSocket, and database concerns while avoiding shared-state races inside a match.

### ⚡ Realtime & Competitive Play

- Casual FIFO and ranked Elo matchmaking with a widening rating band
- Match ready checks, abandonment penalties, turn clocks, draw offers, and resignations
- Reconnect and full state resync after transient disconnects
- Spectator mode, match history, replay, and shareable results
- Private friend challenges and open invite-code matches
- Single-elimination tournaments with brackets, round progression, walkovers, and recovery jobs

### 🤝 Social & Progression

- Anonymous play with an in-place upgrade to a permanent account
- Redis-backed presence, live lobby events, friends, user search, and activity feeds
- Lobby chat, direct messages, unread state, and retention cleanup
- Coins, daily quests, achievements, rank tiers, streaks, and leaderboards
- Shop, inventory, equipment, spirit collection, and spirit evolution

### 🛡️ Production Engineering

- PostgreSQL migrations and transactional persistence for matches, ratings, rewards, and tournament state
- Redis pub/sub, distributed background-job locks, and multi-instance-aware presence
- Per-IP and per-user rate limits plus optional Cloudflare Turnstile protection
- Liveness/readiness probes, structured logging, Prometheus metrics, and graceful shutdown
- Dockerized deployment behind Caddy and Cloudflare Tunnel
- **400+ Go test functions** across unit, repository, handler, concurrency, and end-to-end suites; CI also runs race detection

---

# 🛠 Tech Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=java,spring,go,kafka,grpc,maven,postgres,mysql,mongodb,redis,docker,kubernetes,nginx,cloudflare,githubactions,react,nextjs,vue,ts,tailwind,vite,git,github,linux" alt="Technology stack" />
</p>

---

# 🧱 What I Build

- Reliable REST, gRPC, and WebSocket services
- Concurrent systems with explicit state ownership and lifecycle management
- Event-driven backends and asynchronous workflows
- Data-intensive features backed by PostgreSQL and Redis
- Observable, containerized deployments with CI/CD
- Clean, testable systems with pragmatic architecture boundaries

---

# 🧠 Focus Areas

`Distributed Systems` · `Real-time Backend` · `Event-Driven Architecture` · `Concurrency` · `Clean Architecture` · `Observability` · `Cloud Native`

---

# 📈 GitHub Activity

<div align="center">

<img width="100%" src="https://github-readme-activity-graph.vercel.app/graph?username=longtmb2003&theme=github-compact&hide_border=true" alt="Long's GitHub activity graph" />

</div>

---

<div align="center">

### Thanks for stopping by — let's connect.

<a href="https://longtmb2003.github.io">
  <img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" />
</a>
<a href="https://www.linkedin.com/in/long-tmb/">
  <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
</a>
<a href="https://github.com/longtmb2003">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github" alt="GitHub" />
</a>

<img width="100%" src="https://capsule-render.vercel.app/api?section=footer&type=waving&color=gradient" alt="Footer" />

</div>
