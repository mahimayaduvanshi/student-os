# StudentOS — Your Academic Operating System

StudentOS is a personal academic operating system built around a single engineering objective: **"Less Managing → More Studying"**.

It is specifically engineered not as an administrative college ERP or a simple attendance checklist, but as a local-first personal academic workspace. StudentOS unifies attendance mathematics, recurring timetable scheduling, automated timetable reconstruction, GPA modeling, assignment deadlines, and markdown notes into an integrated system designed to reduce administrative friction and academic anxiety.

## Live Demo

- **Production URL**: https://studentos-academic.vercel.app/
- **Demo Mode**: The application runs with complete functionality out-of-the-box without requiring account creation. Pre-seeded demo records allow immediate evaluation of all subsystems.

---

## Overview

### The Problem

University students routinely juggle academic responsibilities across fragmented, disconnected tools: spreadsheets for tracking attendance percentages, static timetable photos/PDFs in gallery apps, disparate note-taking software, paper diaries, and manual calendar reminders. This fragmented workflow creates administrative overhead, causes missed deadlines, and creates uncertainty about minimum attendance criteria.

### The Solution

StudentOS centralizes the student's daily academic workflow into a unified interface. It combines automated schedule calculations with zero-latency local state persistence and cloud backup. By automating routine academic calculations—such as attendance safety margins, recovery requirements, and class countdowns—it eliminates repetitive manual tracking and allows students to focus on coursework and learning.

---

## Core Features

The following features are currently implemented in StudentOS:

### 1. Mission Control Dashboard

- **Daily Academic Briefing**: Displays today's lectures, real-time indicator for the next upcoming class with location details, and a countdown timer.
- **Batch Attendance Logging**: One-click **"Mark All Today Present"** action or individual lecture attendance toggling.
- **Attendance Safety Ring**: Circular progress visualization reflecting overall attendance relative to the student's minimum threshold, with immediate visual alerts (safe, warning, critical).
- **Embedded Task & Countdown Widgets**: Direct overview of upcoming assignment deadlines, examination countdowns, and active institutional holidays.

### 2. Attendance Engine & Trajectory Mathematics

- **Exact Mathematical Threshold Calculations**: Calculates safe bunks when attendance is above the target and required classes for recovery when attendance is below the target.
- **Academic Exemption Rules**: Automatically accounts for non-penalizing statuses including institutional holidays, approved medical leaves, and official duty absences.
- **Interactive Bunk Simulator**: What-if scenario modeling tool enabling students to simulate future attendance outcomes before deciding to miss classes.
- **Attendance Verification Report**: Formats and generates formal, printable attendance audit summaries suitable for academic advisors or faculty review.
- **Analytics & Heatmap**: Recharts-powered historical trend visualization paired with a GitHub-style attendance consistency calendar heatmap.

### 3. Subject Registry & Academic Performance

- **Course Entity Management**: Configurable course directory with course codes, titles, assigned faculty contacts, lecture/lab room numbers, credit weights, and custom color coding.
- **Integrated GPA & CGPA Simulator**: Supports both 4.0 and 10.0 scale conversions with credit weighting, enabling students to project semester SGPA based on target grades.

### 4. Weekly Timetable & Calendar Export

- **Dynamic Weekly Schedule**: Complete Monday-to-Saturday schedule view with responsive daily filters for mobile viewports.
- **Universal Calendar Export**: One-click timetable export to standard `.ics` and `.csv` formats compatible with Google Calendar, Apple Calendar, and Microsoft Outlook.

### 5. Assignments & Examination Tracker

- **Assignment Pipeline**: Tracks submission status, priority flags, deadline countdowns, and course associations.
- **Exam Countdown Radar**: Centralizes midterm and final exam schedules, room assignments, and remaining days.

### 6. Notes & Study Reflection Diary

- **Markdown Notes Workspace**: Full markdown note editor with folder organization, search, course tagging, and one-click `.md` file export.
- **Study Reflection Diary**: Daily study journal logging focus hours, mood indices, and continuous study streaks.

### 7. Focus Timer (Pomodoro)

- **Time-Drift Resistant Engine**: Implements absolute timestamp delta tracking (`Date.now()`) to eliminate browser background tab throttling and inaccurate timers.
- **Configurable Intervals**: Standard 25-minute, 50-minute, or custom focus/break cycles with direct study-session logging into the study diary.

