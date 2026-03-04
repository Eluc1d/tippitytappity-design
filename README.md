# tippitytappity-design

tippitytappity is a program to practice typing


## Data model

```mermaid
classDiagram

  class user{
        - name: string
        - email: string
        - password: string
        + login(user: string, pass: string) boolean
        + get_email() string
  }
  class ExampleChild{
        - badges vector~string~
        + add_badge(title: string)
        + get_badges() vector~string~
  }
```
