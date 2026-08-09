<div align="center">

<h1>Long Tran</h1>
<h3>Backend Engineer · Real-time Systems · Distributed Architecture</h3>

<p>
I build backend systems that stay correct under concurrency,<br />
recover from failure, and remain understandable as they grow.
</p>

<p>
  <a href="https://longtmb2003.github.io"><img src="https://img.shields.io/badge/Portfolio-111827?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>
  <a href="https://www.linkedin.com/in/long-tmb/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://github.com/longtmb2003"><img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /></a>
</p>

<p>
  <img src="https://img.shields.io/badge/Go-1.26-00ADD8?style=flat-square&logo=go&logoColor=white" alt="Go 1.26" />
  <img src="https://img.shields.io/badge/Java-Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white" alt="Java and Spring Boot" />
  <img src="https://img.shields.io/badge/WebSocket-Real--time-7C3AED?style=flat-square" alt="WebSocket realtime" />
  <img src="https://img.shields.io/badge/PostgreSQL-Data-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Redis-Coordination-DC382D?style=flat-square&logo=redis&logoColor=white" alt="Redis" />
</p>

</div>

---

## 👋 About Me

I'm a backend engineer based in **Ho Chi Minh City, Vietnam**, focused on **distributed systems**, **real-time services**, and **event-driven architecture**. I enjoy designing explicit state ownership, clean service boundaries, durable data flows, and production safeguards—not just endpoints that work on the happy path.

My toolkit spans **Java / Spring Boot** and **Go**, with hands-on work across WebSockets, Kafka, gRPC, PostgreSQL, Redis, Docker, observability, and CI/CD.

---

## 🚀 Featured Project: GoCaro

<div align="center">

<a href="https://gocaro.cyou">
  <img width="100%" src="https://gocaro.cyou/thumbnail-og.jpg" alt="GoCaro — Real-time Multiplayer Gomoku" />
</a>

### A production-minded real-time multiplayer Gomoku platform

<p>
  <a href="https://gocaro.cyou"><img src="https://img.shields.io/badge/PLAY_LIVE-gocaro.cyou-14B8A6?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Play GoCaro" /></a>
  <a href="https://github.com/longtmb2003/GoCaro-Backend"><img src="https://img.shields.io/badge/BACKEND-Go-00ADD8?style=for-the-badge&logo=go&logoColor=white" alt="GoCaro Backend" /></a>
  <a href="https://github.com/longtmb2003/GoCaro-Frontend"><img src="https://img.shields.io/badge/FRONTEND-Vue_3-42B883?style=for-the-badge&logo=vuedotjs&logoColor=white" alt="GoCaro Frontend" /></a>
</p>

</div>

GoCaro started as a two-player WebSocket demo and evolved into a complete multiplayer platform: instant guest play, ranked matchmaking, reconnect, spectators, tournaments, social features, chat, rewards, and collectible spirits—all backed by explicit concurrency and persistence rules.

| Realtime Core | Competition | Social Layer | Progression |
| --- | --- | --- | --- |
| Actor-owned matches | Casual + ranked queues | Redis presence | Elo ranks + streaks |
| Reconnect + resync | Ready checks | Friends + challenges | Coins + daily quests |
| Spectate + replay | Tournament brackets | Lobby + direct chat | Shop + spirit evolution |

**Backend:** `Go 1.26` · `Gin` · `gorilla/websocket` · `PostgreSQL / pgx` · `Redis` · `JWT` · `Prometheus`<br />
**Frontend:** `Vue 3` · `TypeScript` · `Pinia` · `Tailwind CSS 4` · `Vite 8`

### Architecture at a Glance

