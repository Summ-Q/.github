# SummQ

SummQ is a spaced-repetition study platform that automates flashcard creation using artificial intelligence. This organization contains the source code for the mobile client, the core backend API, and the data science microservice.

## Problem Statement

Manual flashcard creation is highly inefficient and disrupts the learning workflow. Existing solutions either require manual data entry, which consumes hours of study time, or they lack sophisticated spaced-repetition algorithms. Students need a system that minimizes preparation time and maximizes retention through optimized, data-driven review schedules.

## Project Idea

SummQ eliminates manual deck creation by parsing user-uploaded study materials (PDFs and text notes) and generating high-quality question-and-answer pairs via an AI pipeline. The application then schedules these flashcards for review using a custom spaced-repetition algorithm that adapts to the user's historical recall accuracy, ensuring optimal memory retention.

## Target Audience

* **University Students:** Specifically those in high-volume memorization fields like medicine, law, and engineering.
* **Language Learners:** Users building vocabulary through aggressive repetition.
* **Certification Candidates:** Professionals studying for standardized technical or medical board exams.

## Technologies Used

The SummQ ecosystem is split into three core repositories, utilizing a microservices architecture:

* **Frontend Client:** Flutter, Dart
* **Core API:** Laravel 11, PHP, Sanctum (Auth)
* **Data Science / AI Service:** Python (Data processing, LLM integration, Spaced Repetition calculation)
* **Database & Infrastructure:** PostgreSQL (Supabase), Vercel (Serverless deployments)

## Application User Flow

The following diagram outlines the standard user journey from authentication to active studying.

```mermaid
graph TD
    %% Node Styling
    classDef user fill:#2d3748,stroke:#4a5568,color:#fff;
    classDef backend fill:#2b6cb0,stroke:#2c5282,color:#fff;
    classDef python fill:#276749,stroke:#22543d,color:#fff;
    classDef db fill:#744210,stroke:#5f370e,color:#fff;

    %% Authentication Flow
    A([User Opens App]) --> B{Has Account?}
    B -- No --> C[Register]
    B -- Yes --> D[Login]
    C --> E[Laravel API: Generate Sanctum Token]
    D --> E
    E --> F[(Supabase: Users Table)]

    %% Deck Creation & Generation
    F --> G[Dashboard]
    G --> H[Create New Deck]
    H --> I[Upload PDF / Enter Notes]
    I --> J[Laravel API: Request Generation]
    J --> K[Python API: Parse & Generate Cards]
    K --> L[Laravel API: Receive JSON Cards]
    L --> M[(Supabase: Flashcards Table)]

    %% Studying Phase
    M --> N[Start Study Session]
    N --> O[Laravel API: Fetch Due Cards]
    O --> P[Display Card]
    P --> Q[User Submits Score 1-4]
    Q --> R[Laravel API: Log Review]
    R --> S[Python API: Calculate Next Due Date]
    S --> T[(Supabase: Study Progress)]
    T --> U{More Cards Due?}
    U -- Yes --> P
    U -- No --> V([Session Complete])

    %% Apply Classes Safely
    class A,B,C,D,G,H,I,N,P,Q,U,V user;
    class E,J,L,O,R backend;
    class K,S python;
    class F,M,T db;
```
