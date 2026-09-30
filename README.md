<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:1A1B27,100:2E9EF7&height=190&section=header&text=Shiv%20Shankar%20Singh&fontSize=46&fontColor=ffffff&fontAlignY=38&desc=Full-Stack%20Developer%20%C2%B7%20Building%20AI%20Backends&descSize=18&descAlignY=60&animation=fadeIn" width="100%"/>
</div>

<div align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=20&pause=1200&color=2E9EF7&center=true&vCenter=true&width=620&lines=Full-Stack+Developer+%28MERN+%2B+TypeScript%29;Building+AI+backends%3A+RAG+%C2%B7+pgvector+%C2%B7+SSE+streaming;Every+project+live%2C+all+on+free-tier+infra;Open+to+Full-Stack+%26+AI+Backend+roles" alt="Typing SVG" />
</div>

<div align="center">

[![Portfolio](https://img.shields.io/badge/Portfolio-singhshiv.netlify.app-000000?style=flat-square&logo=netlify&logoColor=white)](https://singhshiv.netlify.app/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shiv-shankar-singh-/)
[![Email](https://img.shields.io/badge/Email-singhshiv0427-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:singhshiv0427@gmail.com)
[![X](https://img.shields.io/badge/X-@1amWaziR-000000?style=flat-square&logo=x&logoColor=white)](https://x.com/1amWaziR)
[![LeetCode](https://img.shields.io/badge/LeetCode-shiv0427-FFA116?style=flat-square&logo=leetcode&logoColor=black)](https://leetcode.com/u/shiv0427/)
<img src="https://komarev.com/ghpvc/?username=sh1v-max&style=flat-square&color=2E9EF7&label=Profile+views" alt="Profile views"/>

</div>

---

## 👋 Hi, I'm Shiv

I'm a **full-stack developer** from **Bengaluru, India** who builds with **React, Node.js, Express, MongoDB and PostgreSQL**, and I've spent the last few months going deep on **how AI backends actually work**: embeddings, vector search, RAG, conversation memory, streaming and structured LLM output.

I like building things end to end and shipping them. Every project below is **live**, deployed on free-tier infrastructure, and has a README that explains the *why* behind the decisions, not just the features.

```ts
const shiv = {
  role: "Full-Stack Developer",
  basedIn: "Bengaluru, India 🇮🇳",
  education: "B.Tech CSE, Lovely Professional University (2024)",
  stack: ["TypeScript", "React", "Node.js", "Express", "PostgreSQL", "MongoDB"],
  ai: ["RAG", "Embeddings", "pgvector", "SSE streaming", "Structured output + Zod"],
  nowLearning: ["BullMQ + Redis", "Agents & tool calling", "Vitest + Supertest", "Docker"],
  consistency: "300+ day GitHub streak · 100+ days of DSA",
  openTo: ["Full-Stack", "AI Backend", "Frontend"],
};
```

---

## 🧠 Flagship: DocMind

<table>
<tr>
<td>

### [DocMind: Chat With Your PDFs](https://docmind-jet.vercel.app/)

**Upload a PDF, chat with it, get quizzed on it.** An AI backend built from scratch to understand how AI products work under the hood. No LangChain, no LLM SDK: just Express, Postgres and plain HTTP calls to Gemini, so every piece is visible.

`TypeScript` `Express 5` `PostgreSQL` `pgvector` `Drizzle ORM` `Gemini API` `Zod` `Server-Sent Events` `React 19`

[![Live Demo](https://img.shields.io/badge/Live_Demo-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://docmind-jet.vercel.app/)
[![Live API](https://img.shields.io/badge/Live_API-46E3B7?style=for-the-badge&logo=render&logoColor=black)](https://ai-backend-docmind.onrender.com/)
[![GitHub](https://img.shields.io/badge/Source-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sh1v-max/AI-Backend)

</td>
</tr>
</table>

```mermaid
flowchart LR
    A[📄 PDF upload] --> B[Parse text]
    B --> C[~500-word chunks]
    C --> D[Gemini embeddings<br/>3072-dim]
    D --> E[(Postgres + pgvector)]
    Q[💬 Question] --> F[Embed question]
    F --> E
    E -->|top-3 by cosine distance| G[Prompt: chunks + last 8 turns]
    G --> H[Gemini]
    H -->|streamed over SSE| U[⚛️ React UI]
```

- 📄 **Ingestion pipeline:** PDF → text → chunks → **Gemini embeddings (3072-dim)** → **pgvector**, each chunk tagged with its document
- 🔍 **RAG chat** over one PDF or all of them, with the source passages (and which file they came from) shown under every answer
- 🧵 **Conversation memory** in Postgres: the last 8 turns go into every prompt, and a page refresh resumes the same chat
- ⚡ **Live streaming over SSE**, parsed by hand from Gemini's raw byte stream with an async generator
- 📝 **Quiz generation** with Gemini's structured-output mode, **validated with Zod**, retried once on bad output, options shuffled in code, graded in the browser
- ☁️ Deployed on free tier: API on **Render**, frontend on **Vercel**, Postgres on **Neon**

<details>
<summary><b>🔎 Engineering decisions worth knowing</b></summary>
<br>

- **Validate the model like any untrusted client.** Every quiz goes through a Zod schema before it's used. The model was valid 17/17 times in testing, so it's insurance, and a gallery of deliberately broken replies proves what it catches.
- **Valid isn't the same as good.** Across 50 generated questions the correct answer landed unevenly (one slot 36%, another 10%), so options are shuffled in code (Fisher–Yates) after validation instead of trusting the model's habits.
- **Retry once, then fail honestly.** Two attempts max, then a clean `502`. Never an endless loop.
- **Errors travel inside the stream.** Once an SSE response starts, its status code is already sent, so failures go out as an in-band `error` event.
- **Readable errors.** A failed vector query from Drizzle dumps all 3072 embedding numbers. A small helper prints just the message, the underlying cause, and the line in the codebase where it broke.
- **Routes → services → repositories.** Only repositories touch SQL, and services never touch `req`/`res`, so the same pipelines can later run inside a background worker.

</details>

> ⏳ The API is on Render's free tier, so the first request after it's been idle can take up to a minute while it wakes up.

---

## 🚀 Featured Projects

<table>
<tr>
<td width="50%" valign="top">

### 🎬 [Cinegraph](https://cinewatchgraph-ai.web.app)
**AI movie, TV & anime recommender**

`React 19` `Redux Toolkit` `Firebase` `Gemini API` `Cloudflare Workers` `TMDB` `Tailwind v4`

- 🔐 Gemini key kept server-side in a **Cloudflare Worker proxy** with a CORS allow-list and input caps
- ✅ Model returns strict JSON, and every title is **cross-checked against TMDB**, so no hallucinated picks reach the UI
- 🎯 **Taste profile** from your likes/dislikes (top genres, genres to avoid, favorite decade) fed into the prompt
- 💬 **Multi-turn follow-ups** ("more like the third one") and three personalized "For You" rows
- 🔥 Firebase Auth + Firestore with owner-only security rules

[![Live](https://img.shields.io/badge/Live-E7101A?style=flat-square&logo=firebase&logoColor=white)](https://cinewatchgraph-ai.web.app)
[![Code](https://img.shields.io/badge/Code-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/sh1v-max/CineGraph)

</td>
<td width="50%" valign="top">

### ⚙️ [TaskForge](https://taskforge-eight-xi.vercel.app)
**Secured REST API + React task manager**

`Node.js` `Express 5` `MongoDB` `JWT` `Zod` `Swagger` `React 19` `GitHub Actions`

- 🔐 **JWT + bcrypt** auth, and every query scoped to its owner, so users only ever see their own data
- 🛡️ **Zod** on bodies and query strings, Helmet, locked-down CORS, proxy-aware **rate limiting** (100 req / 15 min)
- 📄 Interactive **Swagger / OpenAPI** docs
- 🔍 Server-side **filtering, sorting and pagination**
- 🔁 **GitHub Actions CI**, auto-deploys to Render (API) and Vercel (frontend)

[![Live](https://img.shields.io/badge/Live-000000?style=flat-square&logo=vercel&logoColor=white)](https://taskforge-eight-xi.vercel.app)
[![API Docs](https://img.shields.io/badge/API_Docs-85EA2D?style=flat-square&logo=swagger&logoColor=black)](https://taskforge-api-e2g9.onrender.com/api/docs)
[![Code](https://img.shields.io/badge/Code-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/sh1v-max/Taskforge)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🥘 [BharatDiet](https://bharat-diet.vercel.app)
**Personalized nutrition for real Indian food**

`React 19` `Vite` `Tailwind v4` `React Router 7` `Vitest`

- 🍛 **Meal planner** matched to your calories, protein target, region, diet type and daily budget in ₹
- 🧮 Greedy meal allocator with a protein-boost pass and portion reconciliation ("2 roti → 2.5 roti")
- 📊 **200+ Indian foods** with real serving sizes, macros and cost, sortable by protein-per-rupee
- 🧪 **Vitest suite:** nutrition formulas, dataset validation, and every region × diet × budget × goal combination
- 🔓 Runs fully client-side: no account, no tracking

[![Live](https://img.shields.io/badge/Live-000000?style=flat-square&logo=vercel&logoColor=white)](https://bharat-diet.vercel.app)
[![Code](https://img.shields.io/badge/Code-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/sh1v-max/BharatDiet)

</td>
<td width="50%" valign="top">

### 🍕 [BiteSwift](https://yourbiteswift.netlify.app/)
**Swiggy-style food delivery app**

`React 19` `Redux Toolkit` `React Router` `Parcel` `Netlify Functions`

- 🛒 **Redux Toolkit cart** with quantities, a bill breakdown (GST, fees, coupons) and a simulated checkout
- 🌐 **Netlify Functions proxy** for Swiggy's listing API, which sends no CORS headers
- 🧯 Menus blocked by bot protection **fall back to mock data in the exact same shape**, so the app never breaks
- 💡 Shimmer loading, lazy-loaded routes, custom hooks

[![Live](https://img.shields.io/badge/Live-FF5200?style=flat-square&logo=netlify&logoColor=white)](https://yourbiteswift.netlify.app/)
[![Code](https://img.shields.io/badge/Code-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/sh1v-max/BiteSwift)

</td>
</tr>
</table>

### 🧩 More builds

| Project | What it is | Stack | Links |
|---|---|---|---|
| 🌐 **Portfolio** | 6 themes (WCAG AA checked), live GitHub dashboard with a contribution calendar, project case studies, 33 UI experiments, contact form via a Netlify Function | React, Vite, Tailwind v4, Framer Motion | [Live](https://singhshiv.netlify.app/) · [Code](https://github.com/sh1v-max/My-portfolio-2.0) |
| 📚 **BookVerse** | Book discovery with debounced search by title, author or genre, trending lists and detailed book pages | React, Tailwind CSS, Open Library API | [Live](https://bookversedot.netlify.app/) · [Code](https://github.com/sh1v-max/BookVerse) |
| 🗺️ **Where Is Your Country** | One of my early builds for exploring countries of the world | JavaScript | [Live](https://whereisyourcountry.netlify.app) |

---

## 🛠️ Tech Stack

<table>
<tr><td><b>Languages</b></td><td>

<img src="https://skillicons.dev/icons?i=ts,js,html,css&theme=dark" />

</td></tr>
<tr><td><b>Frontend</b></td><td>

<img src="https://skillicons.dev/icons?i=react,redux,tailwind,vite&theme=dark" />

</td></tr>
<tr><td><b>Backend &amp; Data</b></td><td>

<img src="https://skillicons.dev/icons?i=nodejs,express,postgres,mongodb,firebase&theme=dark" />

</td></tr>
<tr><td><b>DevOps &amp; Tools</b></td><td>

<img src="https://skillicons.dev/icons?i=git,github,githubactions,vercel,netlify,cloudflare,postman,vscode&theme=dark" />

</td></tr>
<tr><td><b>AI &amp; Libraries</b></td><td>

![Gemini](https://img.shields.io/badge/Gemini_API-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-336791?style=flat-square&logo=postgresql&logoColor=white)
![RAG](https://img.shields.io/badge/RAG-FF6F00?style=flat-square)
![SSE](https://img.shields.io/badge/SSE_Streaming-0899D7?style=flat-square)
![Drizzle](https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat-square&logo=drizzle&logoColor=black)
![Zod](https://img.shields.io/badge/Zod-3E67B1?style=flat-square&logo=zod&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=flat-square&logo=swagger&logoColor=black)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=black)
![Neon](https://img.shields.io/badge/Neon_Postgres-00E599?style=flat-square&logo=neon&logoColor=black)

</td></tr>
<tr><td><b>Learning now</b></td><td>

![BullMQ](https://img.shields.io/badge/BullMQ_+_Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Agents](https://img.shields.io/badge/Agents_&_Tool_Calling-8E75B2?style=flat-square)
![Vitest](https://img.shields.io/badge/Vitest_+_Supertest-6E9F18?style=flat-square&logo=vitest&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=next.js&logoColor=white)

</td></tr>
</table>

---

## 🧭 How I Build

- **Understand it, then build the smallest real version.** DocMind has no framework doing the interesting parts on purpose, so I know what RAG, streaming and structured output look like underneath.
- **Treat model output as untrusted input.** Validate it with a schema, cross-check it against real data, and never let a hallucinated result reach the user.
- **Secrets stay on the server.** API keys live behind a proxy or backend, never in the browser bundle.
- **Ship it, then document the why.** Every project is deployed and has a README that explains the tradeoffs, including known limitations.
- **Free-tier first.** Render, Vercel, Netlify, Neon, Firebase and Cloudflare Workers, no card required.

---

## 📊 GitHub Stats

<div align="center">
  <img height="170" src="https://github-readme-stats-pi-three-66.vercel.app/api?username=sh1v-max&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide_border=true&bg_color=0D1117&title_color=2E9EF7&icon_color=2E9EF7" alt="GitHub Stats"/>
  <img height="170" src="https://github-readme-stats-pi-three-66.vercel.app/api/top-langs/?username=sh1v-max&layout=compact&langs_count=8&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=2E9EF7" alt="Top Languages"/>
</div>

<div align="center">
  <img src="https://streak-stats.demolab.com/?user=sh1v-max&theme=tokyonight&hide_border=true&background=0D1117&ring=2E9EF7&fire=2E9EF7&currStreakLabel=2E9EF7" alt="GitHub Streak"/>
</div>

<div align="center">
  <img src="https://ghchart.rshah.org/2E9EF7/sh1v-max" alt="Contribution Chart" width="100%"/>
</div>

---

## 🤝 Let's Connect

<div align="center">

I'm **open to Full-Stack and AI Backend roles**. If you're building something with LLMs, APIs or real users, I'd love to talk.

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:singhshiv0427@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shiv-shankar-singh-/)
[![Portfolio](https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=netlify&logoColor=white)](https://singhshiv.netlify.app/)
[![X](https://img.shields.io/badge/X-000000?style=for-the-badge&logo=x&logoColor=white)](https://x.com/1amWaziR)
[![LeetCode](https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black)](https://leetcode.com/u/shiv0427/)

</div>

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2E9EF7,50:1A1B27,100:0D1117&height=110&section=footer" width="100%"/>
</div>
