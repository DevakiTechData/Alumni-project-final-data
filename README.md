# Alumni-project-final-data

🧾 Students Table — students_1
📘 Overview

The students_1 table is the foundational dataset of the SLU Alumni Connect data model.
It stores demographic, academic, and immigration details for 1,000 SLU students (both current and graduated).
All subsequent tables (e.g., alumni_1, jobs_1, events_1, engagements_1) reference this table via the student_id primary key.

This table serves as the central identity hub for connecting students to employment, alumni engagement, and event participation data.

🧱 Table Summary
Feature	Description
Table Name	students_1
Rows	1,000
Columns	21
Primary Key	student_id
Added Column	serial_no (auto-generated sequence 1–1000)
Purpose	Capture student demographic, academic, and location details
Data Source	Synthetic data generated using Python (pandas, numpy, faker)
Version	v1.0 (Cleaned & Validated – October 2025)
🧩 Column Descriptions
Column Name	Description	Example	Notes
serial_no	Sequential number for reference	1	Added for tracking and indexing
student_id	Unique UUID for each student	c7a4e02e-…	Primary Key
slu_banner_id	SLU internal Banner system ID	B0100001	Unique institutional ID
first_name	Student’s first name	Angela	—
last_name	Student’s last name	Lawrence	—
preferred_name	Optional nickname or short name	Angie	Can be blank if same as first name
slu_email	Official SLU email address	alawrence1@slu.edu	Unique
personal_email	Personal Gmail/Yahoo email	angela.lawrence1@gmail.com	Backup contact
phone_e164	Phone number in international format	+13145551234	E.164 standard
program_name	Academic program	MS Cybersecurity	Mapped to SLU schools
college_name	Associated school/college	School of Science & Engineering	—
concentration	Focus area within the program	Data Analytics	Optional specialization
start_term	Program start term	Fall-2023	Used for trend analysis
grad_term	Graduation term	Spring-2025	—
graduation_year	Year of graduation	2025	Integer field
visa_status	Immigration category	F1, H1B, PR, Citizen, Other	Important for OPT analytics
opt_status	Work authorization status	None, OPT, STEM OPT	Applies mainly to F1 students
current_location_city	Current city of residence	St. Louis	Used for geo-mapping
current_location_state	State (if USA)	MO	Blank for non-US locations
current_location_country	Country of residence	USA, India	80% USA / 20% India distribution
linkedin_url	Professional LinkedIn profile URL	https://linkedin.com/in/angela-lawrence	For alumni tracking
🌍 Data Highlights
Attribute	Distribution
Country Mix	80% USA 🇺🇸 / 20% India 🇮🇳
Top Cities (USA)	St. Louis, Chicago, Dallas, Austin, Seattle, Boston, New York
Top Cities (India)	Hyderabad, Bengaluru
Common Programs	MS Information Systems, MS Data Science, MS Cybersecurity, MS Software Engineering
Visa Breakdown	60% F1, 15% Citizen, 10% H1B, 10% PR, 5% Other
OPT/STEM OPT	Present for 40% of F1 students
🧹 Data Quality Notes

✅ No missing or blank cells (cleaned via forward/backward fill)

✅ All emails, phone numbers, and URLs are synthetically generated and unique

✅ Compatible with SQL imports and Power BI

✅ UTF-8 encoded CSV format for cross-platform use

✅ Matches SLU AUP-compliant anonymization standards

📦 File Information
Property	Value
File Name	students_1_final.csv
Size	~350 KB
Encoding	UTF-8
Generated On	Oct 2025
Tool Used	Python 3.13 (pandas, numpy, faker)
Usage	MySQL seed table, Power BI source, Data Governance demo
🔗 Relationships with Other Tables
Related Table	Relationship Type	Key
alumni_1	1 → 1	student_id
jobs_1	1 → many	student_id
event_attendance_1	1 → many	student_id
engagements_1	indirect (via alumni_1)	alumni_id → student_id
🧠 Example Use Cases

Power BI visualization of Alumni Locations

Analysis of OPT/STEM OPT employment outcomes

Tracking program popularity by graduation year

Joining with events for participation insights

Linking with employers for job placement analytics
