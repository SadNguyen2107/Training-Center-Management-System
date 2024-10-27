<head>
    <link rel="stylesheet" href="styles.css">
</head>

# Team 10: Training-Center-Management-System

<details>
<summary>Table of Contents</summary>

1. [Introduction :star:](#introduction)
2. [Team Members :man_technologist:](#team-members)
3. [Database Design :computer:](#training-center-management-system-database-design)

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
        int session_id PK
        string title
        string content
        int course_id FK
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
        string description
        float score
        int session_id FK
        int student_id FK
    }
    
    ATTENDANCE {
        int attendance_id PK
        int session_id FK
        int student_id FK
        int instructor_id FK
        boolean is_present
    }
    
    BILLING {
        int billing_id PK
        int student_id FK
        int instructor_id FK
        float total_amount
    }
    
    COURSE ||--o{ SESSION : has
    COURSE ||--o{ INSTRUCTOR : assigned_to
    SESSION ||--o{ ASSIGNMENT : has
    STUDENT ||--o{ COURSE : registers_for
    STUDENT ||--o{ SESSION : attends
    STUDENT ||--o{ ASSIGNMENT : completes
    INSTRUCTOR ||--o{ SESSION : teaches
    INSTRUCTOR ||--o{ ATTENDANCE : logs
    ATTENDANCE }o--|| SESSION : logged_for
    ATTENDANCE }o--|| STUDENT : for
    STUDENT ||--o{ BILLING : pays
    BILLING }o--|| INSTRUCTOR : get_paid
```