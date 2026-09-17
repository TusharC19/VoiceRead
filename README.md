<div align="center">
  <br />
   <img src="/assets/banner.svg" alt="Project Banner" />
  <br />

  <div>
<img src="https://img.shields.io/badge/-Next.js_16-000000?style=for-the-badge&logo=Next.js&logoColor=white" />
<img src="https://img.shields.io/badge/-ElevenLabs-FFFFFF?style=for-the-badge&logo=ElevenLabs&logoColor=black" />
<img src="https://img.shields.io/badge/-Vapi-62F6B5?style=for-the-badge&logo=Vapi&logoColor=black" />
<img src="https://img.shields.io/badge/-Clerk-6C47FF?style=for-the-badge&logo=Clerk&logoColor=white" /><br/>
<img src="https://img.shields.io/badge/-MongoDB-47A248?style=for-the-badge&logo=MongoDB&logoColor=white" />
<img src="https://img.shields.io/badge/-Typescript-3178C6?style=for-the-badge&logo=Typescript&logoColor=white" />
<img src="https://img.shields.io/badge/-Tailwind-06B6D4?style=for-the-badge&logo=Tailwind-CSS&logoColor=white" />
<img src="https://img.shields.io/badge/-Shadcn/UI-000000?style=for-the-badge&logo=shadcnui&logoColor=white" />

  </div>

  <h3 align="center">AI Book Companion | Vapi, ElevenLabs</h3>

</div>

## 📋 <a name="table">Table of Contents</a>

1. ✨ [Introduction](#introduction)
2. ⚙️ [Tech Stack](#tech-stack)
3. 🔋 [Features](#features)
4. 🗺️ [Roadmap](#roadmap)
5. 🤸 [Quick Start](#quick-start)
6. 🔗 [Assets](#links)



## <a name="introduction">✨ Introduction</a>

VoiceRead is an AI-powered platform that lets you have real-time voice conversations with your books. Built with Next.js 16, Vapi, and MongoDB, it lets you upload a PDF, pick an ElevenLabs voice persona, and ask questions about the book out loud. Retrieval currently runs on MongoDB text search (with a regex fallback), which returns relevant passages to the configured Vapi assistant during the call.



## <a name="tech-stack">⚙️ Tech Stack</a>

- **[Clerk](https://jsm.dev/books-clerk)** is a comprehensive user management and authentication platform. It provides secure, pre-built components for email and social logins, enabling seamless session management and protected routes with minimal configuration.

- **[ElevenLabs](https://elevenlabs.io/docs)** is an advanced AI audio platform providing lifelike text-to-speech. It powers the selectable voice personas in VoiceRead's voice calls.

- **[MongoDB](https://www.mongodb.com/docs/)** is a flexible, document-based NoSQL database designed for scalability and developer ease. Combined with Mongoose, it stores book metadata, text chunks, and voice-session usage records.

- **[Next.js](https://nextjs.org/docs)** is a powerful React framework for building full-stack web applications. It handles the core application logic, server actions, API routes, and UI for VoiceRead.

- **[Shadcn UI](https://ui.shadcn.com/)** is a collection of re-usable, accessible components built with Tailwind CSS and Radix UI. It powers VoiceRead's interface.

- **[TypeScript](https://www.typescriptlang.org/)** is a superset of JavaScript that adds static typing, providing better tooling, code quality, and error detection.

- **[Vapi](https://jsm.dev/books-vapi)** is a specialized Voice AI platform that enables real-time conversational audio. It orchestrates the voice call and invokes VoiceRead's retrieval tool endpoint during a conversation.

## <a name="features">🔋 Features</a>

👉 **PDF Upload & Ingestion**: Upload a PDF book; text is extracted in the browser via PDF.js and split into 500-word overlapping chunks stored in MongoDB.

👉 **Voice Conversations**: Start a real-time voice call about an uploaded book via the Vapi SDK, with live call-state tracking (connecting, listening, speaking).

👉 **AI Voice Personas**: Choose from configurable ElevenLabs voices for the assistant's speech output.

👉 **Keyword-Based Retrieval**: A MongoDB text-search endpoint (with a regex keyword fallback) returns up to three relevant passages per query for the active book.

👉 **Live Transcripts**: Partial and final speech transcripts are displayed in real time during a call (kept in client state for the session; not yet persisted to the database).

👉 **Library Management**: Browse and search your uploaded books.

👉 **Auth & Subscription Tiers**: Clerk-based authentication with Free/Standard/Pro plans enforcing book count, session count, and per-session duration limits.

## <a name="roadmap">🗺️ Roadmap</a>

The following are planned improvements, not yet implemented:

- Semantic/embedding-based retrieval (current retrieval is keyword-based, not vector search)
- AI-generated chapter/book summaries
- Persisted transcript history (currently transcripts live only in browser state during the call)
- Server-side resource ownership checks on segment/session actions
- Webhook authentication on the retrieval tool endpoint
- OCR support for scanned (image-only) PDFs

## <a name="quick-start">🤸 Quick Start</a>

Follow these steps to set up the project locally on your machine.

**Prerequisites**

Make sure you have the following installed on your machine:

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/en)
- [npm](https://www.npmjs.com/) (Node Package Manager)

**Cloning the Repository**

```bash
git clone https://github.com/TusharC19/VoiceRead.git
cd VoiceRead
```

**Installation**

Install the project dependencies using npm:

```bash
npm install
```

**Set Up Environment Variables**

Create a new file named `.env` in the root of your project and add the following content:

```env
NODE_ENV='development'
NEXT_PUBLIC_BASE_URL=

# CLERK
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_SIGN_IN_FALLBACK_REDIRECT_URL=/
NEXT_PUBLIC_CLERK_SIGN_UP_FALLBACK_REDIRECT_URL=/

# VERCEL BLOB
BLOB_READ_WRITE_TOKEN=

# MONGODB
MONGODB_URI=

# VAPI
NEXT_PUBLIC_VAPI_API_KEY=
NEXT_PUBLIC_ASSISTANT_ID=
VAPI_SERVER_SECRET=

# ELEVENLABS
ELEVENLABS_API_KEY=
```

Replace the placeholder values with your real credentials. You can get these by signing up at: [**Clerk**](https://clerk.com), [**Vercel**](https://vercel.com), [**MongoDB**](https://www.mongodb.com), [**Vapi**](https://vapi.ai), [**ElevenLabs**](https://elevenlabs.io).

> Note: the assistant's model, system prompt, transcriber, and retrieval-tool registration are configured in the Vapi dashboard, not in this repository.

**Running the Project**

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to view the project.

## <a name="links">🔗 Assets</a>

Assets and snippets used in the project can be found in the codebase.
