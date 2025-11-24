# 🛣️ Vestra — Roadmap (Self-Hosted Edition)

Vestra is an open-source academic resource platform that campuses can **self-host** to provide structured study materials, notes, roadmaps, prerequisites, and PYQs for their students.  

Each campus runs **its own instance** of Vestra with:
- its own domain  
- its own database  
- its own storage  
- its own users and roles  

Vestra focuses on being **easy to deploy**, **easy to customize**, and **powerful for students**.

This roadmap outlines the evolution from MVP to a fully production-ready system.

---

# 🚀 Phase 0 — Planning & Foundation  
**Goal:** Establish architecture, repository, core documents, and design guidelines.

### 🔹 Deliverables
- [x] Decide stack: Next.js 14, Supabase (or Postgres + S3), Drizzle ORM, Tailwind, Meilisearch.
- [x] Core repository initialized.
- [x] Docs created:
  - README.md  
  - ROADMAP.md  
  - CONTRIBUTING.md  
  - INSTALLATION.md  
  - DEPLOYMENT.md  
- [ ] Finalize branding: logo, color palette, icon, UX style.
- [ ] Define single-tenant architecture (no multi-tenant DB).

---

# 🏗️ Phase 1 — Core Infrastructure Setup  
**Goal:** Build the foundation that every campus instance will rely on.

### 🔹 Backend Setup
- [ ] Initialize Next.js (App Router, TS, ESLint).
- [ ] Integrate TailwindCSS + shadcn/ui components.
- [ ] Set up Supabase project OR connect to external Postgres.
- [ ] Set up buckets for: `notes`, `pyqs`, `assets`, `uploads`.
- [ ] Enable storage policies for campus admins and contributors.

### 🔹 Database Schema (Drizzle ORM)
Create SQL tables for a **single campus instance**:
- [ ] `users`
- [ ] `roles` (admin, moderator, student, alumni)
- [ ] `courses`
- [ ] `topics`
- [ ] `topic_prerequisites`
- [ ] `resources`
- [ ] `ratings`
- [ ] `comments`
- [ ] `pyqs`
- [ ] `roadmaps`
- [ ] `moderation_logs`
- [ ] `settings` (campus-specific config)
- [ ] Add indexes (slug, course_code, topic_slug, resource_type)

### 🔹 Authentication & Roles
- [ ] Supabase Auth integration.
- [ ] Email/password + optional OAuth providers.
- [ ] Role assignment system.
- [ ] Admin dashboard for managing roles.

### 🔹 Search Integration
- [ ] Set up Meilisearch instance (self-hosted or managed).
- [ ] Create indexes:
  - `topics`
  - `resources`
  - `courses`
- [ ] Sync DB to Meilisearch via API routes or cron jobs.

### 🔹 Deployment Templates
- [ ] `INSTALLATION.md`
- [ ] `DEPLOYMENT.md`
- [ ] Dockerfile
- [ ] Docker Compose (Postgres + Meilisearch + Server)
- [ ] One-click deploy to Vercel (for serverless-friendly setups)
- [ ] Campus configuration file (`config.json`)

---

# 🧩 Phase 2 — Backend API & Core Logic  
**Goal:** Build API endpoints powering resource creation, topic linking, PYQs, and moderation.

### 🔹 REST or Next.js API Routes
- [ ] `/api/auth`
- [ ] `/api/settings`
- [ ] `/api/courses`
- [ ] `/api/topics`
- [ ] `/api/resources`
- [ ] `/api/pyqs`
- [ ] `/api/roadmaps`
- [ ] `/api/search`
- [ ] `/api/moderation`
- [ ] `/api/ratings`
- [ ] `/api/comments`

### 🔹 Logic & Features
- [ ] Topic CRUD (with Markdown or MDX).
- [ ] Topic prerequisite linking (prereq graph).
- [ ] Resource types: notes, videos, blog links, PDFs, books.
- [ ] Resource ranking by rating and verification.
- [ ] Comments + threaded discussions.
- [ ] Roadmap builder:
  - Steps
  - Estimated time
  - Topic linking
- [ ] PYQ linking (year → topic references).
- [ ] Moderation workflow:
  - Drafts
  - Pending approval
  - Version history
  - Rollback
- [ ] Zod request validation across APIs.
- [ ] File uploads & signed URLs.

### 🔹 Background Jobs (optional)
Support for heavy operations:
- [ ] PDF parsing for text extraction
- [ ] Search indexing queue
- [ ] Automated backups
- [ ] Email notifications

Use:
- BullMQ (Redis)  
- or Supabase Cron + Edge Functions  

(Choose based on deployment goals.)

---

