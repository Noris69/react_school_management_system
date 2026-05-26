# **Ynov School Manager**

A **React-based school and university management system** designed to manage academic users, staff, students, courses, notes, attendance, schedules, and internal academic operations.

The project provides a frontend interface connected to a remote backend API. It supports separate authentication flows for **staff** and **students**, and includes dashboard pages for academic management.

---

# **Project Purpose**

The purpose of this project is to provide a modern web interface for managing university or school data.

The application allows users to access academic services based on their profile type:

- **Staff**
- **Student**

It can be used as a foundation for:

- **School management systems**
- **University management platforms**
- **Student portals**
- **Staff dashboards**
- **Attendance management systems**
- **Course and paper management**
- **Notes and academic content platforms**
- **React frontend portfolio projects**

---

# **Technologies Used**

## **Frontend**

- **React 18**
- **JavaScript**
- **React Router DOM**
- **Axios**
- **React Icons**
- **React Toastify**
- **React Scripts**

## **Styling & Formatting**

- **Tailwind CSS**
- **Prettier**
- **Prettier Tailwind Plugin**

## **API Communication**

- **Axios**
- **Remote REST API**

---

# **Main Features**

## **Authentication**

The application provides login for two user types:

- **Staff**
- **Student**

The selected user type is used to call the correct backend login endpoint.

Example:

```text
/auth/login/staff
/auth/login/student
```

After login, user details are stored locally and used across the dashboard.

---

## **Registration**

The application includes separate registration pages for:

- **Staff registration**
- **Student registration**

Routes:

```text
/register/reg_staff
/register/reg_student
```

---

## **Dashboard**

After login, users are redirected to the dashboard.

The dashboard provides access to academic management features such as:

- **Papers**
- **Notes**
- **Students list**
- **Attendance**
- **Internal section**
- **Time schedule**
- **Profile**
- **Staff approval**
- **Add paper**
- **Join paper**

---

## **Paper Management**

The app includes paper/course-related features:

- **View papers**
- **Open paper details**
- **View notes linked to a paper**
- **Add notes to a paper**
- **Edit notes**
- **View students linked to a paper**
- **Add a new paper**
- **Join an existing paper**

---

## **Notes Management**

The notes module allows users to:

- **View notes**
- **Add notes**
- **Edit notes**
- **Attach notes to a specific paper**

---

## **Student Management**

The application includes a students list page where users can view students linked to academic papers or modules.

---

## **Attendance Management**

The application includes an attendance layout dedicated to attendance-related operations.

---

## **Staff Approval**

The app contains a lazy-loaded staff approval page.

This can be used by administrators or authorized staff to approve new staff accounts.

---

## **Profile Page**

Users can access a profile page to view or manage their personal information.

---

## **Notifications**

The app uses **React Toastify** to display toast notifications.

---

# **Application Routes**

| Route | Description |
|---|---|
| **/** | Login page |
| **/register/reg_staff** | Staff registration |
| **/register/reg_student** | Student registration |
| **/dash** | Main dashboard |
| **/dash/paper** | Paper list |
| **/dash/paper/:paper** | Notes linked to a paper |
| **/dash/paper/:paper/add** | Add note |
| **/dash/paper/:paper/:note/edit** | Edit note |
| **/dash/paper/:paper/students** | Students list for a paper |
| **/dash/attendance** | Attendance section |
| **/dash/internal** | Internal section |
| **/dash/time_schedule** | Time schedule |
| **/dash/profile** | User profile |
| **/dash/approve_staff** | Staff approval |
| **/dash/add_paper** | Add paper |
| **/dash/join_paper** | Join paper |

---

# **Project Structure**

```bash
react_school_management_system/
├── public/
│
├── src/
│   ├── Components/
│   │   ├── Forms/
│   │   │   ├── Login.js
│   │   │   ├── StaffForm.js
│   │   │   ├── StudentForm.js
│   │   │   ├── NotesForm.js
│   │   │   ├── TimeScheduleForm.js
│   │   │   ├── PaperForm.js
│   │   │   └── JoinPaper.js
│   │   │
│   │   ├── Layouts/
│   │   │   ├── AppLayout.js
│   │   │   ├── Layout.js
│   │   │   ├── Dash.js
│   │   │   ├── AttendanceLayout.js
│   │   │   ├── InternalLayout.js
│   │   │   ├── RegisterLayout.js
│   │   │   ├── Loading.js
│   │   │   └── ErrorElement.js
│   │   │
│   │   └── Queries/
│   │       ├── Paper.js
│   │       ├── Notes.js
│   │       ├── StudentsList.js
│   │       ├── Profile.js
│   │       └── StaffApproval.js
│   │
│   ├── Hooks/
│   │   └── UserContext.js
│   │
│   ├── config/
│   │   └── api/
│   │       └── axios.js
│   │
│   ├── App.js
│   └── index.js
│
├── package.json
└── README.md
```

---

# **API Configuration**

The app uses Axios with the following base URL:

```text
https://kollege-api.onrender.com
```

Recommended improvement:

Create an environment variable:

```env
REACT_APP_API_BASE_URL=https://kollege-api.onrender.com
```

Then update Axios configuration:

```js
import axios from "axios";

export default axios.create({
  baseURL: process.env.REACT_APP_API_BASE_URL,
  headers: { "Content-Type": "application/json" },
});
```

---

# **Installation**

## **1. Clone the Repository**

```bash
git clone https://github.com/Noris69/react_school_management_system.git
cd react_school_management_system
```

---

## **2. Install Dependencies**

```bash
npm install
```

---

## **3. Create Environment Variables**

Create a `.env` file:

```env
REACT_APP_API_BASE_URL=https://kollege-api.onrender.com
```

---

## **4. Run the Application**

```bash
npm start
```

The application will run on:

```bash
http://localhost:3000
```

---

# **Useful Commands**

## **Start Development Server**

```bash
npm start
```

## **Build for Production**

```bash
npm run build
```

## **Run Tests**

```bash
npm test
```

## **Format Code**

```bash
npm run prettier
```

## **Run Tailwind Watch**

```bash
npm run tailwind
```

---

# **Login Flow**

## **1. Select User Type**

The user chooses:

```text
Staff
```

or:

```text
Student
```

---

## **2. Enter Credentials**

The user enters:

- **Username**
- **Password**

---

## **3. API Login Request**

The app sends:

```http
POST /auth/login/{userType}
Content-Type: application/json
```

Example body:

```json
{
  "username": "student01",
  "password": "password123"
}
```

---

## **4. Store User Details**

After login, the response is saved in:

```text
localStorage
```

under:

```text
userDetails
```

---

## **5. Redirect to Dashboard**

The user is redirected to:

```text
/dash
```

---

# **Git Ignore Recommendations**

```gitignore
node_modules/
build/
dist/
.env
.env.local
*.log
.DS_Store
.vscode/
.idea/
```

---

# **Security Recommendations**

- **Do not hardcode API URLs**
- **Use environment variables**
- **Avoid storing sensitive tokens directly in localStorage**
- **Add token expiration handling**
- **Add protected route guards**
- **Validate user roles on the backend**
- **Use HTTPS in production**
- **Add logout token cleanup**
- **Handle API errors properly**
- **Avoid exposing backend implementation details**

---


# **Author**

Developed by **Noris69**.
