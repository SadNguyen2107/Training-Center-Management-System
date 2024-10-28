<head>
    <link rel="stylesheet" href="styles.css">
</head>

# Team 10: Training-Center-Management-System

<details>
<summary>Table of Contents</summary>

- [Team 10: Training-Center-Management-System](#team-10-training-center-management-system)
  - [Introduction](#introduction)
  - [Team Members](#team-members)
  - [Training Center Management System Database Design](#training-center-management-system-database-design)

</details>

## Introduction
A project to turn in to a lecturer for the Database Design course at [HUST_Hanoi University of Science and Technology :school:](https://hust.edu.vn/) 

## Team Members
* [Nguyễn Trung Sơn _ 1624758 :man:](https://github.com/SadNguyen2107)
* [Nguyễn Văn Trí _ 1624782 :man:](https://github.com/TGaDev203)

## Training Center Management System Database Design
```mermaid
---
title: Training Center Management System
---
erDiagram
    COURSE {
        int course_id PK
        string name
        string description
        float rate
    }

    SESSION {
        int section_id PK
        int course_id FK
        string title
        string content
    }

    STUDENT {
        int student_id PK
        string name
    }

    INSTRUCTOR {
        int instructor_id PK
        string name
        float personal_level
    }

    ASSIGNMENT {
        int assignment_id PK
        int session_id FK
        int student_id FK
        string description
        float score
    }

    BILLING {
        int bill_id PK
        int student_id FK
        int instructor_id FK
        int course_id FK
    }

    ATTENDANCE {
        int attendance_id PK
        int session_id FK
        int student_id FK
        int instructor_id FK
        boolean is_present
    }

    COURSE ||--|{ SESSION : includes
    SESSION ||--o{ ASSIGNMENT : contains
    SESSION ||--o{ ATTENDANCE : tracks
    ATTENDANCE }o--|| STUDENT : records_for
    ATTENDANCE }o--|| INSTRUCTOR : records_for
    ASSIGNMENT }o--|| STUDENT : submitted_by

    STUDENT ||--o{ BILLING : incurs
    INSTRUCTOR ||--o{ BILLING : receives
    COURSE ||--o{ BILLING : generates
```