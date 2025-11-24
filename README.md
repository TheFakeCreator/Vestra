<h1 align="center">Vestra</h1>
<p align="center">
  <img src="./public/assets/icon128.png" alt="Vestra Logo" width="256" height="256" />
</p>

<p align="center">
  <a href="./CONTRIBUTING.md">Contributing</a> •
  <a href="./CODE_OF_CONDUCT.md">Code of Conduct</a> •
  <a href="./LICENSE.md">License</a>
</p>

<p align="center">
  <a href="https://github.com/TheFakeCreator/Vestra"><img src="https://img.shields.io/github/stars/TheFakeCreator/Vestra?style=social" alt="GitHub stars" /></a>
  <a href="https://github.com/TheFakeCreator/Vestra/actions"><img src="https://img.shields.io/github/actions/workflow/status/TheFakeCreator/Vestra/ci.yml?branch=main&label=build&style=flat" alt="CI" /></a>
  <a href="https://github.com/TheFakeCreator/Vestra/issues"><img src="https://img.shields.io/github/issues/TheFakeCreator/Vestra?style=flat" alt="issues" /></a>
  <a href="https://www.npmjs.com/package/vestra"><img src="https://img.shields.io/npm/v/vestra?label=npm&style=flat" alt="npm version" /></a>
  <a href="https://pnpm.io/"><img src="https://img.shields.io/badge/pnpm-%2300A6FF.svg?style=flat&logo=pnpm&logoColor=white" alt="pnpm" /></a>
  <a href="https://github.com/TheFakeCreator/Vestra"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="license" /></a>
</p>

**Vestra** is an open-source, student-driven academic platform designed to help campus communities create, curate, and share high-quality study resources — including notes, roadmaps, past-year questions (PYQs), prerequisites, and course-specific materials.  
Built *by students, for students*, Vestra reduces the time spent searching for resources and gives learners a direct, structured path to exam-ready preparation.

> [!IMPORTANT]
**Important — Application Only:** This repository contains the Vestra application source code only. It is not a hosted service or a ready-made campus site. Campuses that want to use Vestra must deploy and host an instance themselves (for example on Vercel, Netlify, a VPS, or using a cloud provider). See **`⚙️ Getting Started (Local Development)`** below for instructions to run locally and guidance on deployment options.

**Note on Hosted Services (Future):** In the near future we may offer optional deployment services to simplify adoption — either a centralized hosted offering or campus-specific (self-contained) hosting options similar to how some SaaS projects (for example, n8n) provide hosted and self-hosted variants. These would be optional — campuses can continue to self-host or deploy Vestra on their preferred provider.

---

## 🚀 Vision

Every semester, students across campuses waste hours scavenging for the right resources: notes, videos, solutions, roadmaps, and PYQs. Vestra aims to eliminate this overhead. Guiding the students to direct, verified resources linked to their syllabus and exam patterns.

**Vestra’s mission is simple:**  
> *Provide campus-specific, senior-verified study resources — organized, searchable, and linked directly to exam-relevant topics.*

Each campus gets its own micro-platform where students can deploy personal sites, contribute curated resources, and build a self-sustaining ecosystem of knowledge for future batches.

---

## 🔥 Key Features

### 🏫 **Campus-Specific Knowledge Hubs**
Each college or university gets its own dedicated space with:
- Courses
- Topic trees
- Roadmaps
- PYQ archives
- Resource recommendations

### 📘 **Course & Topic System**
For every course, Vestra supports:
- Topic breakdowns (as per syllabus)
- Prerequisite tagging (topic dependency graph)
- Markdown-based explanations
- Linked resources & notes
- Senior-verified tags for quality control

### 🔗 **Resource Curation**
Students can add:
- Notes (PDF/MD)
- External links (YT, NPTEL, GFG, blogs, GitHub)
- Books & reference materials
- Summary cards for quick revision  
Resources are:
- Rated
- Commented
- Ranked by usefulness

### 📝 **PYQ Integration**
Each topic can be linked to:
- Past-year questions
- Specific exam years
- Direct references to question number & section  
A learner can instantly see **where a topic appeared in previous exams**.

### 🧭 **Roadmaps**
Structured, exam-oriented roadmaps designed by seniors:
- Topic order (based on difficulty)
- Time estimates
- Best resources for each topic
- Direct PYQ links

### 👥 **Student Contribution System**
Anyone can:
- Add new resources
- Update topic content
- Suggest edits
- Upload notes

Verified contributors (seniors/alumni) can:
- Approve submissions
- Validate correctness
- Mark best resources
- Flag issues

---

## 🏛️ Architectural Overview

### **Multi-Tenant Design**
Vestra supports multiple campuses on a single deployment:
```bash
/campus-name/course/ee301/topic/per-unit-system
```


