2025/04/10 18:37
Status: #idea
Tags:

# LMS DB Project

### Users

Multiple user types will exist within a unified users table with role differentiation:

Users={students,instructors,administrators,teaching assistants}\text{Users} = \{\text{students}, \text{instructors}, \text{administrators}, \text{teaching assistants}\}Users={students,instructors,administrators,teaching assistants}

**Users Table**

- `user_id`: UUID (PK)
- `username`: VARCHAR(50) NOT NULL UNIQUE
- `email`: VARCHAR(255) NOT NULL UNIQUE
- `password_hash`: VARCHAR(255) NOT NULL
- `first_name`: VARCHAR(50) NOT NULL
- `last_name`: VARCHAR(50) NOT NULL
- `middle_name`: VARCHAR(50) NULL
- `role`: ENUM ('student', 'instructor', 'teaching_assistant', 'administrator')
- `bio`: TEXT NULL
- `profile_image_url`: VARCHAR(255) NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP
- `last_login`: TIMESTAMP NULL
- `active`: BOOLEAN DEFAULT TRUE

**Student Profiles** (extends user information for students)

- `student_id`: UUID (PK, FK to users.user_id)
- `class_standing`: ENUM ('freshman', 'sophomore', 'junior', 'senior', 'graduate')
- `major`: VARCHAR(100) NULL
- `minor`: VARCHAR(100) NULL
- `concentration`: VARCHAR(100) NULL
- `expected_graduation`: DATE NULL
- `advisor_id`: UUID NULL (FK to users.user_id where role='instructor')
- `gpa`: DECIMAL(3,2) NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

### Academic Organization

**Departments**

- `department_id`: UUID (PK)
- `name`: VARCHAR(100) NOT NULL
- `code`: VARCHAR(20) NOT NULL UNIQUE
- `description`: TEXT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Terms** (semesters, quarters, etc.)

- `term_id`: UUID (PK)
- `name`: VARCHAR(100) NOT NULL
- `start_date`: DATE NOT NULL
- `end_date`: DATE NOT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

### Courses

**Courses Table**

- `course_id`: UUID (PK)
- `department_id`: UUID (FK to departments)
- `term_id`: UUID (FK to terms)
- `name`: VARCHAR(255) NOT NULL
- `start_date`: DATE NULL
- `end_date`: DATE NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Course Sections**

- `section_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `section_number`: VARCHAR(10) NOT NULL
- `capacity`: INTEGER NOT NULL 
- `location`: VARCHAR(100) NULL
- `meeting_times`: TEXT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP
- UNIQUE(course_id, section_number)

### Enrollments

The enrollment relationship between users and courses:

$$Enrollment⊆Users×Courses×Roles×Timestamp $$

**Enrollments Table**

- `enrollment_id`: UUID (PK)
- `user_id`: UUID (FK to users)
- `course_id`: UUID (FK to courses)
- `section_id`: UUID (FK to course_sections) NULL
- `role`: ENUM ('student', 'instructor', 'teaching_assistant')
- `enrollment_date`: TIMESTAMP DEFAULT NOW()
- `last_activity`: TIMESTAMP NULL
- `is_active`: BOOLEAN DEFAULT TRUE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP
- UNIQUE(user_id, course_id)

### Course Content Organization

**Modules**

- `module_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `position`: INTEGER NOT NULL
- `is_published`: BOOLEAN DEFAULT FALSE
- `unlock_date`: TIMESTAMP NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Module Items**

- `item_id`: UUID (PK)
- `module_id`: UUID (FK to modules)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `item_type`: VARCHAR(50) NOT NULL
    - Options: 'page', 'file', 'assignment', 'quiz', 'discussion', 'external_url', 'text_header'
- `content_id`: UUID NULL (references ID in respective content table)
- `position`: INTEGER NOT NULL
- `is_published`: BOOLEAN DEFAULT FALSE
- `points_possible`: DECIMAL(10,2) NULL
- `due_date`: TIMESTAMP NULL
- `unlock_date`: TIMESTAMP NULL
- `lock_date`: TIMESTAMP NULL
- `external_url`: VARCHAR(255) NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

### Assignments and Assessment

**Assignments**

