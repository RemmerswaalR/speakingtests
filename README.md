# speakingtests

A SharePoint-based speaking assessment platform for language courses.

Students upload speaking recordings, receive AI-generated transcripts, edit the transcripts to reflect only their own speech, and submit them for assessment. Teachers can review recordings and transcripts, grade submissions, and export speaking metrics.

---

# Project Goals

The system should:

- Reduce teacher workload when assessing speaking assignments.
- Automatically generate speaking participation metrics.
- Allow students to verify and correct AI-generated transcripts.
- Support individual recordings from students participating in pair or group work.
- Integrate with Microsoft 365 authentication.
- Operate primarily within SharePoint Online.
- Scale to approximately 800+ students.

---

# User Roles

## Student

Students can:

- Log in using Microsoft 365.
- View available assignments.
- Select assignment partners.
- Upload audio recordings.
- Receive an AI-generated transcript.
- Edit the transcript.
- Submit the final transcript.
- View previous submissions.

---

## Teacher

Teachers can:

- Create and manage classes.
- Import student rosters via CSV.
- Create assignments.
- View submissions.
- Listen to uploaded recordings.
- View and compare partner submissions.
- Grade submissions.
- Export class data.

Teachers should only be able to access their own classes.

---

## Admin

Admins can:

- Manage teachers.
- Assign teachers to classes.
- Access all classes.
- Export system-wide data.
- Perform all teacher functions.

---

# Student Workflow

1. Log in via Microsoft 365.
2. Select a class.
3. Select an assignment.
4. Select partner(s) from a teacher-generated list.
5. Upload an audio recording.
6. System generates a transcript.
7. Student reviews while listening.
8. Student edits transcript to contain only their own speech.
9. Student submits.
10. Statistics are automatically calculated.

---

# Teacher Workflow

1. Create class.
2. Upload roster.
3. Create assignment.
4. Monitor submissions.
5. Open a submission.
6. Listen to audio while reviewing transcript.
7. Compare partner transcripts side-by-side.
8. Assign grade and feedback.
9. Export results if required.

---

# Metrics

The following metrics are automatically calculated from the final student transcript.

## Word Count

Total number of words contained in the transcript.

Example:

Hello everyone.
Today I will discuss travel.

Word Count = 6

---

## Turn Count

Each new line represents one turn.

Example:

Hello everyone.
Today I will discuss travel.

Turn Count = 2

---

## Average Words Per Turn

Formula:

Average Words Per Turn = Word Count ÷ Turn Count

Round to two decimal places.

Example:

6 words
2 turns

Average = 3.00

---

# Assignment Structure

Assignments are instances of a common workflow.

Examples:

- Week 1 Discussion
- Week 3 Travel Conversation
- Midterm Interview
- Final Discussion

All assignments use the same system but have different names and due dates.

---

# Audio Requirements

Students upload their own recordings.

Typical scenario:

- Students conduct a face-to-face conversation.
- Each student records using their own device.
- Recordings may contain partner voices.
- Transcript ownership is verified by the student during transcript editing.

The system should prioritize identifying the primary speaker but must allow transcript correction.

---

# Data Storage

Preferred storage:

## SharePoint Lists

Possible lists:

- Students
- Teachers
- Classes
- Assignments
- Submissions
- Grades

---

## SharePoint Document Libraries

Store:

- Audio files

---

# Authentication

Authentication will use Microsoft 365.

Requirements:

- Single sign-on
- Existing university accounts
- No separate passwords

---

# Transcript Generation

Requirements:

- AI speech-to-text service
- Initial transcript should begin appearing as quickly as possible
- Students are responsible for final transcript accuracy

Possible providers:

- OpenAI Whisper API
- Deepgram
- Azure Speech
- Other equivalent services

Provider selection is not finalized.

---

# Reporting

Teachers must be able to export:

- Student Name
- Student Email
- Assignment Name
- Word Count
- Turn Count
- Average Words Per Turn
- Grade

Format:

CSV

---

# Comparison View

Teachers reviewing a submission should see:

Student A

- Audio
- Transcript
- Metrics

Student B (Partner)

- Audio
- Transcript
- Metrics

Displayed side-by-side.

---

# Technical Direction

Current preferred architecture:

Microsoft 365
└── SharePoint Online
    ├── SharePoint Lists
    ├── Document Libraries
    ├── Power Automate
    └── SPFx React Application

External Services
└── Speech-to-Text Provider

---

# Non-Goals (Version 1)

The following features are intentionally out of scope:

- AI grading
- Automatic speaking proficiency scores
- Automatic speaker separation
- LMS gradebook integration
- Real-time conversation recording
- Mobile app development

---

# Expected Scale

Target Usage:

- ~800 students
- 9 speaking assignments per student
- Approximately 7,200 submissions annually

The system should be designed with future growth in mind.

---

# Development Phases

## Phase 1

Core Submission Workflow

- Authentication
- Assignment selection
- Audio upload
- Transcript generation

## Phase 2

Transcript Editor

- Audio player
- Editable transcript
- Save functionality

## Phase 3

Metrics Engine

- Word count
- Turn count
- Average words per turn

## Phase 4

Teacher Dashboard

- Review
- Grading
- Exports

## Phase 5

Administration

- Teacher management
- System-wide reporting

---

# Success Criteria

A successful MVP allows:

1. Students to upload recordings.
2. AI to generate transcripts.
3. Students to edit transcripts.
4. Teachers to review submissions.
5. Metrics to be generated automatically.
6. Data to be exported as CSV.
7. Operation within the Microsoft 365 ecosystem.
