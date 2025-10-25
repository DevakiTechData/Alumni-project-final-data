🎓 SLU Alumni Connect — Synthetic Data Repository (2020–2026)
📘 Overview

This repository contains synthetic, realistic datasets representing Saint Louis University’s Alumni Engagement, Career Development, and Employer Partnership ecosystem between 2020 and 2026.

The data supports Power BI dashboards, ETL pipelines, and MySQL database integration for the DataNexus SLU Alumni Connect Project.

All datasets have been generated using Python (Pandas, Faker, NumPy) and validated for referential integrity, ensuring no nulls and consistent foreign key mappings.

🧩 Dataset Summary
#	Table Name	Records	Columns	Description
1	students_1_final_2020_2026.csv	1,000	21	SLU student profiles including academic, visa, and contact details.
2	alumni_1_final_2020_2026.csv	1,000	21	Alumni employment, job role, and post-graduation outcomes.
3	employers_1_final_2020_2026_faang.csv	1,000	22	Employer organizations including FAANG, non-profits, and SLU partners.
4	jobs_1_final_2020_2026.csv	1,000	21	Job listings associated with alumni and employers.
5	events_1_final_2020_2026.csv	1,000	21	University events such as career fairs, webinars, and workshops.
6	event_attendance_1_final_2020_2026.csv	1,000	21	Attendance, feedback, and certificates for students attending events.
7	engagements_1_final_2020_2026.csv	1,000	21	Alumni and employer contributions such as mentorships, talks, and sponsorships.
8	data_dictionary_2020_2026.csv	41	5	Metadata reference describing each table and column.
🧱 Database Structure & Relationships
erDiagram
    STUDENTS ||--o{ ALUMNI : "has"
    ALUMNI ||--o{ JOBS : "works in"
    ALUMNI ||--o{ ENGAGEMENTS : "participates in"
    EMPLOYERS ||--o{ JOBS : "offers"
    EMPLOYERS ||--o{ ENGAGEMENTS : "collaborates via"
    EVENTS ||--o{ EVENT_ATTENDANCE : "records"
    EVENTS ||--o{ ENGAGEMENTS : "linked to"
    STUDENTS ||--o{ EVENT_ATTENDANCE : "attends"

🧮 Table-wise Details
🧑‍🎓 1. Students Table (students_1_final_2020_2026.csv)

Represents all graduate students enrolled between 2020–2026.

Key Columns:

student_id → Primary key

slu_banner_id → Unique SLU system ID

program_name, college_name, concentration → Academic info

visa_status (F1 / H1B / PR / Citizen / Other)

opt_status (None / OPT / STEM OPT)

current_location_city/state/country

linkedin_url → Public professional profile

✅ Use case: Power BI visual on student demographics, visa distribution, program trends.

🧑‍💼 2. Alumni Table (alumni_1_final_2020_2026.csv)

Tracks post-graduation outcomes.

Key Columns:

alumni_id → PK

student_id → FK → students

employment_status → Full-time / Internship / Contract / Unemployed

employer_id → FK → employers

job_title, start_date, salary_band

faang_experience → Boolean (1 = yes)

✅ Use case: Alumni employment heatmaps, FAANG representation, OPT/STEM transitions.

🏢 3. Employers Table (employers_1_final_2020_2026_faang.csv)

Captures organization-level data.

Key Columns:

employer_id → PK

employer_name, industry, sub_industry

is_faang_company → 1 for FAANG, 0 otherwise

is_non_profit → NGOs, healthcare, education

slu_partnership_* → Type, level, status, start_date

faang_company_name_group → FAANG / Non-FAANG

✅ Use case: Analyze SLU–industry partnerships, FAANG diversity, and sponsorship trends.

💼 4. Jobs Table (jobs_1_final_2020_2026.csv)

Describes available or filled positions.

Key Columns:

job_id → PK

employer_id → FK → employers

alumni_id → FK → alumni

job_title, job_type, location_*, salary_usd, job_status

✅ Use case: Track employment outcomes by employer, alumni placement rates, and salary analytics.

🎟 5. Events Table (events_1_final_2020_2026.csv)

Covers all SLU-organized engagements.

Key Columns:

event_id → PK

event_name, event_type, event_theme

start_datetime, end_datetime, timezone

capacity, registrations_count, attendees_count

feedback_score_avg

✅ Use case: Event participation dashboard and organizer analytics.

🧾 6. Event Attendance Table (event_attendance_1_final_2020_2026.csv)

Tracks individual attendance and satisfaction.

Key Columns:

attendance_id → PK

event_id → FK → events

student_id → FK → students

registration_status, attended, check_in_method

feedback_score, certificate_issued

reminder_sent, reminder_sent_at

✅ Use case: Event-level engagement tracking and satisfaction analytics.

🤝 7. Engagements Table (engagements_1_final_2020_2026.csv)

Captures alumni & employer contributions to SLU.

Key Columns:

engagement_id → PK

alumni_id, employer_id, event_id → FKs

engagement_type → Mentorship / Sponsorship / Talk / Donation / Job Post / Volunteering / Workshop / Panel

points_awarded, hours_contributed, monetary_value_usd

satisfaction_rating, status, follow_up_required

privacy_level

✅ Use case: Quantify alumni contributions, sponsorship values, and engagement ratings.

🧠 Data Integrity & Quality

🔗 Referential Integrity:

All foreign keys validated (students → alumni → jobs, events → attendance → engagements).

🚫 No Nulls:

All columns filled (NA used as placeholder).

📅 Date Range:

01/01/2020 – 12/31/2026.

⏱ Format:

Dates as MM/DD/YYYY or MM/DD/YYYY HH:MM.

🔢 Volume:

7 datasets × 1,000 records each (≈ 7,000 rows total).

⚙️ Tools Used

Python Libraries: pandas, faker, numpy, uuid, datetime

Database: MySQL (InnoDB engine)

Visualization: Power BI, Tableau

Version Control: GitHub

Modeling: Mermaid ERD, dbdiagram.io

📁 Folder Structure
📂 SLU_Alumni_Data_2020_2026
 ┣ 📄 students_1_final_2020_2026.csv
 ┣ 📄 alumni_1_final_2020_2026.csv
 ┣ 📄 employers_1_final_2020_2026_faang.csv
 ┣ 📄 jobs_1_final_2020_2026.csv
 ┣ 📄 events_1_final_2020_2026.csv
 ┣ 📄 event_attendance_1_final_2020_2026.csv
 ┣ 📄 engagements_1_final_2020_2026.csv
 ┣ 📄 data_dictionary_2020_2026.csv
 ┗ 📘 README.md

🧭 Author & Context

Prepared by: Devaki Bathalapalli
Project: DataNexus SLU Alumni Connect (2025 MRP-2)
Institution: Saint Louis University (MSIS, 2024–2025)
Scope: Academic analytics prototype for Alumni–Employer–University engagement insights.
Supervised by: Prof. Tatiana & SLU ITS Leadership Team
