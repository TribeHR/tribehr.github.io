---
category: Internal
title: 'System Info'
type: 'GET'
path: '/system_info'

layout: default
---

The mobile app uses this endpoint to retrieve information about the user's company's account.

Currently, the information returned is limited to the company's name, enabled TribeHR package-level features, and leave types.

```GET /system_info.json
X-API-Version: 2.0.0
```

```Status: 200 OK```
```Content-Type: application/json
{
    "company": {
        "name": "My Fabulous Company"
    },
    "enabled_features": [
        "badges",
        "phone_and_email_support",
        "netsuite_user_sync",
        "quizzes",
        "notes_and_feedback",
        "micro_feedback",
        "goal_setting",
        "skills_tracking",
        "reviews_and_review_cycles",
        "supported_goals",
        "directory",
        "employee_profiles",
        "org_chart",
        "employee_documents",
        "basic_reports",
        "advanced_reports",
        "custom_fields",
        "compensation_tracking",
        "history_timeline_view",
        "incident_reports",
        "eeo",
        "locations",
        "location_content",
        "report_filtering",
        "ad_hoc_reporting",
        "employee_file_reports",
        "standard_performance_reports",
        "payroll_time_tracking_reports",
        "eeo1_reports",
        "feedback_and_values_reports",
        "osha_reports",
        "ats_reports",
        "new_importer",
        "company_calendar",
        "vacation_and_sick_tracking",
        "calendar_export",
        "custom_pto",
        "time_tracking",
        "job_postings",
        "email_resume_collection",
        "team_reviewers",
        "advanced_recruiting_reports",
        "facebook_job_postings_application",
        "custom_job_board_layout",
        "multiple_custom_job_boards",
        "payroll_report",
        "xml_api",
        "webhooks_notifications",
        "google_apps_login",
        "rss_import",
        "salesforce",
        "freshbooks",
        "hipchat",
        "company_values",
        "netsuite",
        "nicknames",
        "job_posting_syndication",
        "slack",
        "weekly_email_summary",
        "account_representative",
        "custom_logo",
        "kudos_and_public_recognition",
        "labs"
    ],
    "leave_types": [
        {
            "id": 1,
            "name": "Vacation",
            "accrual": "SEMIMONTHLY",
            "url": "/leave_types/1.json"
        },
        {
            "id": 2,
            "name": "Sick",
            "accrual": "ANNUAL",
            "url": "/leave_types/2.json"
        },
        {
            "id": 3,
            "name": "Travel",
            "accrual": "NONE",
            "url": "/leave_types/3.json"
        },
        {
            "id": 5,
            "name": "Floater",
            "accrual": "ANNUAL",
            "url": "/leave_types/5.json"
        },
        {
            "id": 6,
            "name": "Remote Work",
            "accrual": "NONE",
            "url": "/leave_types/6.json"
        },
        {
            "id": 7,
            "name": "Volunteer",
            "accrual": "ANNUAL",
            "url": "/leave_types/7.json"
        },
        {
            "id": 8,
            "name": "Birthday (BDO)",
            "accrual": "ANNUAL",
            "url": "/leave_types/8.json"
        }
    ]
}
```