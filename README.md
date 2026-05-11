# Hi there, I'm Abhinav 👋

<div align="center">
  
  **Systems Engineer | AI Researcher | Full Stack Developer**
  
  *Building at the intersection of Distributed Systems, Edge AI, and Autonomous Agents.*
  
  [LinkedIn](https://www.linkedin.com/in/abhinav-singh-b01bba327/)
  
</div>

---

## 👨‍💻 About Me

I am a Computer Science undergraduate at **KIET Group of Institutions**. My work focuses on **agentic workflows** and **high-performance backends**.

I move fast, break things, and fix them with better architecture. Currently, I'm exploring **Model Context Protocols (MCP)** and **multi-agent orchestration architectures**.

---

## 🛠️ Tech Stack

### **Languages**
![Go](https://img.shields.io/badge/-Go-00ADD8?logo=go&logoColor=white)
![TypeScript](https://img.shields.io/badge/-TypeScript-3178C6?logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white)
![Java](https://img.shields.io/badge/-Java-ED8B00?logo=openjdk&logoColor=white)
![C++](https://img.shields.io/badge/-C++-00599C?logo=c%2B%2B&logoColor=white)
![Rust](https://img.shields.io/badge/-Rust-000000?logo=rust&logoColor=white)
![SQL](https://img.shields.io/badge/-SQL-4479A1?logo=postgresql&logoColor=white)
![Bash](https://img.shields.io/badge/-Bash-4EAA25?logo=gnubash&logoColor=white)

### **Backend & Systems**
![Node.js](https://img.shields.io/badge/-Node.js-339933?logo=node.js&logoColor=white)
![FastAPI](https://img.shields.io/badge/-FastAPI-009688?logo=fastapi&logoColor=white)
![Express](https://img.shields.io/badge/-Express-000000?logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/-Redis-DC382D?logo=redis&logoColor=white)
![Drizzle ORM](https://img.shields.io/badge/-Drizzle_ORM-C5F74F?logo=drizzle&logoColor=black)
![Docker](https://img.shields.io/badge/-Docker-2496ED?logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/-Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![Nginx](https://img.shields.io/badge/-Nginx-009639?logo=nginx&logoColor=white)
![Linux](https://img.shields.io/badge/-Linux-FCC624?logo=linux&logoColor=black)

### **AI Engineering**
![LangChain](https://img.shields.io/badge/-LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white)
![RAG](https://img.shields.io/badge/-RAG_Pipelines-000000?style=flat&logo=openai)
![Transformers.js](https://img.shields.io/badge/-Transformers.js-FFD21E?style=flat&logo=huggingface&logoColor=black)
![TensorFlow](https://img.shields.io/badge/-TensorFlow-FF6F00?logo=tensorflow&logoColor=white)
![Ollama](https://img.shields.io/badge/-Ollama-000000?style=flat&logo=ollama&logoColor=white)
![OpenAI SDK](https://img.shields.io/badge/-OpenAI_SDK-412991?logo=openai&logoColor=white)
![Vector DB](https://img.shields.io/badge/-Vector_DB-6B46C1?style=flat&logo=pinecone&logoColor=white)
![MCP](https://img.shields.io/badge/-MCP_SDK-000000?style=flat&logo=anthropic&logoColor=white)
![AG-UI](https://img.shields.io/badge/-AG--UI_Protocol-0066CC?style=flat)
![A2A](https://img.shields.io/badge/-A2A_Protocol-4285F4?style=flat&logo=google&logoColor=white)

### **Frontend & Tools**
![React](https://img.shields.io/badge/-React-61DAFB?logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/-Next.js-000000?logo=next.js&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/-Tailwind_CSS-06B6D4?logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/-Vite-646CFF?logo=vite&logoColor=white)
![Git](https://img.shields.io/badge/-Git-F05032?logo=git&logoColor=white)
![Neovim](https://img.shields.io/badge/-Neovim-57A143?logo=neovim&logoColor=white)

---

## 🔭 Featured Projects

| Project | Description | Stack |
| :--- | :--- | :--- |
| **Fraktal** | **Workflow Automation Engine.** A backend execution engine that chains API calls (Trigger → Action) with dynamic state injection and real-time webhook listeners. | `TypeScript` `Node.js` `Redis` |
| **Aether** | **Local-First AI Memory.** A unified memory layer using Chrome's Nano AI and vector search to sync context across ChatGPT, Claude, and Gemini locally. | `Edge AI` `Vector DB` `Transformers.js` |
| **Insights** | **AI Research Platform.** Content aggregation engine that uses Gemini 2.0 Flash to parse/summarize complex PDFs and serve RAG-based Q&A. | `PostgreSQL` `GenAI` `Express` |

---

## 🌍 Open Source Contributions

### [better-auth](https://github.com/better-auth/better-auth) — TypeScript Auth Framework
**[fix(client): broadcast session updates to other tabs on sign-out and user update](https://github.com/better-auth/better-auth/pull/8177)** · *Merged Feb 2026*

`broadcastSessionUpdate()` was dead code — defined and exported from `createSessionRefreshManager` but never called. Session mutations (sign-out, user updates) were never broadcast to other open tabs, causing stale `useSession()` state when `refetchOnWindowFocus` was disabled or rate-limited.

- Wired `broadcastSessionUpdate` into `atomListeners` callback for `/sign-out`, `/update-user`, and `/update-session`
- Added optional `callback?: (path: string) => void` to `ClientAtomListener` type
- Called `match.callback?.(routePath)` inside proxy `onSuccess` to trigger cross-tab broadcasts
- Added 2 new tests verifying broadcast fires correctly for sign-out and updateUser triggers

---

### [Pangolin](https://github.com/fosrl/pangolin) — Self-Hosted Tunneled Reverse Proxy
**[fix: correct session DELETE tautology and HTTP cookie domain interpolation](https://github.com/fosrl/pangolin/pull/2535)** · *Merged Feb 2026*

Identified and fixed two critical bugs in `server/auth/sessions/resource.ts` that silently broke session persistence for all users:

- **Bug 1 — Tautological DELETE:** `.where(eq(resourceSessions.sessionId, resourceSessions.sessionId))` compared a column to itself, generating `WHERE session_id = session_id` (always true) — wiping the *entire* `resourceSessions` table whenever any single session expired, logging out every active user platform-wide.
- **Bug 2 — Broken template literal:** `` `...Domain=$domain}` `` was missing the opening `{`, causing browsers to receive `Domain=$domain}` as a literal string and reject the cookie, leaving all HTTP resources permanently unauthenticated.

---

## 🏆 Achievements

- 🥇 **Winner** - Surreal World Asset Buildathon (June 2025)
- 🥈 **Finalist** - Agents of the Permaweb Hackathon (Aug 2025)
- 🥉 **Finalist** - World Computer Hacker League by ICP (Sept 2025)
- 🛡️ **Finalist** - PSB FinShield Hackathon, IIT Hyderabad (Sept 2025)

---

## 📊 GitHub Stats

<div align="center">
  <img src="https://github-profile-trophies.vercel.app/?username=Abhinav-kodes&theme=radical&no-frame=true&no-bg=true&margin-w=4" />
  <br/>
  
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=Abhinav-kodes&theme=radical" alt="profile details" />
  
  <br/>
  
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=Abhinav-kodes&theme=radical" alt="languages graph" />
</div>

---

<div align="center">
  <sub>"Code. Learn. Share. Repeat."</sub>
</div>
