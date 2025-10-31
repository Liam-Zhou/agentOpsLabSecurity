# SAFE ↔ DESIGN_REVIEW Schema (Full Detail, No PK/FK)

```mermaid
erDiagram
    SAFE {
        string safe_id
        string template
        boolean submitted
        string form_id
        string user
        string target_release_date
        string release_type
        string platforms
    }

    SAFE_QUESTION {
        string qid
        string question
        string response
    }

    APPLICATION {
        string app_name
        string template
        array  questions
    }

    APP_QUESTION {
        string qid
        string question
        string response
    }

    DESIGN_REVIEW {
        string dr_id
        string safe_id
        boolean is_submitted
        string summary_note
    }

    APP_CONTROL_GROUP {
        string app_name
        string stack
        array controls
    }

    CONTROL {
        string control_category
        string control_name
        string stack
        string evidence_collection
        boolean evidence_request_selected
        string recommendation
        string traffic
    }

    SAFE ||--o{ SAFE_QUESTION : has_questions
    SAFE ||--o{ APPLICATION : has_applications
    APPLICATION ||--o{ APP_QUESTION : has_app_questions

    SAFE ||--|| DESIGN_REVIEW : linked_by_safe_id
    DESIGN_REVIEW ||--o{ APP_CONTROL_GROUP : has_app_control_groups
    APP_CONTROL_GROUP ||--o{ CONTROL : has_controls
