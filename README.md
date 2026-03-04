# TippityTappity

A typing practice application that tests your accuracy and speed across a wide range of phrases covering letters, numbers, and symbols.

## Features

- **Accuracy Testing** — Measure how precisely you type a given phrase
- **Speed Testing** — Track your words per minute (WPM)
- **Multi-user Support** — Each user has their own account and progress history
- **Test History** — Every attempt is saved so users can monitor improvement over time

---

## Data Model

```mermaid
classDiagram
  User "1" --> "0..*" TypingTest : attempts
  Phrase "1" --> "0..*" TypingTest : used_in
  class User{
        - id: int
        - username: string
        - email: string
        - password_hash: string
        - created_at: datetime
        + register(username: string, email: string, password: string) User
        + login(username: string, password: string) boolean
        + get_history() vector~TypingTest~
        + get_average_wpm() float
        + get_average_accuracy() float
  }
  class Phrase{
        - id: int
        - text: string
        - difficulty: string
        - category: string
        + get_word_count() int
  }
  class TypingTest{
        - id: int
        - user_id: int
        - phrase_id: int
        - wpm: float
        - accuracy: float
        - duration_seconds: float
        - attempted_at: datetime
        + calculate_wpm(char_count: int, duration_seconds: float) float
        + calculate_accuracy(expected: string, actual: string) float
  }
```

### Entity Descriptions

**User** — Represents a registered account. Stores credentials and provides methods to retrieve personal test history and aggregate performance stats.

**Phrase** — A prompt presented to the user during a typing test. Phrases vary by difficulty (e.g. easy, medium, hard) and category (e.g. letters-only, numbers, symbols, mixed) to exercise different typing skills.

**TypingTest** — A single recorded attempt by a user on a phrase. Captures the WPM, accuracy percentage, total duration, and timestamp of the attempt.

---

## Relationships

| Relationship | Description |
|---|---|
| User → TypingTest | A user can have zero or more test attempts |
| Phrase → TypingTest | A phrase can appear in zero or more test attempts |
