# Backend Server Technical Specs

## Business Goal: 
A language learning school wants to build a prototype of learning portal which will act as three things:
- Inventory of possible vocabulary that can be learned
- Act as a  Learning record store (LRS), providing correct and wrong score on practice vocabulary
- A unified launchpad to launch different learning apps

## Technical Requirements

- The Backend will be built using GO
- The database will be SQLite3
- The API will be built using Gin
- The API will always return JSON
- There will be no authentication or authorization
- Everything will be treated as a single user





## Database

We have the following table
- words - store vocabulary words
  - id integer
  - Japanese String
  - romaji String
  - English String
  - Parts JSON


- words_groups join table for many to many relationship between words and groups
  - id integer
  - word_id integer
  - group_id integer
  

- groups - themtic groups of words
  - id integer
  - group_id integer


- study_sessions - record of a study session grouping word review items
  - id integer
  - study_session_id integer
  - group_id integer
  - correct boolean
  - created_at datetime


- study_activities - a specific study activity , linking a study session to group
  - id integer
  - study_session_id integer
  - group_id integer
  - activity_type string
  - created_at datetime


- word_reviews_items - a record of word practice, whether correct or wrong
  - id integer
  - study_session_id integer
  - word_id integer
  - correct boolean
  - created_at datetime


## API Endpoints

### - `GET /api/dashboard/last-study-session`
Response example:
``` 
json
{
  "id": 5,
  "group_id": 2,
  "last_used": "2025-10-13T18:45:00Z",
  "study_activity_id": 1,
  "group_id":789,
  "group_name": "JLPT N5",
} 
```

- `GET /api/dashboard/study-progress`
- `GET /api/dashboard/quick-stats`

- `GET /api/study_activities/:id`
- `GET /api/study_activities/:id/study_sessions`

- `POST /api/study_activities/:id/launch`
  - requires params: group_id , study_activity_id

- `GET /api/words`
- `GET /api/words/:id`


- `GET /api/groups`
- `GET /api/groups/:id`
- `GET /api/groups/:id/words`
- `GET /api/groups/:id/study_sessions`

- `GET /api/study_sessions`
- `GET /api/study_sessions/:id/words`

- `POST /api/settings/reset-history`
- `POST /api/settings/full-reset`




- 
  specific group


