### 8. Academic AI Co-Pilot

- **Context-Aware Assistance**: Built-in heuristic intelligence capable of summarizing course status, low-attendance warnings, and upcoming deadlines without requiring external API dependencies.
- **Bring-Your-Own-Key (BYOK) Integration**: Optional client-side integration for Gemini, OpenAI, or Claude APIs for extended conversational assistance.

### 9. System Shell & Accessibility

- **Command Palette (`Ctrl+K` / `Cmd+K`)**: Keyboard-first modal for instant navigation across all modules, quick course search, and batch actions.
- **Theme Engine**: Support for dark and light UI themes with persistent user preferences.

---

## Smart Semester Setup

StudentOS includes an automated setup workflow designed to eliminate manual data entry at the beginning of a semester. Rather than relying on simple raw OCR text extraction, it implements an **Intelligent Timetable Reconstruction Pipeline**:

```text
Document Input (PDF / Image)
           │
           ▼
Client-Side Processing (pdfjs-dist / tesseract.js worker)
           │
           ▼
Spatial Coordinate Geometry Analysis (x, y, width, height)
           │
           ▼
2D Grid Boundary & Day/Time-Slot Alignment
           │
           ▼
Legend Resolution (Course Codes, Titles, Faculty, Rooms)
           │
           ▼
Candidate Slot Deduplication & Validation Matrix
           │
           ▼
Interactive Verification Modal ──► State Store Provisioning
````

1. **Dual Ingestion Engine**: Directly processes native digital PDF documents using `pdfjs-dist` or raster timetable photos using `tesseract.js` web workers.
2. **Spatial Fragment Normalization**: Analyzes two-dimensional coordinates to cluster text within column cells, preventing cross-column contamination.
3. **Grid Alignment & Legend Mapping**: Resolves subject codes against timetable legend keys and maps them to recurring time slots across days of the week.
4. **Interactive Validation**: Flags ambiguous entries for student confirmation before provisioning registered courses and timetable slots into the application state.

---

## Tech Stack

| Layer                         | Technology                                  | Purpose                                              |
| :---------------------------- | :------------------------------------------ | :--------------------------------------------------- |
| **Runtime & Framework**       | React 19 (`react`, `react-dom`)             | Declarative component UI architecture                |
| **Language**                  | TypeScript 5 (`typescript`)                 | End-to-end static typing and domain data models      |
| **Bundler & Tooling**         | Vite 8 (`vite`, `@vitejs/plugin-react-swc`) | Fast development server and production compilation   |
| **Routing**                   | React Router DOM 6 (`react-router-dom`)     | Single-page application client-side routing          |
| **Styling & Design**          | Tailwind CSS, Radix UI, Lucide Icons        | Accessible, responsive design system                 |
| **Authentication & Database** | Firebase 12, Cloud Firestore                | User identity management and cloud persistence       |
| **Document Processing**       | `pdfjs-dist` (v3), `tesseract.js` (v7)      | In-browser PDF extraction and OCR parsing            |
| **Data Visualization**        | Recharts (`recharts`)                       | Attendance trend tracking and analytics              |
| **Utility Libraries**         | `date-fns`, `sonner`, `zod`                 | Date parsing, notification toasts, schema validation |

---

## Roadmap / Future Scope

The following items represent planned architectural directions and are explicitly labeled as **FUTURE SCOPE**:

* **Shared Academic Knowledge & Resource System**: A peer-contributed academic resource network allowing verified notes, syllabus guides, and previous examination solutions to be contributed and accessed across student cohorts, seniors, and faculty.
* **Native Push & Schedule Notifications**: Service Worker integration for local device alerts before upcoming classes and morning briefing summaries.
* **LMS Synchronization**: Two-way integration with institutional learning management platforms (Moodle, Canvas, Blackboard) via open APIs.

---

## Author

**Mahima Yadav**<br />
B.Sc. Information Technology<br />
NIMS University

* **GitHub**: [@mahimayaduvanshi](https://github.com/mahimayaduvanshi)
* **Live Application**: [https://studentos-academic.vercel.app/](https://studentos-academic.vercel.app/)
