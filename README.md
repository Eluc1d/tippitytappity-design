mermaid 
```
classDiagram
  User "1" --> "0..*" TypingTest : attempts
  Phrase "1" --> "0..*" TypingTest : used_in

  class User {
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

  class Phrase {
    - id: int
    - text: string
    - difficulty: string
    - category: string
    + get_word_count() int
  }

  class TypingTest {
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
