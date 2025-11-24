# Vestra — Full Project Context (For Agents / Developers / Planning)

## What Vestra Is

Vestra is an open-source, self-hosted academic resource platform designed to help individual college campuses organize and share their syllabuses, study materials, topic-wise notes, roadmaps, past-year questions (PYQs), prerequisites, and curated external resources.

It is built by students, for students, enabling seniors to contribute knowledge, curations, and experience to help juniors study efficiently without wasting time searching for the right materials.

Each campus runs its own fully independent Vestra instance, with its own database, storage, domain, and user base.

## Primary Goals

- Eliminate resource search overhead for students, especially during exams.
- Provide topic-wise structured learning paths, with prerequisites clearly mapped.
- Link topics to past-year questions, making exam prep direct and targeted.
- Enable campus seniors and alumni to contribute verified resources, notes, and roadmaps.
- Give each campus full control over hosting, branding, and data via a self-hosted deployment.
- Provide foundations for future AI-powered study guidance (semantic search, AI summaries, etc.)

## Who Will Use Vestra

- **Students** (consume resources, rate, comment, bookmark)
- **Seniors / Alumni** (contribute notes, add resources, share roadmaps)
- **Moderators** (approve contributions, manage quality)
- **Campus Admins** (manage users, roles, settings, theme, deployment)

## Core Features

### 1. Courses & Topics

Each course contains multiple topics. Topics can include:

- Markdown/MDX explanations
- Prerequisite topics (graph)
- Linked resources (videos, notes, PDFs, links)
- Linked PYQs
- Tags, difficulty, importance indicators

### 2. Prerequisite Graph (Topic Dependencies)

- Each topic can link to others as prerequisites.
- A directed acyclic graph (DAG) visualized in the UI.
- Helps students know the correct learning order.

### 3. Resources

Students can add curated resources such as:

- PDFs, notes
- External links (YouTube, NPTEL, etc.)
- Books / chapters
- Blogs
- Lecture recordings

Each resource has:

- Rating
- Comments
- Tags
- Verified flag (by moderators/alumni)

### 4. PYQ Linking

- Past-year questions can be uploaded and linked to topics.
- Each PYQ includes:
  - Year
  - Question text
  - Attached PDF/image
  - Topic references
- Students can see which topics appear most in exams.

### 5. Roadmaps

Roadmaps provide step-by-step guidance for a course or exam, including:

- Ordered steps
- Recommended resources
- Time estimates
- Topic links
- Study mode filters (revision, crash course)

### 6. Admin & Moderator Tools

- Approve/reject content contributions
- Modify courses, topics, resources
- Manage user roles (admin/moderator/alumni/student)
- Customize campus branding

### 7. Student Features

- Bookmarking
- Progress tracking (optional)
- Resource rating & comments
- Study dashboard
- Contributor badges
- User profile pages

## Architecture Overview

- Self-hosted, single-tenant instances (each campus deploys own instance)
- No multi-tenancy in the same backend

### Tech Stack

- Next.js 14 (App Router + TypeScript)
- TailwindCSS + shadcn/ui (UI library)
- Supabase OR self-managed Postgres (database + auth + storage)
- Drizzle ORM (schema + migrations)
- Meilisearch (search indexing)
- Redis + BullMQ (optional) for background jobs
- Deployment: Vercel / Docker / Self-host server
- S3/Supabase Storage (file uploads)

### APIs

- Built with Next.js Route Handlers (app/api/...) or Supabase RPC / PostgREST
- Optional edge functions for heavy logic

## Database Entities (Single-Tenant Schema)

- Users (roles: admin, moderator, alumni, student)
- Courses: id, title, code, semester, description
- Topics: id, course_id, title, slug, content_md, tags, created_by, verified_by, prerequisite_topic_ids
- Resources: id, topic_id, title, type, url/file, rating, verified_flag, added_by
- PYQs: id, course_id, year, question_text, file_url, linked_topic_ids
- Roadmaps: id, course_id, steps (ordered list), time_estimates, linked_topic_ids
- Ratings & Comments: user_id, resource_id, comment text, rating
- Moderation Logs: entity_type, action, by_user, timestamp

## Search System

- Meilisearch indexes courses, topics, and resources.
- Auto-sync on content updates.
- Fast autosuggest in the search bar.

## Storage

- Notes (PDFs), PYQs, images, attachments.
- Campus branding assets (logo, banner).
- Managed via Supabase Storage or any S3-compatible provider.

## Deployment Model

Campuses deploy their own instance via:

- Option A — Vercel (frontend + API; Supabase backend)
- Option B — Docker (full self-hosted stack with Docker Compose including Next.js server, Postgres, Meilisearch, Redis optional)
- Option C — Campus server (manual Node.js + Postgres setup)

## Security

- Role-based access control
- Supabase Row-Level Security if using Supabase
- Admin-only features
- Moderation workflow
- File validation and safe uploads
- Optional rate limiting (Redis)

## Core Deliverables

- Complete Vestra web app
- Admin dashboard
- Self-hosting documentation
- Database migrations
- Pre-built UI components
- Installer template (copy-paste setup)
- Default theme + branding files

## Future Enhancements & Vision

- AI-powered topic summaries
- AI-based resource recommendations
- Semantic search (pgvector)
- Contributor leaderboard
- Offline-first mobile app (Expo)
- Integration with LMS (Moodle/Canvas)
- Vestra Cloud: hosted version for campuses without servers
- Plugin ecosystem

## Key Principles

- Self-hostable → campuses own their data
- Open-source → transparent and community-driven
- Student-first → goal is to reduce study overhead
- Modular → deploy only what you need
- Scalable → suitable for 200 students or 20,000

## Final Statement

Vestra is an open-source, self-hosted academic resource platform that organizes course content, topics, roadmaps, and PYQs into a structured, student-driven knowledge hub. Each campus hosts its own independent instance, with customizable themes, moderator roles, and full control over data. Built with Next.js, Supabase/Postgres, Drizzle ORM, Meilisearch, and Tailwind, Vestra aims to become the standard study repository for colleges worldwide.
