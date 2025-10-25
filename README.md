# Alumni-project-final-data

**🧾 Students Table — students_1**------------------------------------
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


**🧾 Alumni Table — alumni_1**---------------------------------------------------------------------------
📘 Overview

The alumni_1 table represents all Saint Louis University (SLU) graduates and alumni who have transitioned from student status to professional careers.
This dataset captures their career progression, professional achievements, engagement interests, and visibility preferences, forming a bridge between the academic (students_1) and corporate (employers_1) datasets.

The table is foundational for analyzing:

Post-graduation outcomes

Alumni involvement and mentoring patterns

Employer and industry relationships

Skills and experience mapping across graduating cohorts

🧱 Table Summary
Feature	Description
Table Name	alumni_1
Rows	1,000
Columns	21
Primary Key	alumni_id
Foreign Key	student_id → students_1.student_id
Purpose	Track career details, skills, certifications, and engagement of SLU alumni
Data Source	Synthetic dataset generated via Python (pandas, faker, numpy)
Blank Cells	None — every cell is filled with valid data
Version	v1.0 (Cleaned & Validated – October 2025)
🧩 Column Descriptions
#	Column Name	Description	Example
1	serial_no	Sequential record number	1
2	alumni_id	Unique UUID for each alumnus (Primary Key)	63658156-bd48-4a5f-829f-9560e7398536
3	student_id	Foreign Key reference to students_1	2758bec7-dbb0-4bc7-ae51-7bcc277e4245
4	current_employer_id	Employer identifier linking to employers_1	EMP000001
5	current_title	Current job title or role	Data Engineer
6	years_experience	Total years of work experience	7.3
7	career_stage	Career level — Early, Mid, Senior, or Lead	Senior
8	skills_primary	Primary technical or functional skills	Python, SQL, Statistics
9	skills_secondary	Secondary or complementary skills	Communication, Teamwork
10	certifications	Professional certifications held	AWS CCP, Security+
11	achievements	Key academic or professional recognitions	Hackathon Winner, Dean’s List
12	mentoring_interest	1 if the alumnus is open to mentoring current students	1
13	volunteering_interest	1 if the alumnus is interested in volunteering	0
14	is_active_member	Indicates whether currently active in SLU Alumni network	1
15	last_engagement_date	Last recorded engagement or event participation date	2024-05-23
16	profile_visibility	Visibility scope — Public, SLU-only, or Private	SLU-only
17	preferred_contact_method	Preferred method of contact	LinkedIn, Email, or Phone
18	preferred_time_zone	Time zone used for meetings or mentoring	America/Chicago
19	portfolio_url	Portfolio or personal website	https://portfolio.example.com/jane-doe-4
20	github_url	GitHub profile URL	https://github.com/jdoe4
21	created_at	Record creation timestamp (UTC)	2025-10-25 04:21:33
🌍 Data Highlights
Attribute	Distribution / Notes
Years of Experience	0.0–12.0 years, normally distributed
Career Stage	Early (<2), Mid (2–5), Senior (5–10), Lead (>10)
Mentoring & Volunteering	Each ~50% of alumni participate
Profile Visibility	45% Public, 35% SLU-only, 20% Private
Certifications	AWS CCP, Azure Fundamentals, PMP, Security+, None
Time Zones	America/Chicago, America/New_York, America/Los_Angeles
🧹 Data Quality Notes

✅ No missing or null fields.

✅ All UUIDs and URLs validated syntactically.

✅ Dates follow ISO-8601 format.

✅ CSV encoded in UTF-8, ready for MySQL or Power BI import.

✅ Matches SLU AUP anonymization and data governance guidelines.

🔗 Relationships with Other Tables
Related Table	Relationship	Key Field
students_1	One-to-One	student_id
employers_1	Many-to-One	current_employer_id
engagements_1	One-to-Many	alumni_id
events_1	Indirect	via engagements_1 or event participation
📊 Use Cases in Analytics Dashboards
Dashboard	Insights Enabled
Alumni Dashboard	Employment distribution by job title, skills, and experience
Employer Dashboard	Employer engagement by alumni count and career stage
Engagement Dashboard	Mentoring, volunteering, and event involvement trends
Career Path Dashboard	Certifications vs. role progression correlations
📂 File Information
Property	Value
File Name	alumni_1_final.csv
Size	~350 KB
Encoding	UTF-8
Created On	Oct 25, 2025
Tool Used	Python (pandas, faker, datetime, uuid)
Usage	MySQL table seed, Power BI data model input, analytics prototype
