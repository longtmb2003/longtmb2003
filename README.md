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

> **Real-time multiplayer Gomoku (Caro) backend** — an end-to-end system for live matches, not just a CRUD app.

**🔗 Live Demo:** https://go-caro-frontend.vercel.app

**What it does under the hood:**

- ⚡ **Real-time gameplay** over WebSocket (low-latency move sync)
- 🎯 **Matchmaking** — pairs players into live rooms
- 🧩 **Room Actor model** — each game room owns its own state & lifecycle
- 🔄 **Event-driven room lifecycle** — create → join → play → finish
- 🏛️ **Clean Architecture** — clear separation of domain / application / infra
- 🔐 **JWT authentication**
- 🗄️ **PostgreSQL** persistence

### Architecture

```mermaid
flowchart LR
    C["🌐 Next.js Client<br/>(TypeScript)"]
    subgraph BE["Spring Boot Backend"]
        WS["WebSocket Gateway"]
        MM["Matchmaking Service"]
        RA["Room Actors<br/>(per-game state)"]
        EV["Event-driven<br/>room lifecycle"]
    end
    DB[("PostgreSQL")]

    C -- "REST / JWT" --> BE
    C <-- "WebSocket" --> WS
    WS --> MM --> RA
    RA --> EV
    RA --> DB
```

**Tech:** `Java` · `Spring Boot` · `WebSocket` · `Next.js` · `TypeScript` · `PostgreSQL`

---

# 🛠 Tech Stack

<p align="center">
<img src="https://skillicons.dev/icons?i=java,spring,maven,kafka,grpc,postgres,mysql,mongodb,redis,docker,kubernetes,nginx,githubactions,nextjs,react,ts,tailwind,git,github,linux"/>
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

<img height="165" src="https://github-readme-stats.vercel.app/api?username=longtmb2003&show_icons=true&theme=transparent&hide_border=true&count_private=true&include_all_commits=true" />
<img height="165" src="https://streak-stats.demolab.com/?user=longtmb2003&theme=transparent&hide_border=true" />

<br/>

<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=longtmb2003&layout=compact&theme=transparent&hide_border=true&langs_count=8" />

<br/><br/>

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