```mermaid
flowchart LR
    USER["Browser"] --> EDGE["Cloudflare Tunnel<br/>Caddy"]
    EDGE --> SPA["Vue 3 SPA"]
    SPA -->|REST| HTTP["Gin Handlers"]
    SPA <-->|WebSocket| WS["Realtime Gateways"]

    subgraph BACKEND["Go Backend"]
        HTTP --> SVC["Application Services"]
        WS --> MM["Matchmaker"]
        MM --> RM["Room Manager"]
        RM --> ROOM["Room Actor<br/>one goroutine per match"]
        ROOM --> CORE["MatchCore<br/>pure game rules"]
        ROOM --> BUS["Domain Event Bus"]
        BUS --> SVC
    end

    SVC --> PG[("PostgreSQL")]
    SVC --> REDIS[("Redis")]
    MM --> REDIS
    BACKEND --> OBS["Logs · Health · Prometheus"]
```

The important boundary is the **Room Actor**: one goroutine exclusively owns board state, clocks, disconnect state, and match lifecycle. Other components send commands through channels; they never mutate a live match directly.

---

## 🔀 Highlighted System Flows

### 1. Play Instantly, Keep the Same Identity

Anonymous play is a first-class account state, not a disposable frontend session. Upgrading changes credentials on the same user record, so Elo, history, coins, quests, and inventory survive.

```mermaid
sequenceDiagram
    actor Player
    participant SPA as Vue SPA
    participant Auth as Auth Service
    participant Game as Game Platform
    participant DB as PostgreSQL

    Player->>SPA: Play Now
    SPA->>Auth: POST /api/auth/anonymous
    Auth->>DB: Create anonymous user
    Auth-->>SPA: JWT + stable user ID
    SPA->>Game: Queue and play as guest
    Game->>DB: Persist Elo, history, coins, quests

    Player->>SPA: Save My Account
    SPA->>Auth: POST /api/auth/upgrade
    Auth->>DB: Add username + password to same user ID
    Auth-->>SPA: New JWT, all progress preserved
```

### 2. Match Lifecycle, Reconnect, and Durable Results

The live path separates commands, domain rules, event delivery, and persistence. A transient network failure enters a grace window; a returning player receives a complete state snapshot before continuing.

```mermaid
flowchart LR
    QUEUE["Casual / Ranked Queue"] --> READY{"Ready Check"}
    READY -->|Both accept| MATCH["Matchmaker pairs players"]
    READY -->|Timeout| PENALTY["Strike / temporary lockout"]
    MATCH --> ROOM["Room Actor"]
    ROOM --> CORE["MatchCore validates command"]
    CORE --> EVENTS["Immutable domain events"]
    EVENTS --> LIVE["WebSocket broadcast"]
    EVENTS --> SAVE["Persist match · moves · Elo"]
    SAVE --> HISTORY["History · Replay · Share"]

    ROOM -->|Connection drops| GRACE["Reconnect grace window"]
    GRACE -->|Player returns| RESYNC["Authenticate + full state resync"]
    RESYNC --> ROOM
    GRACE -->|Window expires| FORFEIT["Disconnect loss"]
    ROOM -.-> SPECTATE["Spectator stream"]
```

### 3. Tournament Bracket from Registration to Champion

Tournament matches reuse the real matchmaker and room engine. The bracket persists independently from live reservations, so recovery can reissue work after a restart or reconcile a dropped event.

```mermaid
flowchart TD
    CREATE["Organizer creates tournament"] --> REGISTER["Players register"]
    REGISTER --> FULL{"Field full?"}
    FULL -->|No| REGISTER
    FULL -->|Yes| SEAL["Seed and persist bracket"]
    SEAL --> START["Start round"]
    START --> RESERVE["Reserve each bracket pair"]
    RESERVE --> ARRIVE{"Players arrive in grace period?"}
    ARRIVE -->|Both| PLAY["Play in normal Room Actor"]
    ARRIVE -->|One / none| WALKOVER["Resolve walkover"]
    PLAY --> RESULT{"Match result"}
    RESULT -->|Draw| REMATCH["Issue capped rematch"]
    REMATCH --> RESERVE
    RESULT -->|Winner| ADVANCE["Persist winner and advance bracket"]
    WALKOVER --> ADVANCE
    ADVANCE --> ROUND{"Final completed?"}
    ROUND -->|No| START
    ROUND -->|Yes| CHAMPION["Crown champion + notify players"]

    RECOVERY["Restart recovery + periodic reconciler"] -.-> RESERVE
    RECOVERY -.-> ADVANCE
```

