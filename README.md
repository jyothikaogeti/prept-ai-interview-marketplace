<div align="center">

# Prept — AI Interview Platform

</div>

<div align="center">

[![Next.js](https://img.shields.io/badge/Next.js-16-black?logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Clerk](https://img.shields.io/badge/Clerk-Authentication-6C47FF?logo=clerk&logoColor=white)](https://clerk.com/)
[![Prisma](https://img.shields.io/badge/Prisma-ORM-2D3748?logo=prisma&logoColor=white)](https://www.prisma.io/)
[![Supabase](https://img.shields.io/badge/Supabase-Database-3FCF8E?logo=supabase&logoColor=white)](https://supabase.com/)
[![Stream](https://img.shields.io/badge/Stream-Video%20%26%20Chat-005FFF)](https://getstream.io/)
[![Google Gemini](https://img.shields.io/badge/Google_Gemini-AI-8E75B2?logo=googlegemini&logoColor=white)](https://ai.google.dev/gemini-api/docs)
[![Arcjet](https://img.shields.io/badge/Arcjet-Protection-111827)](https://docs.arcjet.com/)
[![Resend](https://img.shields.io/badge/Resend-Email-000000?logo=resend&logoColor=white)](https://resend.com/)

</div>

Prept is a full-stack web application for arranging 1:1 mock interviews with interviewers. Users can create profiles, browse interviewers, manage availability, book sessions using credits, join Stream video calls with chat, generate interview questions with Google Gemini, and receive transcript-based feedback when the configured recording and transcription workflow completes.

The application uses Next.js App Router, Clerk, PostgreSQL with Prisma, Stream Video and Chat, Google Gemini, Arcjet, and Resend. Some external services require account-level setup and credentials before their workflows can be used.

## Problem Statement

Preparing for technical interviews requires more than reading questions or studying documentation. Candidates benefit from realistic practice, interaction with another engineer, and constructive feedback.

Interview scheduling and management can also involve separate tasks such as maintaining availability, coordinating sessions, tracking earnings, and revisiting earlier interviews.

Prept addresses these needs by bringing several activities into one application:

- Discovering interviewers based on their profiles and specialities.
- Booking sessions using an internal credit balance.
- Conducting video interviews with chat.
- Generating category-specific questions for interviewers.
- Storing session details and recording links.
- Managing interviewer availability, earnings, and withdrawal requests.
- Processing a transcript-based feedback workflow using Gemini.

## Key Features

### 🔐 Authentication & Role-Based Onboarding

- Secure sign-up and sign-in using Clerk.
- Role-based onboarding for Interviewees and Interviewers.
- User profiles linked to Clerk identities, with role changes restricted after onboarding.

### 🧑‍💻 Interviewer Discovery

- Browse interviewer profiles with professional experience, company, title, interview categories, and credit rates.
- Search by name, title, or company.
- Filter interviewers by Full Stack, Frontend, Backend, DSA, Android, DevOps, System Design, and Behavioral categories.

### 🗓️ Interview Scheduling & Booking

- Configure daily availability windows as an interviewer.
- Book 45-minute interview slots across the next seven days.
- Prevent overlapping scheduled bookings and display unavailable slots.
- Validate user roles, available credits, and booking conflicts on the server.

### 💳 Credit-Based Subscription System

- Free, Starter, and Pro subscription plans managed through Clerk Billing.
- Monthly credit allocations of 1, 5, and 15 for the respective plans.
- Automatically deduct interviewee credits and credit interviewer earnings when a booking is created.
- Track balances and earnings through the application.

### 📹 Video Interviews & In-Call Chat

- Real-time video interviews powered by Stream Video.
- In-call chat powered by Stream Chat.
- Screen-sharing support and recording/transcription configuration.

### 🤖 AI-Powered Interview Questions

- Generate six category-specific interview questions with concise model answers.
- Supports Frontend, Backend, Full Stack, System Design, DSA, DevOps, Android, and Behavioral interviews.
- Accessible to interviewers through the interview call interface.

### 📊 AI-Generated Interview Feedback

- Generate structured feedback from interview transcripts using Google Gemini.
- Reports include a session summary, technical skills, communication, problem-solving, strengths, areas for improvement, and an overall rating.
- Save feedback and associate it with completed bookings.

### 📼 Interview Recordings

- Automatically capture recording-ready webhook events.
- Save recording URLs to associated bookings for later access.
- Display recordings and AI feedback on appointment cards for eligible subscription plans.

### 📈 Interviewer Dashboard

- Manage availability and upcoming appointments.
- View completed-session statistics, credit balances, and withdrawal history.
- Track earned credits and payout requests.

### 💸 Withdrawal Management

- Submit withdrawal requests against earned credits.
- Apply the configured 20% platform fee.
- Notify the administrator by email for review.
- Support administrative approval of withdrawal requests.

### 🛡️ Security & Rate Limiting

- Request protection using Arcjet Shield and bot detection.
- Action-specific token-bucket rate limiting.
- Server-side validation for role assignment, bookings, and credit-related operations.

### 🎨 Responsive User Interface

- Responsive UI built with React and Tailwind CSS.
- Lucide icons, theme support, and toast notifications powered by Sonner.

## Real-World Use Cases

- **🧑‍🎓 Prepare for a technical interview:** Create an interviewee account, browse interviewer profiles, request a mock interview, join the call, and review stored feedback when available.
- **🧑‍💼 Conduct mock interviews:** Set up an interviewer profile, configure an availability interval, meet candidates through Stream, and use category-based AI question suggestions during the call.
- **📚 Review previous sessions:** Use appointment history, recording URLs, and feedback records to revisit completed interviews when those records have been created successfully.
- **💰 Track interviewer earnings:** Review completed-session statistics, credit balance, and withdrawal request history from the interviewer dashboard.
- **📨 Review withdrawal requests:** An administrator whose primary Clerk email matches `ADMIN_EMAIL` can open a payout review page and approve a request using the additional configured password. This is a manual status workflow, not an automated funds transfer.

## Tech Stack

| Technology        | Purpose                                                                                               |
| ----------------- | ----------------------------------------------------------------------------------------------------- |
| ⚡ `Next.js`      | Routing, server components, Server Actions, one Route Handler                                         |
| ⚛️ `React`        | Component model, Suspense-driven loading states                                                       |
| 🎨 `Tailwind CSS` | Styling and responsive layouts                                                                        |
| 🧩 `shadcn/ui`    | UI component setup and styling conventions                                                            |
| 🔐 `Clerk`        | Authentication, user sessions, route protection, and email lookup for alerts                          |
| 🗄️ `Supabase`     | Persistent storage for users, availability, bookings, feedback, credit transactions, and payouts      |
| 🔷 `Prisma ORM`   | Database schema, queries, transactions, and migrations                                                |
| 📹 `Stream Video` | Server-side call setup, participant tokens, browser calling UI, recording/transcription configuration |
| 💬 `Stream Chat`  | In-call message channel and chat interface                                                            |
| 🤖 `Gemini`       | Gemini requests for interview questions and transcript-based feedback                                 |
| 🛡️ `Arcjet`       | Shield, bot detection, and booking/withdrawal rate limiting                                           |
| 📧 `Resend`       | Withdrawal-request email notifications                                                                |
| ✉️ `React Email`  | Rendering the withdrawal request notification template                                                |
| 🎯 `Lucide React` | Interface icons                                                                                       |
| 🔔 `Sonner`       | Toast notifications                                                                                   |
| ☁️ `Vercel`       | Deployment                                                                                            |

## System Architecture and Data Flow

The application follows a Next.js App Router architecture. Pages and server actions coordinate authentication, business rules, and database access. External providers handle identity, AI generation, calls, messaging, and email.

```mermaid
flowchart LR
    Browser["Browser<br/>(React client components)"]
    Next["Next.js server<br/>Pages and Server Actions"]
    Proxy["proxy.js<br/>Clerk and Arcjet"]
    Clerk["Clerk<br/>Authentication and plans"]
    Prisma["Prisma Client<br/>PostgreSQL adapter"]
    DB[("PostgreSQL")]
    Stream["Stream Video and Chat"]
    Hook["POST /api/webhooks/stream<br/>Signature verification"]
    Gemini["Google Gemini API"]
    Arcjet["Arcjet protection<br/>and rate limits"]
    Resend["Resend email API"]

    Browser --> Proxy
    Proxy --> Next
    Proxy --> Clerk
    Proxy --> Arcjet
    Next --> Prisma
    Prisma --> DB
    Next --> Stream
    Stream --> Hook
    Hook --> Prisma
    Hook --> Gemini
    Next --> Gemini
    Next --> Arcjet
    Next --> Resend
```

### Booking flow

1. The interviewee selects an interviewer and a time interval in the UI.
2. `bookInterviewerSlot` checks the Clerk session and applies the booking rate limiter.
3. The action loads the interviewee and interviewer database records, checks their roles and the interviewee's credit balance, and rejects an overlapping scheduled booking.
4. The server creates or retrieves a Stream call and configures recording, screen sharing, and automatic transcription.
5. A Prisma transaction creates the booking and a `BOOKING_DEDUCTION` transaction, deducts the interviewee's credits, and increases the interviewer's credit balance.
6. The action revalidates the relevant paths and returns the booking and Stream call identifiers.

### Interview and feedback flow

1. `getCallData` finds a booking by `streamCallId` and checks that the signed-in Clerk user is the interviewee or interviewer before generating a one-hour Stream token.
2. `CallRoom` initializes Stream Video. `CallUI` creates a Stream Chat client and a channel whose members are the two booking participants.
3. An interviewer can invoke `generateInterviewQuestions` to request six questions for a supported category from Gemini.
4. Stream sends `call.recording_ready` or `call.transcription_ready` events to the configured webhook endpoint. The webhook validates `X-Signature` using `STREAM_SECRET_KEY` before processing the event.
5. The recording handler saves a recording URL. The transcription handler extracts speech segments, builds a speaker-labelled transcript, and requests structured feedback from Gemini.
6. The feedback transaction upserts the booking's report, marks the booking `COMPLETED`, and creates a `BOOKING_EARNING` ledger entry if one does not already exist.

## Folder Structure

```text
ai-interview-platform/
├── actions/                  # Server actions
│   ├── aiQuestions.js        # Gemini question generator
│   ├── appointments.js       # Interviewee's bookings
│   ├── booking.js            # Interviewer profile + slot booking
│   ├── call.js               # Call access check + Stream token
│   ├── dashboard.js          # Availability, stats, withdrawals
│   ├── explore.js            # Interviewer listing
│   ├── onboarding.js         # Role selection / profile setup
│   ├── payout.js             # Admin payout approval
│   └── user.js
├── app/
│   ├── (auth)/               # Clerk sign-in / sign-up pages
│   ├── (protected)/          # explore, interviewers/[id], appointments, dashboard,
│   │                         # onboarding, call/[callId], payout/[id]
│   ├── api/webhooks/stream/route.js   # Stream webhook handler
│   ├── layout.js, page.js    # Root layout and landing page
├── components/               # Shared UI (header, cards, modals, pricing, ui/ primitives)
├── emails/                   # react-email template for withdrawal requests
├── hooks/useFetch.js         # Wrapper for calling       server actions with loading/error state
├── lib/
│   ├── prisma.js             # Prisma client
│   ├── getUser.js            # DB user sync + monthly credit allocation
│   ├── arcjet.js             # Token-bucket rate-limit helper
│   ├── helpers.js            # Date and slot-generation helpers
│   └── data.js               # Static content, plans, categories
├── prisma/                   # schema.prisma + migrations/
├── public/                   # Logo and company logos
├── proxy.js                  # Clerk + Arcjet request proxy
├── prisma.config.ts          # Prisma CLI config
└── next.config.mjs
```

## Database Schema

Prept uses PostgreSQL with Prisma ORM. The datasource is PostgreSQL; `lib/prisma.js` uses `DATABASE_URL` with the `pg` pool and Prisma PostgreSQL adapter, while `prisma.config.ts` reads `DIRECT_URL` for Prisma CLI operations.

#### **`User`**

| Field                    | Type                  | Description                                  |
| ------------------------ | --------------------- | -------------------------------------------- |
| `id`                     | `String`              | Primary key; UUID default                    |
| `clerkUserId`            | `String`              | Unique Clerk user ID                         |
| `name`                   | `String?`             | Optional display name                        |
| `email`                  | `String`              | Unique email address                         |
| `imageUrl`               | `String?`             | Optional profile image URL                   |
| `role`                   | `UserRole`            | Defaults to `UNASSIGNED`                     |
| `createdAt`              | `DateTime`            | Defaults to `now()`                          |
| `updatedAt`              | `DateTime`            | Automatically updated by Prisma              |
| `credits`                | `Int`                 | Interviewee credit balance; defaults to `0`  |
| `currentPlan`            | `String`              | Plan slug; defaults to `free`                |
| `creditsLastAllocatedAt` | `DateTime?`           | Optional last credit allocation time         |
| `title`                  | `String?`             | Optional professional title                  |
| `bio`                    | `String?`             | Optional profile biography                   |
| `company`                | `String?`             | Optional company name                        |
| `yearsExp`               | `Int?`                | Optional years of experience                 |
| `categories`             | `InterviewCategory[]` | Interview categories for an interviewer      |
| `creditRate`             | `Int`                 | Credits charged per booking; defaults to `1` |
| `creditBalance`          | `Int`                 | Interviewer credit balance; defaults to `0`  |

`clerkUserId` and `email` have unique indexes. A user can have availability records, bookings in either participant role, credit transactions, and payout records.

#### **`Availability`**

| Field           | Type                 | Description               |
| --------------- | -------------------- | ------------------------- |
| `id`            | `String`             | Primary key; UUID default |
| `interviewerId` | `String`             | Foreign key to `User.id`  |
| `status`        | `AvailabilityStatus` | Defaults to `AVAILABLE`   |
| `startTime`     | `DateTime`           | Interval start            |
| `endTime`       | `DateTime`           | Interval end              |

The model has an index on `(interviewerId, startTime)`. Deleting a user cascades to that user's availability records.

#### **`Booking`**

| Field            | Type            | Description                                  |
| ---------------- | --------------- | -------------------------------------------- |
| `id`             | `String`        | Primary key; UUID default                    |
| `intervieweeId`  | `String`        | Foreign key to `User.id` for the interviewee |
| `interviewerId`  | `String`        | Foreign key to `User.id` for the interviewer |
| `startTime`      | `DateTime`      | Scheduled start time                         |
| `endTime`        | `DateTime`      | Scheduled end time                           |
| `status`         | `BookingStatus` | Defaults to `SCHEDULED`                      |
| `creditsCharged` | `Int`           | Credits charged for the booking              |
| `streamCallId`   | `String?`       | Optional unique Stream call identifier       |
| `recordingUrl`   | `String?`       | Optional recording URL saved by the webhook  |
| `createdAt`      | `DateTime`      | Defaults to `now()`                          |
| `updatedAt`      | `DateTime`      | Automatically updated by Prisma              |

Indexes: `(status, createdAt)`, `(intervieweeId, status)`, and `(interviewerId, status)`. `streamCallId` is unique. A booking can have one feedback record and multiple credit transactions.

#### **`Feedback`**

| Field            | Type               | Description                           |
| ---------------- | ------------------ | ------------------------------------- |
| `id`             | `String`           | Primary key; UUID default             |
| `bookingId`      | `String`           | Unique foreign key to `Booking.id`    |
| `summary`        | `String`           | Overall session summary               |
| `technical`      | `String`           | Technical assessment                  |
| `communication`  | `String`           | Communication assessment              |
| `problemSolving` | `String`           | Problem-solving assessment            |
| `recommendation` | `String`           | Hiring recommendation and explanation |
| `strengths`      | `String[]`         | List of strengths                     |
| `improvements`   | `String[]`         | List of improvement areas             |
| `overallRating`  | `FeedbackRating`   | Overall rating enum                   |
| `sessionRating`  | `Int?`             | Optional user-provided session rating |
| `sessionComment` | `String?` (`Text`) | Optional user comment                 |
| `createdAt`      | `DateTime`         | Defaults to `now()`                   |

`bookingId` is unique, implementing an optional one-to-one relationship with a booking. Deleting the booking cascades to its feedback record.

#### **`CreditTransaction`**

| Field       | Type              | Description                                              |
| ----------- | ----------------- | -------------------------------------------------------- |
| `id`        | `String`          | Primary key; UUID default                                |
| `userId`    | `String`          | Foreign key to `User.id`                                 |
| `amount`    | `Int`             | Credit movement amount; sign depends on transaction type |
| `type`      | `TransactionType` | Transaction type enum                                    |
| `bookingId` | `String?`         | Optional foreign key to `Booking.id`                     |
| `createdAt` | `DateTime`        | Defaults to `now()`                                      |

Deleting the user cascades to their credit transactions. Deleting a referenced booking sets the optional `bookingId` to `NULL`.

#### **`Payout`**

| Field           | Type           | Description                             |
| --------------- | -------------- | --------------------------------------- |
| `id`            | `String`       | Primary key; UUID default               |
| `interviewerId` | `String`       | Foreign key to `User.id`                |
| `credits`       | `Int`          | Credits requested for withdrawal        |
| `platformFee`   | `Float`        | Calculated platform fee                 |
| `netAmount`     | `Float`        | Calculated net amount                   |
| `paymentMethod` | `String`       | Payment method supplied by interviewer  |
| `paymentDetail` | `String`       | Payment details supplied by interviewer |
| `status`        | `PayoutStatus` | Defaults to `PROCESSING`                |
| `adminNote`     | `String?`      | Optional administrative note            |
| `createdAt`     | `DateTime`     | Defaults to `now()`                     |
| `updatedAt`     | `DateTime`     | Automatically updated by Prisma         |
| `processedAt`   | `DateTime?`    | Optional processing time                |
| `processedBy`   | `String?`      | Optional processor identifier           |

Indexes: `(status, createdAt)` and `(interviewerId, status)`. Deleting the interviewer cascades to their payout records.

### Enumerations

| Enum                 | Values                                                                                        |
| -------------------- | --------------------------------------------------------------------------------------------- |
| `UserRole`           | `UNASSIGNED`, `INTERVIEWEE`, `INTERVIEWER`                                                    |
| `InterviewCategory`  | `FRONTEND`, `BACKEND`, `FULLSTACK`, `SYSTEM_DESIGN`, `DSA`, `DEVOPS`, `ANDROID`, `BEHAVIORAL` |
| `AvailabilityStatus` | `AVAILABLE`, `BOOKED`, `BLOCKED`                                                              |
| `BookingStatus`      | `SCHEDULED`, `COMPLETED`, `CANCELLED`                                                         |
| `FeedbackRating`     | `EXCELLENT`, `GOOD`, `AVERAGE`, `POOR`                                                        |
| `TransactionType`    | `CREDIT_PURCHASE`, `BOOKING_DEDUCTION`, `BOOKING_EARNING`, `ADMIN_ADJUSTMENT`                 |
| `PayoutStatus`       | `PROCESSING`, `PROCESSED`                                                                     |

### Entity relationship diagram

```mermaid
erDiagram
    User ||--o{ Availability : "interviewer sets"
    User ||--o{ Booking : "books (interviewee)"
    User ||--o{ Booking : "hosts (interviewer)"
    Booking ||--o| Feedback : has
    User ||--o{ CreditTransaction : has
    Booking ||--o{ CreditTransaction : "related to"
    User ||--o{ Payout : requests
```

## API Reference

The application has one explicit HTTP Route Handler.

#### `POST /api/webhooks/stream`

Receives Stream events for recordings and transcriptions. The handler requires an `X-Signature` header and verifies the HMAC-SHA256 signature using `STREAM_SECRET_KEY` before parsing the request JSON. It processes `call.recording_ready` and `call.transcription_ready`; other event types are acknowledged and ignored.

#### Recording-ready event

The following is a example of the fields read by the handler, not a complete Stream event payload:

```json
{
  "type": "call.recording_ready",
  "call_cid": "default:CALL_ID",
  "call_recording": {
    "url": "<recording-url>"
  }
}
```

#### Transcription-ready event

```json
{
  "type": "call.transcription_ready",
  "call_cid": "default:CALL_ID",
  "call_transcription": {
    "url": "<transcription-url>"
  }
}
```

The handler downloads the transcript, parses line-separated JSON entries, keeps entries where `type` is `speech`, labels segments with participant names where available, and sends the transcript to Gemini. Validated feedback is persisted, the booking is marked `COMPLETED`, and a `BOOKING_EARNING` credit transaction is created if it does not already exist.

**Example request**

```bash
curl -X POST http://localhost:3000/api/webhooks/stream \
  -H "Content-Type: application/json" \
  -H "X-Signature: <signature-generated-from-the-exact-payload>" \
  --data-binary @stream-event.json
```

The signature must be generated from the exact payload bytes according to Stream's webhook signing procedure; an arbitrary placeholder signature will be rejected. For real events, configure Stream to send webhooks to the deployed public endpoint.

**Success (`200 OK`)**

```json
{
  "ok": true
}
```

**Error responses implemented by the route**

| Status | Response `error`            | Condition                                                                                                           |
| ------ | --------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `400`  | `Invalid webhook request`   | Reading/decompressing the body or signature verification throws an error                                            |
| `400`  | `Invalid JSON payload`      | Verified payload cannot be parsed as JSON                                                                           |
| `401`  | `Missing webhook signature` | `X-Signature` header is missing                                                                                     |
| `401`  | `Invalid webhook signature` | Signature does not match the payload                                                                                |
| `500`  | `Webhook is not configured` | `STREAM_SECRET_KEY` is missing                                                                                      |
| `500`  | `Webhook processing failed` | An error occurs while processing a supported event, such as a failed transcript download or Gemini/Prisma operation |

### Server actions

| Server Action                                                 | Input                                | Behavior and result                                                                                                                                                                                                                        |
| ------------------------------------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `getCurrentUser()`                                            | None                                 | Returns selected fields from the current user's database profile, or `null` when the Clerk user or database profile is unavailable.                                                                                                        |
| `completeOnboarding(data)`                                    | Role and interviewer profile fields  | Requires authentication; validates the role and required interviewer fields; updates an `UNASSIGNED` profile and revalidates affected paths.                                                                                               |
| `getInterviewers()`                                           | None                                 | Returns interviewer profiles and one available interval where present; returns an empty list on a caught query error.                                                                                                                      |
| `getInterviewerProfile(interviewerId)`                        | Interviewer ID                       | Returns selected profile information, an available interval, and scheduled booking intervals; returns `null` on lookup failure.                                                                                                            |
| `bookInterviewerSlot({ interviewerId, startTime, endTime })`  | Interviewer ID and start/end values  | Applies rate limiting; checks roles, credits, and overlapping scheduled bookings; creates the Stream call and transactionally saves the booking and credit-balance updates. Returns `success`, `bookingId`, and `streamCallId` on success. |
| `getIntervieweeAppointments()`                                | None                                 | Returns the current interviewee's bookings with interviewer information and feedback, or an empty array if no matching user is available.                                                                                                  |
| `getCallData(callId)`                                         | Stream call ID                       | Checks sign-in and booking participation, then returns call/token data or an error result. The generated Stream user token is valid for one hour.                                                                                          |
| `generateInterviewQuestions({ category })`                    | Supported category                   | Requires authentication and a valid category; requests six questions with answers from Gemini and returns `{ questions }`.                                                                                                                 |
| `setAvailability({ startTime, endTime })`                     | Start and end time                   | Requires an interviewer; validates the interval and creates or updates the first available-availability record.                                                                                                                            |
| `getAvailability()`                                           | None                                 | Returns the current user's first available-availability record.                                                                                                                                                                            |
| `getInterviewerAppointments()`                                | None                                 | Returns bookings associated with the current database user as interviewer, including interviewee details and feedback.                                                                                                                     |
| `getInterviewerStats()`                                       | None                                 | Returns completed-session count, completed-booking credits, `creditRate`, and `creditBalance`.                                                                                                                                             |
| `requestWithdrawl({ credits, paymentMethod, paymentDetail })` | Credits and payment details          | Requires an interviewer; checks the balance, limits requests, transactionally creates a payout and decrements the balance, then attempts to notify `ADMIN_EMAIL` with Resend. Returns `success` and `netAmount` on success.                |
| `getWithdrawlHistory()`                                       | None                                 | Returns payout records belonging to the current user, newest first.                                                                                                                                                                        |
| `approvePayout({ payoutId, adminPassword })`                  | Payout ID and administrator password | Requires a signed-in user whose primary email matches `ADMIN_EMAIL`, validates `ADMIN_PAYOUT_PASSWORD`, and marks an unprocessed payout `PROCESSED`. It does not transfer money.                                                           |

## External Integrations

### 1. Clerk

**Purpose:** Authentication, identity lookup, sign-up and sign-in UI, and subscription-related checkout.

Clerk's plan lookup is used to identify `starter` and `pro` subscriptions, and the pricing component uses Clerk's experimental `CheckoutButton`. Paid plan identifiers are defined in `lib/data.js`.

Local setup requires a configured Clerk application. The plan configuration in the Clerk Dashboard must correspond to the plan identifiers and slugs expected by the source code.

### 2. PostgreSQL and Prisma

**Purpose:** Store users, availability intervals, bookings, feedback, credit transactions, and payouts.

The runtime database client uses the `pg` connection pool and `PrismaPg` adapter. The Prisma CLI obtains its migration connection URL from `DIRECT_URL`.

### 3. Stream

**Purpose:** Video calls, chat, user tokens, recording/transcription configuration, and event delivery.

The booking action creates the call and configures recording, screen sharing, and automatic transcription. The browser uses Stream Video and Stream Chat React components. The webhook handles recording and transcription completion event types.

The integration requires a Stream application, valid API credentials, and webhook configuration for the supported event types.

### 4. Google Gemini

**Purpose:** Generate interview questions and attempt to generate structured feedback from interview transcripts.

The code uses the `@google/genai` SDK and requests JSON-formatted output. The current source specifies the model name `gemini-3.8-flash` for these requests.

A valid API key and access to the configured model are required for AI functionality. Model availability, quotas, and provider errors may affect requests.

### 5. Arcjet

**Purpose:** Request protection, Shield, bot detection, and selected action-level rate limiting.

The shared middleware configures Shield and bot detection. Booking and withdrawal operations use token-bucket limiters:

- Booking: capacity of 5, configured with a refill rate of 2 over an interval of one hour.
- Withdrawal requests: capacity of 3, configured with a refill rate of 1 over an interval of one hour.

These settings should not be interpreted as a single global rate limit applied identically to every route.

### 5. Resend and React Email

**Purpose:** Send an email when an interviewer submits a withdrawal request.

The action renders a React Email template and attempts to send a notification through Resend. The sender address and recipient are hard-coded in the current source. Email errors are caught and logged; an email failure does not necessarily fail the withdrawal transaction.

The sender configuration and recipient should be reviewed before deploying the workflow in production.

## Environment Variables

The repository does not contain a `.env.example` file. Create a local `.env` in the project root and configure the variables used by the application and its SDKs.

#### Example `.env`

```bash
# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_replace_me
CLERK_SECRET_KEY=sk_test_replace_me

# PostgreSQL / Prisma
DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/prept?schema=public"
DIRECT_URL="postgresql://USER:PASSWORD@localhost:5432/prept?schema=public"

# Stream Video and Chat
NEXT_PUBLIC_STREAM_API_KEY=replace_with_stream_api_key
STREAM_SECRET_KEY=replace_with_stream_secret_key

# Google Gemini
GEMINI_API_KEY=replace_with_gemini_api_key

# Arcjet
ARCJET_KEY=replace_with_arcjet_key

# Resend
RESEND_API_KEY=re_replace_with_resend_api_key
ADMIN_EMAIL=admin@example.com

# Payout approval
ADMIN_PAYOUT_PASSWORD=replace_with_a_long_random_password

# Base URL
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### Configuration notes

- The `.gitignore` file excludes `.env*`. Keep real credentials in local or hosting environment configuration; do not commit them.
- No environment-variable validation module was found in the supplied source.
- The application has a `NEXT_PUBLIC_APP_URL` setting but no documented default URL for a deployed instance.
- The Clerk plan IDs are defined in `lib/data.js`; configuring keys alone does not guarantee the subscription checkout flow is configured correctly.
- `NODE_ENV` is used by the Prisma client for development-time global caching and is normally managed by the runtime. It is not included as a manual credential.

## Prerequisites

- **Node.js:** Use Node.js `20.19+`, `22.12+`, or `24+` to meet the documented minimum version ranges for Prisma ORM 7. Next.js 16 itself requires Node.js `20.9+`; Prisma has the stricter requirement. See the [Prisma system requirements](https://www.prisma.io/docs/orm/reference/system-requirements) and [Next.js installation requirements](https://nextjs.org/docs/app/getting-started/installation).
- **npm:** The repository includes `package-lock.json`; `npm install` installs the locked dependency versions.
- **PostgreSQL:** A reachable PostgreSQL database. The repository does not pin a server version.
- **Clerk account:** A Clerk application with valid environment keys. Configure the `starter` and `pro` plan slugs/IDs to match the references in `lib/data.js` if testing checkout.
- **Stream account:** A Stream application with video/chat capability and valid API credentials. Configure webhooks for `call.recording_ready` and `call.transcription_ready`.
- **Google AI account:** A Gemini API key with access to the model configured in `lib/gemini.js`.
- **Arcjet account:** An Arcjet key for the request-protection configuration.
- **Resend account:** Required if withdrawal notification emails need to be delivered; the sender configured in the source must be accepted by the account.

## Installation and Local Setup

1. **Clone or extract the repository**

   ```bash
   git clone https://github.com/jyothikaogeti/prept-ai-interview-platform.git
   cd prept-ai-interview-platform
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Create a PostgreSQL database**

   Create a database named `prept`, or use a different name and update both `DATABASE_URL` and `DIRECT_URL`. Ensure the credentials have permission to create tables and indexes. During local development, both URLs can point to the same database.

4. **Generate the Prisma client**

   ```bash
   npx prisma generate
   ```

5. **Apply the existing migration**

   ```bash
   npx prisma migrate dev
   ```

   To inspect migration status:

   ```bash
   npx prisma migrate status
   ```

   The repository contains an initial migration; no seed script is configured.

6. **Configure the external services**

   Before exercising provider-dependent functionality:
   - Configure the Clerk application credentials and subscription plans.
   - Configure a Stream application with the supplied API key and secret.
   - Configure Stream webhook delivery for `call.recording_ready` and `call.transcription_ready` at `/api/webhooks/stream`.
   - Configure an Arcjet key.
   - Configure a Gemini API key.
   - Configure Resend if withdrawal notification delivery is required.

   For deployed Stream webhooks, use the actual public HTTPS base URL of the deployed application.

7. **Start the development server**

   ```bash
   npm run dev
   ```

   Open `http://localhost:3000` in a browser.

## Available Scripts

The following scripts are defined in `package.json`:

| Command         | Purpose                                                     |
| --------------- | ----------------------------------------------------------- |
| `npm run dev`   | Starts the Next.js development server.                      |
| `npm run build` | Creates a production build.                                 |
| `npm run start` | Starts the production server; run after a successful build. |
| `npm run lint`  | Runs ESLint using the repository configuration.             |

The following Prisma CLI commands are also used during setup; they are not custom npm scripts:

| Command                     | Purpose                                                 |
| --------------------------- | ------------------------------------------------------- |
| `npx prisma generate`       | Generates the Prisma client in `lib/generated/prisma/`. |
| `npx prisma migrate dev`    | Applies and manages development migrations.             |
| `npx prisma migrate status` | Reports the migration status.                           |
| `npx prisma migrate deploy` | Applies pending migrations in a deployment workflow.    |

## Deployment

- Use a Node.js runtime supported by Prisma ORM 7 and install dependencies from `package-lock.json`.
- Set all required environment variables in the hosting provider. Keep secret keys server-side and set `NEXT_PUBLIC_APP_URL` to the public application URL.
- Provision PostgreSQL and run `npx prisma generate` as part of the build/setup process.
- Apply migrations with `npx prisma migrate deploy` before serving application requests that depend on the updated schema.
- Build with `npm run build` and start with the hosting provider's supported Next.js process or `npm run start`.
- Configure Clerk keys and paid plans, Stream credentials and webhook delivery, Gemini access, Arcjet, and Resend as needed for the enabled workflows.
- Configure Stream to send signed `call.recording_ready` and `call.transcription_ready` events to `https://<your-domain>/api/webhooks/stream`.
- Verify `ADMIN_EMAIL` matches the primary email of the administrator's Clerk account. Set `ADMIN_PAYOUT_PASSWORD` to a long random secret.
- Confirm that the configured Resend sender is valid for the Resend account before relying on withdrawal notifications.

## Troubleshooting

| Symptom                                     | Likely Cause / Solution                                                                                                                                                                                                                             |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Clerk authentication fails**              | Verify `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` and `CLERK_SECRET_KEY`; restart the development server after changing `.env`. Check the Clerk application/domain configuration.                                                                          |
| **Database queries fail**                   | Verify PostgreSQL is reachable and `DATABASE_URL` points to the intended database. Check credentials and database permissions.                                                                                                                      |
| **Prisma generate or migration fails**      | Check `DIRECT_URL` and `prisma.config.ts`, then review the SQL migration and error output. Run `npx prisma generate` after dependency installation. Do not reset a database containing data you need.                                               |
| **Booking fails**                           | Confirm the signed-in user has the `INTERVIEWEE` role, the target profile is an interviewer, the interviewee has enough credits, and no scheduled booking overlaps the requested interval. Check the Stream API credentials if call creation fails. |
| **Stream call or chat cannot initialize**   | Verify `NEXT_PUBLIC_STREAM_API_KEY`, `STREAM_SECRET_KEY`, and Stream application configuration. `getCallData` only returns a token to a booking participant.                                                                                        |
| **Stream webhook returns `401`**            | Ensure Stream is sending the correct `X-Signature` for the exact request payload and that the configured `STREAM_SECRET_KEY` matches the Stream application.                                                                                        |
| **Stream webhook returns `500`**            | Check server logs, database connectivity, transcript download responses, `GEMINI_API_KEY`, and the configured Gemini model. A processing error returns HTTP 500.                                                                                    |
| **Gemini question generation fails**        | Confirm `GEMINI_API_KEY` is set and the configured model identifier in `lib/gemini.js` is available to the account. The question action expects valid JSON in the response text.                                                                    |
| **Transcript feedback is missing**          | Confirm Stream transcription is enabled and a transcript URL/event is available. Check whether the transcript contains speech entries and inspect Gemini/Prisma errors in server logs.                                                              |
| **Withdrawal notification is not received** | Verify `RESEND_API_KEY`, `ADMIN_EMAIL`, the sender configured in `actions/dashboard.js`, and Resend delivery logs. Email errors are logged and do not necessarily roll back an already-created payout request.                                      |
| **Payout page returns not found**           | The signed-in Clerk user's primary email must match `ADMIN_EMAIL` (case-insensitive). Also confirm the payout ID exists. Approval separately requires `ADMIN_PAYOUT_PASSWORD`.                                                                      |
| **Arcjet blocks a request**                 | Review the Arcjet key, Shield/bot-detection decisions, and token-bucket rate-limit configuration in `proxy.js` and `lib/arcjet.js`.                                                                                                                 |
| **Build or dependency installation fails**  | Verify the Node.js version meets Prisma ORM 7's supported requirements, run `npm install`, and inspect ESLint/build output.                                                                                                                         |

## Learning Outcomes

- **Next.js App Router, Server Actions, and Route Handlers** — Separate page rendering and business operations from the Stream webhook handler.
- **Authentication and authorization** — Integrate Clerk identities with database users, apply role checks, and protect sensitive payout data at both page and action boundaries.
- **Prisma and PostgreSQL** — Model users, availability, bookings, feedback, transactions, and payouts; manage relational constraints and migrations.
- **Transactional credit accounting** — Use Prisma transactions to group booking-related updates and payout-request creation.
- **External API integration** — Integrate Stream Video/Chat, Google Gemini, Arcjet, and Resend into application workflows.
- **Webhook processing** — Verify Stream signatures, parse event payloads, handle transcript downloads, validate AI output, and persist feedback.
- **Security and reliability considerations** — Apply rate limits and understand the importance of secret management, signature verification, error handling, idempotency, and automated tests.