- `assignment_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `instructions`: TEXT NULL
- `assignment_type`: ENUM ('quiz', 'assignment', 'discussion', 'project', 'exam')
- `points_possible`: DECIMAL(10,2) NOT NULL
- `due_date`: TIMESTAMP NULL
- `available_from`: TIMESTAMP NULL
- `available_until`: TIMESTAMP NULL
- `is_published`: BOOLEAN DEFAULT FALSE
- `submission_types`: VARCHAR(255) NULL
- `allow_late_submissions`: BOOLEAN DEFAULT FALSE
- `late_submission_deduction`: DECIMAL(5,2) NULL
- `group_assignment`: BOOLEAN DEFAULT FALSE
- `peer_reviews`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Submissions**

- `submission_id`: UUID (PK)
- `assignment_id`: UUID (FK to assignments)
- `user_id`: UUID (FK to users)
- `status`: ENUM ('draft', 'submitted', 'late', 'graded', 'resubmitted')
- `submitted_at`: TIMESTAMP NULL
- `content`: TEXT NULL
- `file_url`: VARCHAR(255) NULL
- `online_url`: VARCHAR(255) NULL
- `submission_comments`: TEXT NULL
- `is_late`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP
- UNIQUE(assignment_id, user_id)

**Grades**

- `grade_id`: UUID (PK)
- `submission_id`: UUID (FK to submissions)
- `grader_id`: UUID (FK to users)
- `score`: DECIMAL(10,2) NULL
- `feedback`: TEXT NULL
- `status`: ENUM ('not_graded', 'grading_in_progress', 'graded', 'muted')
- `graded_at`: TIMESTAMP NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Course Grades**

- `course_grade_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `user_id`: UUID (FK to users)
- `final_grade`: DECIMAL(5,2) NULL
- `letter_grade`: VARCHAR(5) NULL
- `is_passing`: BOOLEAN NULL
- `calculated_at`: TIMESTAMP
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP
- UNIQUE(course_id, user_id)

### Discussion Forums

**Discussion Forums**

- `forum_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `is_published`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Discussion Topics**

- `topic_id`: UUID (PK)
- `forum_id`: UUID (FK to discussion_forums)
- `user_id`: UUID (FK to users)
- `title`: VARCHAR(255) NOT NULL
- `content`: TEXT NOT NULL
- `is_announcement`: BOOLEAN DEFAULT FALSE
- `is_pinned`: BOOLEAN DEFAULT FALSE
- `allow_replies`: BOOLEAN DEFAULT TRUE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Discussion Replies**

- `reply_id`: UUID (PK)
- `topic_id`: UUID (FK to discussion_topics)
- `user_id`: UUID (FK to users)
- `parent_reply_id`: UUID NULL (FK to discussion_replies)
- `content`: TEXT NOT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

### Announcements and Calendar

**Announcements**

- `announcement_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `user_id`: UUID (FK to users)
- `title`: VARCHAR(255) NOT NULL
- `content`: TEXT NOT NULL
- `is_published`: BOOLEAN DEFAULT FALSE
- `published_at`: TIMESTAMP NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Calendar Events**

- `event_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `start_date`: TIMESTAMP NOT NULL
- `end_date`: TIMESTAMP NULL
- `location`: VARCHAR(255) NULL
- `is_all_day`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

### Learning Resources

**Files** (course materials and student uploads)

- `file_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `user_id`: UUID (FK to users)
- `filename`: VARCHAR(255) NOT NULL
- `file_path`: VARCHAR(255) NOT NULL
- `file_type`: VARCHAR(50) NULL
- `file_size`: BIGINT NULL
- `is_public`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

## Entity-Relationship Diagram

The following is the formal expression of the core relationships in the database:

Student⊂User\text{Student} \subset \text{User}Student⊂User Instructor⊂User\text{Instructor} \subset \text{User}Instructor⊂User Course⇒Department×Term\text{Course} \Rightarrow \text{Department} \times \text{Term}Course⇒Department×Term Enrollment⇒User×Course\text{Enrollment} \Rightarrow \text{User} \times \text{Course}Enrollment⇒User×Course Module⇒Course\text{Module} \Rightarrow \text{Course}Module⇒Course Assignment⇒Course\text{Assignment} \Rightarrow \text{Course}Assignment⇒Course Submission⇒Assignment×User\text{Submission} \Rightarrow \text{Assignment} \times \text{User}Submission⇒Assignment×User Grade⇒Submission\text{Grade} \Rightarrow \text{Submission}Grade⇒Submission

## Additional Features

### Quizzes and Tests

**Quizzes**

