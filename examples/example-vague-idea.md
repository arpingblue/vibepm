# Example: From Vague Idea to AI-Ready Specs

This example demonstrates a complete Vibecoding architecture session.

---

## Round 1: Initial Pitch

**User:**
> I want to make a tool where users can upload YouTube links and get a summarized podcast out of it. We can charge for the transcriptions.

**Vibecoding Architect:**

Interesting idea. Let's design the architecture so an AI coding agent can build this without hallucinating.

**Current State:**
- Concept: YouTube URL -> Video processing -> Summarized Audio Podcast
- Monetization: Yes, requires handling payments.

To define the exact code scaffolding and not overwhelm an AI Coder, I need to lock down the stack and data flow immediately.

1. **Tech Stack Selection:** For the frontend and API routes, Next.js (App Router) is currently the most robust framework for AI generation. For the backend database and Auth, should we use Supabase (Postgres) or Firebase? 
2. **Audio/AI Integration:** What exact APIs are we calling on the backend to achieve this? Are we doing YouTube download -> Whisper API (for text) -> GPT-4 (for summary) -> ElevenLabs (for podcast audio)?
3. **Wait Time (Edge Case):** Generating a podcast takes minutes. We can't keep a serverless function running that long. Do we need a background job queue (like Inngest or Upstash), or should we just show a spinner and rely on webhooks from an external service?

*I'm asking this because "long-running async AI tasks" are the #1 reason AI-generated apps break. We must define the queue architecture first.*

---

## Round 2: Architecture & Constraints

**User:**
> Let's go with Next.js and Supabase, I'm somewhat familiar with them. The API flow you described is exactly right. For the wait time, I'm not sure, maybe just a simple webhook if ElevenLabs supports it? I also want them to be able to pick podcast voices and background music from a dashboard.

**Vibecoding Architect:**

Got it. This is becoming a solid architectural blueprint.

**Updated State:**
- Stack: Next.js (App Router) + Supabase (Auth + DB)
- AI Flow: Custom Endpoint -> Whisper -> OpenAI -> ElevenLabs
- Async Strategy: Webhooks

Now I need to aggressively cut scope to protect the AI Coder's context limit, and define the data schema.

1. **MVP Context-Cut:** Adding "background music mixing" requires complex audio processing (FFmpeg on the server), which will dramatically complicate your MVP backend. **Can we cut background music for Phase 1** and strictly return the raw TTS voice?
2. **Data Schema:** It sounds like we only need two core tables for the DB: `profiles` (mapping auth info & credits) and `generations` (storing the youtube URL, the resulting audio URL, and the status: pending/completed/failed). Does this cover your core entities?
3. **Monetization Check:** You mentioned charging. Integrating Stripe Subscriptions + Webhooks + Credits is extremely complex for an AI to generate in one shot. Should we start Phase 1 as completely free (no Stripe) to ensure the core audio pipeline works first, then add billing in Phase 2?

*If we dump Stripe, FFmpeg, and external webhooks on a coding agent all at once, you will get spaghetti code that won't compile. We must slice this.*

---

## Round 3: Finalizing Specs

**User:**
> That makes total sense. Yes, cut the background music completely. And yes, leave Stripe out of it for now, let's just use Supabase Auth and make it free for logged-in users. Your two tables scheme sounds perfect.

**Vibecoding Architect:**

Excellent. We have successfully constrained the scope and locked the architecture.

**Final State:**
- 100% Locked Stack: Next.js + Tailwind + Supabase Auth & DB
- Core Flow: Authenticated User inputs YouTube URL -> Endpoint creates `generation` record (status: pending) -> Kicks off background task (Whisper -> GPT -> Elevenlabs) -> Updates `generation` record (status: complete, audio_url: X).
- Removed: Billing (Stripe), Audio mixing.

The boundaries are now tight enough that an AI Coding Agent can safely build this. **I'm ready to generate your handoff artifacts.**

Which documents should I output for your AI Coder?
1. **The `.cursorrules` / System Prompt** (To set its global rules and stack)
2. **AI Implementation Plan** (The step-by-step checklist the AI must follow)
3. **Database Schema** (Supabase SQL statements ready to execute)
4. **All of the above**
