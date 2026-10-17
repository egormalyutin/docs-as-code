# Диаграммы

## Диаграмма последовательности

```mermaid
sequenceDiagram
    actor Recruiter as Рекрутёр
    participant System as Система
    participant Model as ML-модель

    Recruiter->>System: Открыть карточку кандидата и выбрать вакансию
    System->>System: Извлечь текст резюме
    System->>System: Структурировать данные резюме (опыт, навыки, образование)
    System->>System: Выделить ключевые требования вакансии
    System->>Model: Передать данные резюме и требования вакансии
    Model-->>System: Вернуть оценку соответствия, совпадения и пробелы
    System->>System: Сохранить результат в карточке кандидата
    System-->>Recruiter: Показать оценку, совпадения, пробелы и рекомендацию
```

## Диаграмма классов

```mermaid
classDiagram
    class Recruiter {
        +int id
        +string name
        +string email
    }

    class Candidate {
        +int id
        +string name
        +string email
        +string resumeFile
    }

    class Vacancy {
        +int id
        +string title
        +string requirements
    }

    class AnalysisResult {
        +int id
        +float matchScore
        +string[] matches
        +string[] gaps
        +string recommendation
        +datetime createdAt
    }

    Recruiter "1" --> "*" Candidate : управляет
    Recruiter "1" --> "*" Vacancy : создаёт
    Candidate "1" --> "*" AnalysisResult : имеет
    Vacancy "1" --> "*" AnalysisResult : по вакансии
```