# 🎓 Internship Management System (Java 21, JDBC, MySQL, Servlets, JSP)

An enterprise-grade Internship Management web application built strictly with **Java 21**, **JDBC**, **MySQL**, **Servlets**, and **JSP** (No Spring Boot, No Hibernate).

---

## 📂 Project Structure Overview

```text
intern management/
├── pom.xml                                   # Maven configuration (Java 21, Jakarta Servlet 6.0, MySQL Connector)
├── database.sql                              # Complete MySQL database creation & seed data script
├── README.md                                 # Setup and beginner execution guide
└── src/
    └── main/
        ├── java/com/internship/
        │   ├── dao/
        │   │   ├── DBConnection.java         # JDBC Connection Manager (PreparedStatement, root/YOUR_PASSWORD)
        │   │   ├── AdminDAO.java             # Admin metrics & authentication
        │   │   ├── StudentDAO.java           # Student registration & CRUD
        │   │   ├── CompanyDAO.java           # Company management
        │   │   ├── InternshipDAO.java        # Internship posting, search & filtering
        │   │   ├── ApplicationDAO.java       # Student application submissions & review
        │   │   └── CompletionDAO.java        # Completion tracking, ratings & certificate codes
        │   ├── model/
        │   │   ├── Admin.java
        │   │   ├── Student.java
        │   │   ├── Company.java
        │   │   ├── Internship.java
        │   │   ├── Application.java
        │   │   └── InternshipCompletion.java
        │   └── servlet/
        │       ├── LoginServlet.java         # Handles /login for Students and Admins
        │       ├── LogoutServlet.java        # Handles /logout
        │       ├── RegisterServlet.java      # Handles /register for Students
        │       ├── StudentDashboardServlet.java # Handles /student/dashboard
        │       ├── AdminDashboardServlet.java   # Handles /admin/dashboard
        │       ├── CompanyServlet.java       # Handles /companies and /admin/companies
        │       ├── InternshipServlet.java    # Handles /internships and /admin/internships
        │       ├── ApplicationServlet.java   # Handles /applications and /admin/applications
        │       ├── SelectionServlet.java     # Handles /admin/selection (Approve / Reject)
        │       └── CompletionServlet.java    # Handles /completion and /admin/completion
        └── webapp/
            ├── WEB-INF/
            │   └── web.xml                   # Jakarta EE 6.0 deployment descriptor
            ├── css/
            │   └── style.css                 # Modern responsive CSS design
            ├── js/
            │   └── app.js                    # Modal controls and interactive helpers
            ├── index.jsp                     # Portal landing page
            ├── login.jsp                     # Student & Admin sign-in page
            ├── register.jsp                  # Student registration page
            ├── student-dashboard.jsp         # Student dashboard (Status, Offers, Openings)
            ├── admin-dashboard.jsp           # Admin dashboard (KPIs, Reports, Students)
            ├── companies.jsp                 # Partner company directory & management
            ├── internships.jsp               # Internship listings, search & apply modal
            ├── applications.jsp              # Applications tracking & recruiter remarks
            ├── selection.jsp                 # Candidate selection & rejection center
            └── completion-tracking.jsp       # Completion milestones, ratings & certificates
```

---

## ⚡ Quick Start Guide (Step-by-Step for Beginners)

### Step 1: Run the MySQL Database Script

Open **MySQL Workbench** OR **MySQL 8.0 Command Line Client**:

Run the following command in your MySQL terminal:
```sql
source c:/Users/veera/OneDrive/Desktop/intern management/database.sql;
```
*(Or open `database.sql` in MySQL Workbench and click the lightning bolt ⚡ execute button).*

This creates the database `internship_management` and sets up all tables with demo data.

---

### Step 2: Configure Your MySQL Password

Open this file:
[`src/main/java/com/internship/dao/DBConnection.java`](file:///c:/Users/veera/OneDrive/Desktop/intern%20management/src/main/java/com/internship/dao/DBConnection.java#L24-L25)

Find line 24 & 25:
```java
private static final String USERNAME = "root";
private static final String PASSWORD = "YOUR_PASSWORD";
```
Replace `"YOUR_PASSWORD"` with your actual MySQL `root` password (e.g., `"root"`, `"admin"`, or `""` if blank).

---

### Step 3: Run the Project on Apache Tomcat

You can run this project in **Eclipse**, **IntelliJ IDEA**, **NetBeans**, **VS Code**, or via **Tomcat standalone**:

#### Option A: Using Eclipse IDE for Enterprise Java (Recommended for College/Labs)
1. Open Eclipse -> **File** -> **Import...** -> **Existing Maven Projects**.
2. Browse to `c:\Users\veera\OneDrive\Desktop\intern management` and click **Finish**.
3. In the **Servers** tab, click **New Server** -> select **Apache Tomcat v10.1** (or Tomcat 10+).
4. Right-click the `internship-management` project -> **Run As** -> **Run on Server**.

#### Option B: Using IntelliJ IDEA Ultimate
1. Open IntelliJ -> **Open** -> select `c:\Users\veera\OneDrive\Desktop\intern management`.
2. Click **Run** -> **Edit Configurations** -> **+** -> **Tomcat Server** -> **Local**.
3. In the **Deployment** tab, click **+** -> **Artifact** -> select `internship-management:war exploded`.
4. Click **Run / Debug**.

#### Option C: Using Command Line & Tomcat `webapps/`
If you have Maven and Tomcat installed:
```powershell
mvn clean package
```
Copy `target/internship-management.war` into your Tomcat `webapps/` folder, then start Tomcat:
```powershell
<TOMCAT_DIR>\bin\startup.bat
```

---

### Step 4: Open in Your Web Browser

Navigate to:
```text
http://localhost:8080/internship-management/
```
*(Or `http://localhost:8080/` depending on your server context path).*

---

## 🔑 Default Login Credentials

### 🛡️ Administrator Account
* **Username:** `admin`
* **Password:** `admin123`

### 👨‍🎓 Sample Student Account
* **Email:** `alex@example.com`
* **Password:** `student123`
*(Or click **Student Sign Up** to create your own account)*
