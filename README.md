<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:E1306C,50:FD1D1D,100:F77737&height=120&section=header&text=Shiv%20Shankar%20Singh&fontSize=35&fontColor=white&animation=fadeIn&fontAlignY=35"/>
</div>

<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&pause=1000&color=2E9EF7&center=true&vCenter=true&width=480&lines=Full-Stack+Developer+%F0%9F%9A%80;React+%7C+Node.js+%7C+Express+%7C+MongoDB;Building+AI+backends%3A+RAG%2C+pgvector%2C+streaming;Learning+in+public%2C+one+step+at+a+time" alt="Typing SVG" />
</div>

<div align="center">
  <img src="https://user-images.githubusercontent.com/74038190/229223263-cf2e4b07-2615-4f87-9c38-e37600f8381a.gif" width="400">
</div>

## 👨‍💻 About Me

🎓 **B.Tech CSE graduate** from Lovely Professional University (2024)  
💼 **Full-stack developer** working mostly with **React, Node.js, Express and MongoDB**  
🤖 Right now building **DocMind**, an AI backend from scratch: embeddings, vector search, RAG, streaming, structured output  
🚀 Every project below is **live and deployed**, all on free-tier infra  
📍 Based in **Bengaluru, India**

```js
const shiv = {
  role: "Full-Stack Developer",
  location: "Bengaluru, India 🇮🇳",
  stack: ["React", "Redux Toolkit", "Node.js", "Express", "MongoDB", "PostgreSQL"],
  currentFocus: ["AI backends (RAG, pgvector)", "Streaming (SSE)", "Background jobs", "Testing"]
};
```
---

## 🚀 Featured Projects

### 🧠 [DocMind: Chat With Your PDFs](https://github.com/sh1v-max/AI-Backend) · *in progress*
**RAG • Vector Search • SSE Streaming • TypeScript • Express 5 • PostgreSQL + pgvector • Drizzle ORM • Gemini API • Zod**

> An AI backend built from scratch to understand how AI products actually work. No LangChain, no LLM SDK, just Express, Postgres and plain HTTP calls to Gemini.

- 📄 PDF upload → chunking → **Gemini embeddings (3072-dim)** stored in **pgvector**
- 🔍 **RAG chat** with cosine-similarity search, source passages shown under every answer, one PDF or all of them
- 🧵 **Conversation memory** stored in Postgres, a refresh resumes the same chat
- ⚡ Answers **stream live over SSE**, parsed by hand from Gemini's byte stream
- 📝 **Quiz generation** with Gemini structured output, **validated with Zod**, retried once on bad output, options shuffled in code
- 🗺️ Next up: background jobs (BullMQ), agents and tool calling, tests, deployment

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sh1v-max/AI-Backend)

### 🎬 [Cinegraph: AI Movie, TV & Anime Recommender](https://cinewatchgraph-ai.web.app)
**React 19 • Redux Toolkit • Firebase • Gemini API • Cloudflare Workers • TMDB API • Tailwind v4**

> A recommendation engine built around your own taste profile, covering movies, TV shows and anime in one search.

- 🤖 Natural-language search ("like Inception but shorter") that explains **why each pick was chosen**
- 🔐 Gemini key kept server-side in a **Cloudflare Worker proxy** with a CORS allow-list and input caps
- 🎯 Taste profile computed from your likes/dislikes (top genres, genres to avoid, favorite decade) and fed into the prompt
- 💬 **Multi-turn follow-ups** ("more like the third one") and three personalized "For You" rows
- ✅ Every AI suggestion is cross-checked against **real TMDB data**, so no hallucinated titles
- 🔥 Firebase Auth + Firestore with **per-user security rules**, live-synced ratings and watchlist