### **Tech Stack (Proposed)**
- **Next.js 14** — App Router, SSR/ISR, fast UI
- **TailwindCSS** — clean and responsive styling
- **Supabase / PostgreSQL + MongoDB** — auth, DB, storage
- **Meilisearch** — fast resource & topic search
- **Vercel** — hosting for frontend + API routes
- **Redis** — caching & background jobs
- **Render** — backend hosting
- **Supabase Edge Functions** — backend serverless functions
- **drizzle-orm** — type-safe DB queries
- **Express.js** — backend framework
- **Sentry** — error monitoring
- **Jest** — unit testing
- **Playwright** — end-to-end testing
- **Vitest** — alternative for faster TDD
- **PostHog** or **Plausible** — privacy-friendly analytics
- **GitHub Actions** — CI/CD for deployments

---

## 🗂️ Data Model (Simplified)

### **Campus**
- name  
- slug  
- domain  
- created_by  

### **Course**
- code  
- title  
- semester  
- instructors  

### **Topic**
- title  
- content_md  
- prerequisites  
- linked_resources  
- linked_pyqs  

### **Resource**
- title  
- url or file  
- type  
- rating  
- comments  

### **PYQ**
- year  
- question_text  
- file_reference  
- linked_topics  

---

## 🔍 Search & Discovery

- Full-text search for topics, courses, resources
- Filtering by:
  - semester
  - course
  - resource type
  - verified content
- Ranking by:
  - upvotes
  - ratings
  - senior verification
  - past exam relevance

---

## ⚙️ Getting Started (Local Development)

### **Prerequisites**
- Node.js 18+
- Postgres (local or Supabase)
- Git
- pnpm / npm / yarn

### **Clone the repository**

```powershell
git clone https://github.com/TheFakeCreator/vestra.git
cd vestra
```

### **Install dependencies**

Install all workspace dependencies from the repository root using `pnpm`:

```powershell
pnpm -w install
```

### **Set up environment**

Create a local env file from the example and edit values (database, keys, hostnames):

```powershell
Copy-Item .env.example .env.local
# then open and edit .env.local
```

Add or confirm these variables in `.env.local` (example):

```ini
DATABASE_URL=postgresql://user:pass@localhost:5432/vestra
SUPABASE_URL=https://your-supabase-url
SUPABASE_ANON_KEY=your-anon-key
NEXT_PUBLIC_SITE_URL=http://localhost:3000
MEILI_HOST=http://localhost:7700
MEILI_API_KEY=masterKey
```

### **Run development servers**

Run each app individually from the repo root (recommended):

```powershell
pnpm --filter ./packages/server dev
pnpm --filter ./packages/web dev
```

Or run both in parallel from the root (if you have the root `dev` script configured):

```powershell
pnpm dev
```

Your web app should be available at `http://localhost:3000` by default.

### 🤝 Contributing
We welcome contributions from students, alumni, and developers!

### Ways to Contribute
- Fix bugs & open PRs
- Improve documentation

- Add UI components

- Suggest features

- Help with backend development

- Create sample data & seed scripts

### Guidelines
- Use clear PR titles & commit messages
- Follow coding style defined in the repo

- Open an issue before working on new features

- Keep UI consistent with project design

- See CONTRIBUTING.md for full guidelines.

### 🧪 Testing
Run tests from the workspace root:

```powershell
pnpm -w test
```
- Unit tests (Jest or Vitest)

- Integration tests

- API route testing

- UI testing with Playwright (optional)

### 📜 License
Code is licensed under the MIT License.
User-submitted content (notes, explanations, etc.) may be licensed under CC BY-SA 4.0 to ensure free use and distribution.

### 📬 Community & Support
- GitHub Issues: Feature requests & bug reports

- Discussions: Share ideas and feedback

- Discord/Telegram (optional): For contributors and campus admins

### 🌱 Roadmap

#### MVP
- Multi-campus setup

- Topic editor (Markdown)

- Resource link system

- PYQ linking

- Search system

- Basic deploy-to-subdomain for student websites

#### Phase 2
- Roadmaps UI

- Leaderboards for contributors

- Notes uploader + PDF viewer

- Commenting & rating system

- Moderation dashboard

#### Phase 3
- AI-assisted topic summaries

- AI “smart search” across campuses

- Mobile app (React Native)

### ✨ Acknowledgements
Vestra is inspired by the struggles of thousands of students trying to find the right resources during exams. The project exists to make learning simpler, faster, and more collaborative.

### ⭐ Star the Repo
If Vestra helped you or your campus, consider starring the repository to support open-source development!
```
⭐ https://github.com/TheFakeCreator/vestra
```
Built with ❤️ by students, for students.