- `quiz_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `instructions`: TEXT NULL
- `time_limit_minutes`: INTEGER NULL
- `allowed_attempts`: INTEGER DEFAULT 1
- `shuffle_questions`: BOOLEAN DEFAULT FALSE
- `show_correct_answers`: BOOLEAN DEFAULT TRUE
- `show_correct_answers_after`: TIMESTAMP NULL
- `due_date`: TIMESTAMP NULL
- `available_from`: TIMESTAMP NULL
- `available_until`: TIMESTAMP NULL
- `points_possible`: DECIMAL(10,2) NOT NULL
- `is_published`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Quiz Questions**

- `question_id`: UUID (PK)
- `quiz_id`: UUID (FK to quizzes)
- `question_text`: TEXT NOT NULL
- `question_type`: VARCHAR(50) NOT NULL
    - Options: 'multiple_choice', 'true_false', 'essay', 'matching', 'fill_in_blank'
- `points`: DECIMAL(10,2) NOT NULL
- `position`: INTEGER NOT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Quiz Question Options**

- `option_id`: UUID (PK)
- `question_id`: UUID (FK to quiz_questions)
- `option_text`: TEXT NOT NULL
- `is_correct`: BOOLEAN NULL
- `position`: INTEGER NOT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Quiz Attempts**

- `attempt_id`: UUID (PK)
- `quiz_id`: UUID (FK to quizzes)
- `user_id`: UUID (FK to users)
- `start_time`: TIMESTAMP NOT NULL
- `end_time`: TIMESTAMP NULL
- `is_completed`: BOOLEAN DEFAULT FALSE
- `score`: DECIMAL(10,2) NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Quiz Responses**

- `response_id`: UUID (PK)
- `attempt_id`: UUID (FK to quiz_attempts)
- `question_id`: UUID (FK to quiz_questions)
- `selected_option_id`: UUID NULL (FK to quiz_question_options)
- `text_response`: TEXT NULL
- `is_correct`: BOOLEAN NULL
- `points_earned`: DECIMAL(10,2) NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

### Group Collaboration

**Group Categories**

- `category_id`: UUID (PK)
- `course_id`: UUID (FK to courses)
- `name`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `allow_self_signup`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Groups**

- `group_id`: UUID (PK)
- `category_id`: UUID (FK to group_categories)
- `name`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Group Memberships**

- `membership_id`: UUID (PK)
- `group_id`: UUID (FK to groups)
- `user_id`: UUID (FK to users)
- `is_leader`: BOOLEAN DEFAULT FALSE
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP
- UNIQUE(group_id, user_id)

### Rubrics and Assessment Tools

**Rubrics**

- `rubric_id`: UUID (PK)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `is_public`: BOOLEAN DEFAULT FALSE
- `created_by`: UUID (FK to users)
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Rubric Criteria**

- `criteria_id`: UUID (PK)
- `rubric_id`: UUID (FK to rubrics)
- `title`: VARCHAR(255) NOT NULL
- `description`: TEXT NULL
- `points`: DECIMAL(10,2) NOT NULL
- `position`: INTEGER NOT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Rubric Ratings**

- `rating_id`: UUID (PK)
- `criteria_id`: UUID (FK to rubric_criteria)
- `description`: TEXT NOT NULL
- `points`: DECIMAL(10,2) NOT NULL
- `position`: INTEGER NOT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

**Rubric Associations**

- `association_id`: UUID (PK)
- `rubric_id`: UUID (FK to rubrics)
- `association_type`: VARCHAR(50) NOT NULL
- `association_id`: UUID NOT NULL
- `created_at`: TIMESTAMP
- `updated_at`: TIMESTAMP

## Mathematical Model of Grade Calculation

The final grade calculation in a course can be expressed as:

Gfinal=∑i=1n(SiPi×Wi)×100G_{final} = \sum_{i=1}^{n} \left( \frac{S_i}{P_i} \times W_i \right) \times 100Gfinal​=∑i=1n​(Pi​Si​​×Wi​)×100

Where:

- $G_{final}$ is the final grade percentage
- $n$ is the number of assignment categories
- $S_i$ is the sum of scores in category $i$
- $P_i$ is the sum of possible points in category $i$
- $W_i$ is the weight of category $i$

## Design Notes

1. **UUID as Primary Keys**: Using UUIDs instead of sequential IDs provides better security and distributed database capabilities.
2. **Timestamps**: All tables include `created_at` and `updated_at` timestamps for audit and tracking purposes.
3. **Soft Deletion**: Most entities use status flags rather than actual deletion to preserve historical data.
4. **Denormalization**: Some strategic denormalization is used where query performance benefits outweigh storage concerns.
5. **Indexing Strategy**:
    - Foreign keys are indexed
    - Frequently queried columns are indexed
    - Composite indexes for common query patterns
6. **Constraints**:
    - Unique constraints prevent duplicate enrollments
    - Foreign key constraints maintain referential integrity
    - Check constraints enforce business rules
7. **Extensibility**: The schema design allows for future extensions through additional related tables rather than modifying existing structures.

---

## References

- PostgreSQL Documentation
- Canvas LMS API Documentation
- Database Design Best Practices




---
# References