[![Live Demo](https://img.shields.io/badge/Live_Demo-E7101A?style=for-the-badge&logo=firebase&logoColor=white)](https://cinewatchgraph-ai.web.app)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sh1v-max/CineGraph)

### ⚙️ [TaskForge: Full-Stack Task Manager](https://taskforge-eight-xi.vercel.app)
**Node.js • Express 5 • MongoDB • JWT • Zod • Swagger • React • GitHub Actions**

> A deployed full-stack app: a secured REST API, a React frontend, and a CI/CD pipeline that ships every push.

- 🔐 **JWT auth** with bcrypt, and every task query scoped to its owner, so users only ever see their own data
- 🛡️ **Zod validation** on request bodies and query strings, Helmet, locked-down CORS, rate limiting behind a proxy
- 📄 Interactive **Swagger/OpenAPI docs**, live at [`/api/docs`](https://taskforge-api-e2g9.onrender.com/api/docs)
- 🔍 CRUD with server-side **filtering, sorting and pagination**, dashboard stats, dark mode
- 🔁 **GitHub Actions CI** (lint, syntax check, build), auto-deploys to **Render** (API) and **Vercel** (frontend)

[![Live Demo](https://img.shields.io/badge/Live_Demo-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://taskforge-eight-xi.vercel.app)
[![API Docs](https://img.shields.io/badge/API_Docs-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)](https://taskforge-api-e2g9.onrender.com/api/docs)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sh1v-max/Taskforge)

### 🍕 [BiteSwift: Food Delivery App](https://yourbiteswift.netlify.app/)
**React 19 • Redux Toolkit • React Router • Parcel • Netlify Functions**

> A Swiggy-style food delivery app running on real restaurant data, with a cart that actually works.

- 🛒 **Redux Toolkit cart** with per-item quantities, a bill breakdown (GST, fees, coupons) and a simulated checkout
- 🌐 **Netlify Functions proxy** for Swiggy's listing API, which sends no CORS headers
- 🧯 Menus blocked by Swiggy's bot protection **fall back to mock data in the exact same shape**, so the app never breaks
- 💡 Shimmer loading, lazy-loaded routes, custom hooks (`useRestaurantMenu`, `useOnlineStatus`)

[![Live Demo](https://img.shields.io/badge/Live_Demo-FF5200?style=for-the-badge&logo=netlify&logoColor=white)](https://yourbiteswift.netlify.app/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sh1v-max/BiteSwift)

### 📚 [BookVerse: Book Discovery Platform](https://bookversedot.netlify.app/)
**React • Tailwind CSS • React Router • Open Library API**

> A book discovery app with search, trending sections and detailed book pages.

- 🔍 Search by **title, author or genre** with debounced, instant results
- 📈 Daily, weekly and monthly **trending books**
- 📖 Detailed book pages with descriptions, characters and publication info

[![Live Demo](https://img.shields.io/badge/Live_Demo-00AD9F?style=for-the-badge&logo=netlify&logoColor=white)](https://bookversedot.netlify.app/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sh1v-max/BookVerse)

---

## 🛠️ Tech Stack & Tools

<div align="center">

### Frontend

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Redux](https://img.shields.io/badge/Redux_Toolkit-593D88?style=for-the-badge&logo=redux&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=react-router&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Framer Motion](https://img.shields.io/badge/Framer_Motion-0055FF?style=for-the-badge&logo=framer&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

### Backend & Databases

![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Drizzle](https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=for-the-badge&logo=drizzle&logoColor=black)
![Firebase](https://img.shields.io/badge/Firebase-039BE5?style=for-the-badge&logo=Firebase&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![Zod](https://img.shields.io/badge/Zod-3E67B1?style=for-the-badge&logo=zod&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)

### AI

![Gemini](https://img.shields.io/badge/Gemini_API-8E75B2?style=for-the-badge&logo=googlegemini&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![RAG](https://img.shields.io/badge/RAG-FF6F00?style=for-the-badge)
![SSE](https://img.shields.io/badge/SSE_Streaming-0899D7?style=for-the-badge)

### Tools & Deployment

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Netlify](https://img.shields.io/badge/Netlify-00C7B7?style=for-the-badge&logo=netlify&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)
![Cloudflare Workers](https://img.shields.io/badge/Cloudflare_Workers-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)

### Currently Learning

![BullMQ](https://img.shields.io/badge/BullMQ_+_Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Agents](https://img.shields.io/badge/AI_Agents_&_Tool_Calling-8E75B2?style=for-the-badge)
![Testing](https://img.shields.io/badge/Vitest_+_Supertest-6E9F18?style=for-the-badge&logo=vitest&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-black?style=for-the-badge&logo=next.js&logoColor=white)

</div>

---

## 📊 GitHub Analytics

<div align="center">
  <img height="180em" src="https://github-readme-stats-pi-three-66.vercel.app/api?username=sh1v-max&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide_border=true&bg_color=0D1117" alt="GitHub Stats"/>
  <img height="180em" src="https://github-readme-stats-pi-three-66.vercel.app/api/top-langs/?username=sh1v-max&layout=compact&langs_count=8&theme=tokyonight&hide_border=true&bg_color=0D1117" alt="Top Languages"/>
</div>

<div align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=sh1v-max&theme=tokyonight&hide_border=true&background=0D1117" alt="GitHub Streak Stats"/>
</div>

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=sh1v-max&bg_color=0D1117&color=79FF97&line=00E676&point=00BCD4&area=true&hide_border=true" alt="Contribution Graph"/>
</div>

---

## 🤝 Let's Connect

<div align="center">

Full-stack developer who ships real, deployed projects, and is now going deep on AI backends.

Open to **full-stack, frontend and AI backend** roles.

<br>

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:singhshiv0427@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shiv-shankar-singh-/)
[![Portfolio](https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=About.me&logoColor=white)](https://singhshiv.netlify.app/)
[![Twitter](https://img.shields.io/badge/Twitter-249EF0?style=for-the-badge&logo=x&logoColor=white)](https://x.com/1amWaziR)
[![LeetCode](https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/u/shiv0427/)

</div>

<div align="center">

**Thanks for visiting! Let's build something together.** 🚀

<img src="https://komarev.com/ghpvc/?username=sh1v-max&style=for-the-badge&color=brightgreen" alt="Profile Views"/>

</div>

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:E1306C,50:FD1D1D,100:F77737&height=120&section=footer"/>
</div>
