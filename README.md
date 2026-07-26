<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&height=260&color=gradient&text=Long%20Tran&fontColor=ffffff&fontSize=52&fontAlignY=38&desc=Distributed%20%26%20Real-time%20Backend%20Engineer&descAlignY=58"/>

<img src="https://readme-typing-svg.demolab.com?font=Inter&weight=600&size=22&duration=3500&pause=2000&center=true&vCenter=true&width=760&lines=Building+distributed+backend+systems.;Designing+scalable%2C+real-time+APIs.;Java+-+Spring+Boot+-+Kafka+-+gRPC;Learning+by+building." />

<br/>

<a href="https://longtmb2003.github.io">
  <img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white"/>
</a>
<a href="https://www.linkedin.com/in/long-tmb/">
  <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>
<a href="https://github.com/longtmb2003">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github"/>
</a>

</div>

---

# 👋 Hi, I'm Long

**Backend engineer** based in **Ho Chi Minh City, Vietnam**, focused on **distributed systems**, **real-time services**, and **event-driven architecture**.

I enjoy solving backend problems where **reliability, performance, and architecture** matter more than fancy UI — designing clean APIs, modeling concurrent systems, and making services that stay correct under load.

My core stack is **Java · Spring Boot · Kafka · gRPC**, and I learn best by building things that run under production-like conditions.

---

# 🎯 Current Focus

<table>
<tr>
<td>

**Building**
- Real-time WebSocket services
- Event-driven backends with Kafka
- gRPC service-to-service communication

</td>
<td>

**Going deeper on**
- Distributed systems & system design
- Clean / Hexagonal Architecture
- Cloud native (Docker · Kubernetes · CI/CD)

</td>
</tr>
</table>

---

# 🚀 Featured Project — GoCaro
## 🎮 GoCaro — Real-time Multiplayer Gomoku (Caro)

An end-to-end system for **live online matches** — not a CRUD demo. Play instantly
as a guest, climb a ranked ELO ladder, and reconnect mid-game without losing.

🔗 **Live demo:** https://go-caro-frontend.vercel.app
📦 [Backend (Go)](https://github.com/longtmb2003/GoCaro-Backend) · [Frontend (Vue)](https://github.com/longtmb2003/GoCaro-Frontend)

**Stack** — Backend: `Go 1.26` · `Gin` · `gorilla/websocket` · `pgx/PostgreSQL` · `JWT` ·
Frontend: `Vue 3` · `TypeScript` · `Pinia` · `TailwindCSS` · `Vite`

### ⚙️ Backend — engineered for concurrency, not just endpoints
- ⚡ **Real-time gameplay over WebSocket** — low-latency move sync on a 15×15 board
- 🧩 **Actor-style rooms** — one goroutine per match owns its state, timers & lifecycle; no mutexes on game state
- 🔄 **Event-driven architecture** — commands in, domain events out over an internal event bus (persistence is just a subscriber)
- 🏛️ **Clean Architecture** — domain / application / transport strictly separated; the domain never imports networking
- 🎯 **Dual matchmaking** — casual FIFO queue, plus **ranked ELO** (K=32) with a rating band that widens the longer you wait
- 🔁 **Reconnect with a grace window** — a dropped player rejoins their live match and resyncs the board
- 👀 **Spectator mode** · 🎞️ **Replay** · ⏱️ **Turn clock** · 🤝 **Draw offers**
- 🔐 JWT auth · 🗄️ PostgreSQL persistence · ✅ **230 tests** (unit + e2e, race-checked in CI)

### 🖥️ Frontend — a full game client, not a shell
- 🚀 **Anonymous "Play Now"** — start a match in one click, **save your account later** without losing rating or history
- 🏆 **Player progression** — ELO rank tiers, win streaks, coins, daily missions & achievement sharing
- 📊 **Live lobby** — online-user presence, leaderboard preview & username search, match history
- ♻️ **Resilient in-match UX** — auto-reconnect overlay, opponent-away countdown, live turn timer
- ♿ Accessible, responsive, light/dark — built as Page → Component → Composable → Store → Socket layers

---

# 🛠 Tech Stack

<p align="center">
<img src="https://skillicons.dev/icons?i=java,spring,go,kafka,grpc,maven,postgres,mysql,mongodb,redis,docker,kubernetes,nginx,githubactions,react,nextjs,vue,ts,tailwind,git,github,linux"/>
</p>

---

# 🧱 Things I Build

- ✅ High-throughput **REST & gRPC APIs**
- ✅ **Real-time WebSocket** services
- ✅ **Event-driven** backends with Kafka
- ✅ **Dockerized** deployments with CI/CD
- ✅ Clean, testable, well-architected services

---

# 🧠 Focus Areas

`Distributed Systems` · `Real-time Backend` · `Event-Driven Architecture` · `Clean Architecture` · `Cloud Native` · `Scalable APIs`

---

# 📈 GitHub Activity

<div align="center">

<img width="100%" src="https://github-readme-activity-graph.vercel.app/graph?username=longtmb2003&theme=github-compact&hide_border=true" />

</div>

---

<div align="center">

### Thanks for stopping by! Let's connect.

<a href="https://longtmb2003.github.io">
  <img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white"/>
</a>
<a href="https://www.linkedin.com/in/long-tmb/">
  <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>
<a href="https://github.com/longtmb2003">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github"/>
</a>

<img width="100%" src="https://capsule-render.vercel.app/api?section=footer&type=waving&color=gradient"/>

</div>
