# Enterprise Employee Management System (EMS)

A comprehensive, full-stack **Employee Management System** built with **Java 17, Spring Boot, HTML5, CSS3, and JavaScript**.

---

##  Key Features

###  Administrator Portal (`admin.html`)
- **Executive Dashboard**: KPI metrics for Total Employees, Pending Leaves, Pending Wants, and Total Disbursed Payroll.
- **Employee Directory & CRUD**:
  - View all staff records with search by name/title and filtering by department.
  - Add new employees with credentials, base salary, working days, and performance score.
  - Update employee details (department, designation, salary, attendance, performance rating, status).
  - Delete or deactivate employees.
- **Leave Approvals Management**:
  - Filter leaves by *Pending*, *Approved*, or *Rejected*.
  - Review leave applications with reason, date range, and duration.
  - Approve or Reject with optional administrator comments.
- **Performance & Attendance-Based Salary Engine**:
  - Real-time interactive payroll calculator:
    - Select employee (auto-fills base salary, working days, and rating).
    - Configurable **Standard Working Days** (default 22) vs **Actual Days Worked**.
    - Performance rating slider ($1.0$ to $5.0$) with dynamic incentive multipliers ($+5\%$ to $+20\%$).
    - Real-time calculation: Prorated attendance earnings, missed days deductions, performance bonus, and final Net Payout.
  - **Release Salary**: Disburse and save official monthly payroll records.
  - **Corporate Payslip Generator**: Printable, formatted employee salary statement.
- **Employee Wants & Operational Necessities**:
  - View equipment, software license, training sponsorship, and office comfort requests from employees.
  - Respond with decisions (*In Review*, *Approved*, *Resolved*, *Rejected*) and administrator procurement notes.

---

### Employee Portal (`employee.html`)
- **Employee Overview**:
  - Personalized welcome banner with department, designation, and contract salary.
  - Personal KPI widgets: Working days attendance, performance score, approved leave count, and active requests.
- **Apply for Leave**:
  - Leave application form with automatic day duration calculator.
  - Leave types: *Casual Leave*, *Medical / Sick Leave*, *Annual Vacation*, *Emergency Leave*, *Compensatory Off*.
  - Real-time status tracking with administrator feedback comments.
- **Submit Employee Wants & Necessities for Administrator**:
  - Submit operational requests directly to executive administration.
  - Categories: *Work Equipment & Hardware*, *Software & Tools*, *Training & Learning*, *Office Space & Comfort*, *Career & Role*.
  - Priority levels (*Low*, *Medium*, *High*, *Urgent*) and business justifications.
  - Live tracking of administrator responses and procurement actions.
- **My Salary & Payslips**:
  - Historical view of all released monthly salaries.
  - View and print detailed corporate salary slips showing earnings, deductions, and performance incentives.

---

## Default Demo Accounts

| Role | Username | Password | Full Name / Description |
| :--- | :--- | :--- | :--- |
| **Administrator** | `admin` | `admin123` | Alex Mercer (Admin & Executive Management) |
| **Employee** | `john.doe` | `password123` | John Doe (Senior Full Stack Engineer) |
| **Employee** | `sarah.smith` | `password123` | Sarah Smith (Lead UI/UX Designer) |
| **Employee** | `michael.scott` | `password123` | Michael Scott (Sales Operations Specialist) |
| **Employee** | `emily.davis` | `password123` | Emily Davis (Talent Acquisition Lead) |
| **Employee** | `robert.j` | `password123` | Robert Johnson (Cloud Infrastructure Specialist) |

*(The login page features 1-click quick-fill buttons for immediate demo access)*

---

## Technology Stack

- **Backend**:
  - Java 17
  - Spring Boot 4
  - Spring Data JPA / Hibernate
  - Embedded H2 Database (with H2 Web Console at `/h2-console`)
  - RESTful API Architecture
- **Frontend**:
  - HTML5 (Semantic, responsive markup)
  - Modern CSS3 (CSS Variables, Flexbox/Grid, Print Stylesheet `@media print`)
  - Vanilla JavaScript (Async/Await Fetch API, modular client)
- **Build Tool**:
  - Apache Maven Wrapper (`mvnw` / `mvnw.cmd`)

---

## 🚀 Running the Project

### Option 1: Run Pre-built Executable JAR
```bash
java -jar target/employee-management-system-1.0.0.jar
```

### Option 2: Run via Maven Wrapper
```bash
# On Windows
.\mvnw.cmd spring-boot:run

# On Linux / macOS
./mvnw spring-boot:run
```

Once started, open your web browser at:
 **`http://localhost:8080/index.html`**

To access the H2 in-memory database console:
 **`http://localhost:8080/h2-console`**
- JDBC URL: `jdbc:h2:mem:emsdb`
- User: `sa`
- Password: *(blank)*

---

## Project Structure

```
Employee Management System/
├── pom.xml
├── mvnw / mvnw.cmd
├── src/
│   ├── main/
│   │   ├── java/com/ems/
│   │   │   ├── EmployeeManagementApplication.java
│   │   │   ├── config/
│   │   │   │   └── DataInitializer.java        # Seeds initial data
│   │   │   ├── controller/
│   │   │   │   ├── AuthController.java
│   │   │   │   ├── EmployeeController.java
│   │   │   │   ├── LeaveController.java
│   │   │   │   ├── EmployeeWantController.java
│   │   │   │   ├── SalaryController.java
│   │   │   │   └── DashboardController.java
│   │   │   ├── dto/                            # Data Transfer Objects
│   │   │   ├── model/                          # JPA Entities (User, LeaveRequest, EmployeeWant, SalaryRecord)
│   │   │   ├── repository/                     # Spring Data JPA Repositories
│   │   │   └── service/                        # Business Logic Services
│   │   └── resources/
│   │       ├── application.properties
│   │       └── static/                         # Frontend Web Assets
│   │           ├── index.html                  # Unified Login Page with 1-click Demo buttons
│   │           ├── admin.html                  # Administrator Portal & Management
│   │           ├── employee.html               # Employee Portal & Self-Service
│   │           ├── css/style.css               # Modern Responsive Stylesheet
│   │           └── js/
│   │               ├── api.js                  # REST API Client & Utilities
│   │               ├── admin.js                # Administrator Dashboard Controller
│   │               └── employee.js             # Employee Portal Controller
└── README.md
```
