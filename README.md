# 🚀 LeadFlow AI GovCon Command Center

AI-powered system for sourcing, scoring, and automating federal contract opportunities.

Built for agencies, operators, and founders who want to identify, qualify, and respond to GovCon opportunities faster using automation + AI.

---

## 🧠 What This Is

The LeadFlow AI GovCon Command Center is an end-to-end automation system that:

- Pulls opportunities from SAM.gov
- Extracts and analyzes solicitation documents including PDF, DOCX, XLSX, amendments, and attachments
- Scores opportunities using a bid / no-bid decision engine
- Generates structured summaries and opportunity reports
- Produces draft proposal content
- Displays the opportunity pipeline in a clean dashboard

---

## ⚙️ Core System Architecture

SAM.gov → Intake → Attachment Download → Document Classification → AI Extraction → Bid Scoring → Report Generation → Proposal Drafting → Dashboard

---

## ⚙️ Built With

- n8n for workflow automation
- PostgreSQL for structured data storage
- Google Sheets for optional client-facing tracking
- AI models for document parsing, scoring, summarization, and proposal generation
- Node.js / Next.js for dashboard development
- Docker for deployment and service management

---

## 🔄 Workflow System

### Core Workflows

- WF_01_Federal_Intake_Orchestrator
- WF_02_Download_Solicitation_Attachments
- WF_03_Classify_And_Extract_Solicitation_Files
- WF_04_Bid_No_Bid_Scoring
- WF_05_Opportunity_Report_And_Notifications
- WF_06_Document_Ingestion_And_Classification
- WF_07_Proposal_Generator

---

## 📊 Main Features

### Opportunity Intake

- Ingests federal opportunities from SAM.gov
- Supports filtering by NAICS, PSC, set-aside type, keywords, and due dates
- Normalizes incoming opportunity data
- Tracks pipeline status from intake to proposal

### Solicitation File Processing

- Downloads solicitation attachments
- Handles PDFs, DOCX files, XLSX files, amendments, and supporting documents
- Classifies documents by type
- Keeps the latest amendment version as the source of truth

### AI Document Extraction

- Extracts important solicitation sections
- Identifies Section B, PWS, Section L, Section M, CLINs, and compliance requirements
- Produces clean summaries for faster review
- Reduces manual reading time for proposal teams

### Bid / No-Bid Scoring

- Scores opportunities based on fit, deadline, complexity, competition, and available information
- Produces a recommendation
- Explains the reasoning behind the score
- Helps users avoid wasting time on low-fit opportunities

### Reporting And Notifications

- Generates opportunity summaries
- Sends important status updates
- Tracks recommendation, reasoning, bid score, and proposal status
- Supports client-facing reporting through dashboard or spreadsheet views

### Proposal Generation

- Creates structured draft proposal content
- Uses extracted solicitation requirements
- Helps proposal teams move faster from opportunity review to response draft

---

## 🧱 Planned Repository Structure

```text
/workflows
/dashboard
/database
/scripts
/docs