# 🎨 Phase 3 — Frontend MVP  
**Goal:** Deliver a usable platform for students, moderators, and admins.

### 🔹 Global Layout & Components
- [ ] Landing page (campus-branded)
- [ ] Top navigation + user menu
- [ ] Search bar with auto-suggest
- [ ] Sidebar navigation (course/topic tree)
- [ ] Dark mode toggle
- [ ] Notifications UI

### 🔹 Course Experience
- [ ] Course list by semester
- [ ] Course overview page
- [ ] Topic list under each course
- [ ] PYQ section for each course

### 🔹 Topic Experience
- [ ] Topic page:
  - MDX rendering
  - Prerequisite graph visualization
  - Linked resources
  - Linked PYQs
  - Contributor details
- [ ] Add/edit topic form
- [ ] Resource rating + comments
- [ ] Resource cards (video, PDF, link preview)

### 🔹 Roadmap Experience
- [ ] Roadmap viewer (step-based)
- [ ] Create roadmap UI
- [ ] Link roadmap to topics
- [ ] “Exam-oriented roadmap” toggle

### 🔹 Authentication UI
- [ ] Login, signup, logout
- [ ] Forgot password
- [ ] Email verification
- [ ] Role-based UI:
  - Admin
  - Moderator
  - Alumni
  - Student

---

# ⚙️ Phase 4 — Campus Admin Panel  
**Goal:** Make Vestra configurable and manageable for each campus.

### 🔹 Admin Dashboard Features
- [ ] Manage users & roles
- [ ] Manage courses
- [ ] Approve/reject content contributions
- [ ] System settings (branding, name, logo)
- [ ] Customize color palette/theme
- [ ] SEO settings (meta tags, robots)
- [ ] Enable/disable features (roadmaps, comments, PYQs)
- [ ] Backup/restore database

### 🔹 Campus Branding
- [ ] Custom theme editor (colors, icons)
- [ ] Upload campus logo
- [ ] Custom domain support
- [ ] Footer/footer links customization

---

# 🔥 Phase 5 — Advanced Student Features  
**Goal:** Make the platform deeply useful and student-centric.

### 🔹 Learning Features
- [ ] Bookmarks / Favorites
- [ ] Study streak tracking
- [ ] Topic completion tracking
- [ ] "Study dashboard" for personalized progress
- [ ] Resource recommendations based on rating & usage

### 🔹 Social Features
- [ ] Leaderboard for top contributors
- [ ] Contributor badges
- [ ] User profile pages
- [ ] Follow courses/topics

### 🔹 Analytics (Campus-Level)
- [ ] Most viewed topics
- [ ] Most used resources
- [ ] Heatmap of study activity before exams
- [ ] PYQ frequency charts
- [ ] Contributor statistics

---

# 🤖 Phase 6 — AI Enhancements (Optional but High Value)
These are optional but turn Vestra into a next-gen study platform.

### AI Features
- [ ] AI summaries for long topics
- [ ] AI-powered explanations for difficult concepts
- [ ] Auto-extract key points from PDFs
- [ ] AI-generated topic roadmaps
- [ ] AI search (semantic search + embeddings)
- [ ] “Ask Vestra” assistant (campus-trained)

Use:
- pgvector (Postgres)
- OpenAI / local models for embeddings
- Re-ranking via Meilisearch

---

# 📱 Phase 7 — Mobile App  
(Optional, but many students will prefer mobile.)

### Build with Expo:
- [ ] Topic browsing
- [ ] Roadmap viewer
- [ ] Offline downloads of notes
- [ ] Push notifications
- [ ] Study reminders

---

# 🚀 Phase 8 — Launch & Adoption  
### For each campus:
- [ ] Prepare installation/deployment docs
- [ ] Publish Docker images
- [ ] Publish example data seeds
- [ ] Provide customization guide
- [ ] Help early campuses deploy pilot instances

### Marketing / Community
- [ ] Discord/Telegram community
- [ ] Documentation website
- [ ] Showcase campuses using Vestra

---

# 🧭 Long-Term Vision
- Vestra Cloud: optional hosted service for campuses that don’t want to self-host.
- Plugin ecosystem (custom features per campus).
- Integration with LMS systems (Moodle, Canvas).
- Full offline-first student application.
- Campus-to-campus resource sharing (federation model).

---

# 🏁 Final Notes
Vestra is being built as a powerful, open, student-first platform.  
This roadmap is designed to:
- keep development organized  
- ensure scalability  
- make deployments easy  
- enable community contributions  
- empower campuses to run Vestra independently  

As the platform grows, this roadmap will evolve with new milestones and features.

Pull requests and community suggestions are welcome!
