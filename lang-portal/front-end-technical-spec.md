# Front end Technical Specification

## Pages

### **Dashboard `/dashboard`**
#### Purpose
The purpose of this page is to provide a summary of learning and act as the default page when a user visits the web-app.

#### Components
---
- **Last Study Session**
    - Shows last activities used.
    - Shows when last activity was used.
    - Summarizes wrong vs correct from last activity.
    - Has a link to the group.

- **Study Progress**
    - Total words studied (e.g., 3/134).
        - Across all study sessions, shows the total words studied out of all possible words in our database.

    - Display a mastery progress bar (e.g., 75% mastered).

- **Quick Stats**
    - Success rate (e.g., 85% correct)
    - Total study sessions (e.g., 5 sessions)
    - Total active groups (e.g., 2 groups)
    - Study streak (e.g., 3 days)
    - Total study time (e.g., 2 hours)

- **Start Studying**
    - Goes to the study activities page.


#### **Needed API Endpoints**

- `GET /api/dashboard/last-study-session`
- `GET /api/dashboard/study-progress`
- `GET /api/dashboard/quick-stats`
---
### **Study Activities Index`/study-activities`**

#### Purpose
The purpose of this page is to show a collection of study activities with a thumbnail , title , to either launch or view the study activity.

#### Components
---
- Study Activity Card
    - Show a Thumbnail of the study activity.
    - Title of the study activity.
    - A Launch button to take us to the launch page.
    - A View button to view more information about past study sessions for the study activity.

#### **Needed API Endpoints**
- `GET /api/study-activities`


### **Study Activity Show `/study_activities/:id`**

#### Purpose
The purpose of this page is to show more information about a specific study activity, including past study sessions.

#### Components
---
- Title of the study activity.
- Thumbnail of the study activity.
- Description of the study activity.
- Launch button
- Study activities Paginated list
    - id 
    - activity name
    - group name
    - start time
    - end time (inferred by the last word review item submitted)
    - number of review items

#### **Needed API Endpoints**
- `GET /api/study_activities/:id`
- `GET /api/study_activities/:id/study_sessions`

---
### **Study Activity Launch `/study_activities/:id/launch`**
#### Purpose
The purpose of this page is to launch a study activity

#### Components
---
- Title of the study activity.
- Launch form 
    - Select field for groups
    - Launch now button

#### Behavior 
After the submission a new tab opens with the study activity based on its URL provided by the database.

Also after the form is submitted the page will redirect to the study session show page. 

#### **Needed API Endpoints**
- `POST /api/study_activities/:id/launch`

---
### **Words Index `/words`**
#### Purpose
The purpose of this page is to show all words in our database.

#### Components
---
- Paginated word list
    - Columns:
        - Word (japanese)
        - Romaji
        - English
        - Correct count
        - Wrong count
    - Pagination with 100 item per page.
    - Clicking the japanese word takes you to the word show page.

#### **Needed API Endpoints**
- `GET /api/words`

---

### **Word Show `/words/:id`**

#### Purpose
The purpose of this page is to show more information about a specific word.

#### Components
---
- Word (japanese)
- Romaji
- English
- Study Statistics
    - Correct count
    - Wrong count
- Word Groups 
    - Show an a series of pills for (e.g. tags)
    - When group name is clicked it takes you to the group show page.

#### **Needed API Endpoints**
- `GET /api/words/:id`

---
### **Word Groups Index `/groups`**
#### Purpose
The purpose of this page is to show a list of groups in our database.

#### Components
---
- Paginated Group List
    - Columns
        - Group Name
        - Word Count
    - Clicking the group name will take us to the group show page.

#### **Needed API Endpoints**
- `GET /api/words/groups`

### **Group Show `/groups/:id`**
#### Purpose
The Purpose of this page is to show more information about a specific group.

#### Components
---
- Group Name
- Group statistics
    - Total Word count
- Words in Group (Paginated list of words)
    - Should use the same component as the words index page.
- Study sessions (PAginated list of study sessions)
    - Should use the same component as the study session index page.

#### **Needed API Endpoints**
- `GET /api/groups/:id`
- `GET /api/groups/:id/words`
- `GET /api/groups/:id/study_sessions`


### Study Sessions Index `/study_sessions`

#### Purpose
The purpose of this page is to show a list of study sessions in our database.

#### Components
---
- Paginated Study Session List
    - Columns
        - ID 
        - Activity Name
        - Group Name
        - Start Time
        - End Time 
        - Number of review items
    - Clicking the ID will take us to the study session show page.


#### **Needed API Endpoints**
- `GET /api/study_sessions`


---
### Study Session Show `/study_sessions/:id`
#### Purpose
The purpose of this page is to show more information about a specific study session.
#### Components
---
- Study Session details
    - Activity Name
    - Group Name
    - Start Time
    - End Time 
    - Number of review items
- Word Review Items 
    - Should use the same component as the words index page.

#### **Needed API Endpoints**
- `GET /api/study_sessions/:id`
- `GET /api/study_sessions/:id/words`

---


### Settings page `/settings`
#### Purpose
The purpose of this page is to make configuration to the study portal.
#### Components
---
- Theme Selector (light , dark , system)
- Reset History 
    - This will delete all study sessions and word review items.
- Full Reset Button
    - This will drop all tables and re-create them with seed data.


#### **Needed API Endpoints**
- `POST /api/settings/reset-history`
- `POST /api/settings/full-reset`





---
#### Purpose
#### Components
#### **Needed API Endpoints**


