### 4. One Match Event Powers the Progression Loop

Match completion is published once. Ordered subscribers ensure stats are updated before rewards are calculated; other subscribers handle achievements, spectators, and tournament progression without adding those concerns to gameplay code.

```mermaid
flowchart LR
    FINISH["MatchFinished event"] --> BUS["In-process Event Bus"]
    BUS --> STATS["Stats Service<br/>Elo · W/L · streak"]
    BUS --> REWARD["Reward Service<br/>coins · quest progress"]
    BUS --> ACH["Achievement Evaluator<br/>unlock · item · coins"]
    BUS --> TOURNAMENT["Tournament Progression<br/>advance bracket"]
    BUS --> SPECTATORS["Spectator Hub<br/>final frame"]

    REWARD --> QUEST["Daily quests"]
    REWARD --> WALLET["Coin ledger"]
    ACH --> COLLECTION["Collection rewards"]
    WALLET --> SHOP["Shop + inventory"]
    QUEST --> CLAIM["Player claims completed quest"]
    CLAIM --> WALLET
    COLLECTION --> SPIRIT["Equip / evolve spirit"]
    SHOP --> SPIRIT
    SPIRIT --> NEXT["Visible in the next match"]
```

---

## 🧠 Engineering Highlights

- **Explicit concurrency:** one goroutine owns each live match; no mutex protects board state.
- **Failure recovery:** reconnect snapshots, graceful shutdown, tournament recovery, and periodic reconciliation.
- **Durable workflows:** 27 versioned PostgreSQL migrations plus transactional match, rating, reward, and bracket writes.
- **Distributed coordination:** Redis-backed cross-node presence, pub/sub, and background-job locks.
- **Production safeguards:** per-IP/per-user limits, optional Turnstile, liveness/readiness probes, structured logs, and Prometheus metrics.
- **Proven behavior:** 400+ Go test functions across domain, handlers, repositories, concurrency, and end-to-end flows; CI runs vet, lint, and the race detector.

---

## 🛠 Technology Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=java,spring,go,kafka,grpc,maven,postgres,mysql,mongodb,redis,docker,kubernetes,nginx,cloudflare,githubactions,react,nextjs,vue,ts,tailwind,vite,git,github,linux" alt="Technology stack" />
</p>

| Area | Tools |
| --- | --- |
| Backend | Go, Java, Spring Boot, Gin, REST, gRPC, WebSockets |
| Data & Messaging | PostgreSQL, MySQL, MongoDB, Redis, Kafka |
| Frontend | Vue 3, TypeScript, Pinia, Tailwind CSS, Vite |
| Platform | Docker, Kubernetes, Caddy, Nginx, Cloudflare, GitHub Actions |

---

## 🎯 What I'm Exploring

`Distributed Systems` · `Real-time Backend` · `Event-Driven Architecture` · `Concurrency` · `Failure Recovery` · `Observability` · `Cloud Native`

---

## 📈 GitHub Activity

<div align="center">

<img width="100%" src="https://github-readme-activity-graph.vercel.app/graph?username=longtmb2003&theme=github-compact&hide_border=true" alt="Long's GitHub activity graph" />

</div>

---

<div align="center">

### Let's build something reliable.

<a href="https://longtmb2003.github.io"><img src="https://img.shields.io/badge/Portfolio-111827?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>
<a href="https://www.linkedin.com/in/long-tmb/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="https://github.com/longtmb2003"><img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /></a>

</div>
