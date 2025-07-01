---
{"dg-publish":true,"permalink":"/1-project/01-thuc-tap/java-intern-fundamentals-tuan-1/","title":"JAVA-INTERN-FUNDAMENTALS-tuần-1","tags":["research","lecture_notes","tutorial","explanatory_article"],"created":"2025-07-01T15:08:42.541+07:00"}
---

# Bài 1

## Yêu cầu: 
**Bài số 1**: Cài đặt Hệ quản trị cơ sở dữ liệu MySQL. Tạo 1 lược đồ ERD trong đó có 1 bảng mô tả đối tượng Sinh viên. Các thuộc tính của sinh viên gồm có: Mã sinh viên, Tên sinh viên, Địa chỉ cư trú, Điểm tổng kết.   

Thực hiện viết các API Restful Web Service cho phép:   

a.     Thêm 1 đối tượng sinh viên   

b.     Cập nhật thông tin sinh viên (các thông tin cập nhật bao gồm tất cả các thông tin ngoại trừ Mã sinh viên)   

c.     Xóa 1 sinh viên khỏi cơ sở dữ liệu   

d.     Tra cứu thông tin sinh viên theo các tiêu chí: mã sinh viên, tên sinh viên   

e.     Lấy top 3 sinh viên có Điểm tổng kết **_cao nhất_**.


## Tìm hiểu
(chat Grok)
I’ll guide you step-by-step through installing MySQL, creating an ERD, and implementing RESTful Web Service APIs for the student management system as requested. The solution will use MySQL for the database, Java with Spring Boot for the APIs, and include detailed steps for setup and implementation.

---

### Step 1: Install MySQL
MySQL is a popular open-source relational database management system. Follow these steps to install and set it up:

1. **Download MySQL**:
   - Visit the official MySQL website: [https://dev.mysql.com/downloads/](https://dev.mysql.com/downloads/).
   - Choose **MySQL Community Server** for your operating system (Windows, macOS, or Linux).
   - Download the installer (e.g., MySQL Installer for Windows or `.dmg` for macOS).

2. **Install MySQL**:
   - **Windows**:
     - Run the MySQL Installer.
     - Select **Developer Default** or **Custom** setup type to include MySQL Server and MySQL Workbench.
     - Follow the wizard to install MySQL Server, MySQL Workbench, and connectors.
     - During installation, set a **root password** and optionally create additional users.
   - **macOS**:
     - Open the `.dmg` file and follow the installer prompts.
     - Set the root password when prompted.
   - **Linux** (e.g., Ubuntu):
     ```bash
     sudo apt update
     sudo apt install mysql-server
     sudo mysql_secure_installation
     ```
     Follow prompts to set the root password and secure the installation.

3. **Verify Installation**:
   - Open a terminal or command prompt and run:
     ```bash
     mysql -u root -p
     ```
   - Enter the root password. If you see the MySQL prompt (`mysql>`), the installation is successful.

4. **Install MySQL Workbench** (optional but recommended):
   - Download MySQL Workbench from the same MySQL website.
   - Use it for visual database design and management.

---

### Step 2: Create the ERD (Entity-Relationship Diagram)
The ERD describes the **Student** entity with the specified attributes: Student ID, Name, Address, and GPA.

1. **Design the ERD**:
   - **Entity**: Student
   - **Attributes**:
     - `student_id` (Primary Key, e.g., VARCHAR(10))
     - `name` (VARCHAR(100))
     - `address` (VARCHAR(255))
     - `gpa` (FLOAT or DECIMAL(4,2) for two decimal places, e.g., 8.75)
   - **ERD Representation** (conceptual):
     ```
     [Student]
     +-------------+
     | student_id  | (PK)
     | name        |
     | address     |
     | gpa         |
     +-------------+
     ```

2. **Create the Database and Table in MySQL**:
   - Log into MySQL:
     ```bash
     mysql -u root -p
     ```
   - Create a database:
     ```sql
     CREATE DATABASE student_db;
     USE student_db;
     ```
   - Create the `students` table:
     ```sql
     CREATE TABLE students (
         student_id VARCHAR(10) PRIMARY KEY,
         name VARCHAR(100) NOT NULL,
         address VARCHAR(255),
         gpa DECIMAL(4,2) CHECK (gpa >= 0 AND gpa <= 10)
     );
     ```

3. **Visualize ERD Using MySQL Workbench**:
   - Open MySQL Workbench.
   - Go to **Database > Reverse Engineer** to connect to `student_db` and generate the ERD.
   - Alternatively, create a new ERD:
     - Go to **File > New Model**.
     - Add a table named `students` with the above attributes.
     - Save the ERD as a `.mwb` file for documentation.

---

### Step 3: Set Up the Development Environment for RESTful APIs
We’ll use **Spring Boot** (Java) to create RESTful APIs, as it’s widely used and simplifies development.

1. **Install Java Development Kit (JDK)**:
   - Download and install JDK 17 or later from [https://www.oracle.com/java/](https://www.oracle.com/java/).
   - Verify installation:
     ```bash
     java -version
     ```

2. **Install an IDE**:
   - Use **IntelliJ IDEA**, **Eclipse**, or **VS Code** with Java extensions.
   - IntelliJ IDEA Community Edition is recommended for Spring Boot.

3. **Set Up Maven or Gradle**:
   - We’ll use **Maven** for dependency management.
   - Create a new Spring Boot project using **Spring Initializr**:
     - Visit [https://start.spring.io/](https://start.spring.io/).
     - Set:
       - Project: Maven
       - Language: Java
       - Spring Boot: Latest stable version (e.g., 3.2.x)
       - Dependencies: **Spring Web**, **Spring Data JPA**, **MySQL Driver**
     - Generate and download the project.
     - Import the project into your IDE.

4. **Configure MySQL Connection**:
   - Open `src/main/resources/application.properties` in your Spring Boot project.
   - Add:
     ```properties
     spring.datasource.url=jdbc:mysql://localhost:3306/student_db
     spring.datasource.username=root
     spring.datasource.password=your_root_password
     spring.jpa.hibernate.ddl-auto=update
     spring.jpa.show-sql=true
     ```

---

### Step 4: Implement RESTful APIs
We’ll create a Spring Boot application with RESTful APIs for the specified operations.

#### 4.1. Create the Entity Class
Create a `Student` entity to map to the `students` table.

```java
// src/main/java/com/example/demo/model/Student.java
package com.example.demo.model;

import jakarta.persistence.Entity;
import jakarta.persistence.Id;
import jakarta.persistence.Table;

@Entity
@Table(name = "students")
public class Student {
    @Id
    private String studentId;
    private String name;
    private String address;
    private float gpa;

    // Getters and setters
    public String getStudentId() { return studentId; }
    public void setStudentId(String studentId) { this.studentId = studentId; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public String getAddress() { return address; }
    public void setAddress(String address) { this.address = address; }
    public float getGpa() { return gpa; }
    public void setGpa(float gpa) { this.gpa = gpa; }
}
```

#### 4.2. Create the Repository
Create a repository interface for database operations.

```java
// src/main/java/com/example/demo/repository/StudentRepository.java
package com.example.demo.repository;

import com.example.demo.model.Student;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;

import java.util.List;

public interface StudentRepository extends JpaRepository<Student, String> {
    List<Student> findByNameContainingIgnoreCase(String name);
    @Query("SELECT s FROM Student s ORDER BY s.gpa DESC")
    List<Student> findTop3ByOrderByGpaDesc();
}
```

#### 4.3. Create the Service
Create a service to handle business logic.

```java
// src/main/java/com/example/demo/service/StudentService.java
package com.example.demo.service;

import com.example.demo.model.Student;
import com.example.demo.repository.StudentRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;
import java.util.Optional;

@Service
public class StudentService {
    @Autowired
    private StudentRepository studentRepository;

    // a. Add a student
    public Student addStudent(Student student) {
        return studentRepository.save(student);
    }

    // b. Update a student
    public Student updateStudent(String studentId, Student updatedStudent) {
        Optional<Student> existingStudent = studentRepository.findById(studentId);
        if (existingStudent.isPresent()) {
            Student student = existingStudent.get();
            student.setName(updatedStudent.getName());
            student.setAddress(updatedStudent.getAddress());
            student.setGpa(updatedStudent.getGpa());
            return studentRepository.save(student);
        }
        throw new RuntimeException("Student not found");
    }

    // c. Delete a student
    public void deleteStudent(String studentId) {
        if (studentRepository.existsById(studentId)) {
            studentRepository.deleteById(studentId);
        } else {
            throw new RuntimeException("Student not found");
        }
    }

    // d. Find by student ID
    public Student findByStudentId(String studentId) {
        return studentRepository.findById(studentId)
                .orElseThrow(() -> new RuntimeException("Student not found"));
    }

    // d. Find by name
    public List<Student> findByName(String name) {
        return studentRepository.findByNameContainingIgnoreCase(name);
    }

    // e. Get top 3 students by GPA
    public List<Student> getTop3ByGpa() {
        return studentRepository.findTop3ByOrderByGpaDesc();
    }
}
```

#### 4.4. Create the Controller
Create a REST controller to expose the APIs.

```java
// src/main/java/com/example/demo/controller/StudentController.java
package com.example.demo.controller;

import com.example.demo.model.Student;
import com.example.demo.service.StudentService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/students")
public class StudentController {
    @Autowired
    private StudentService studentService;

    // a. Add a student
    @PostMapping
    public ResponseEntity<Student> addStudent(@RequestBody Student student) {
        return ResponseEntity.ok(studentService.addStudent(student));
    }

    // b. Update a student
    @PutMapping("/{studentId}")
    public ResponseEntity<Student> updateStudent(@PathVariable String studentId, @RequestBody Student student) {
        return ResponseEntity.ok(studentService.updateStudent(studentId, student));
    }

    // c. Delete a student
    @DeleteMapping("/{studentId}")
    public ResponseEntity<Void> deleteStudent(@PathVariable String studentId) {
        studentService.deleteStudent(studentId);
        return ResponseEntity.noContent().build();
    }

    // d. Find by student ID
    @GetMapping("/{studentId}")
    public ResponseEntity<Student> getStudentById(@PathVariable String studentId) {
        return ResponseEntity.ok(studentService.findByStudentId(studentId));
    }

    // d. Find by name
    @GetMapping("/search")
    public ResponseEntity<List<Student>> getStudentsByName(@RequestParam String name) {
        return ResponseEntity.ok(studentService.findByName(name));
    }

    // e. Get top 3 students by GPA
    @GetMapping("/top3")
    public ResponseEntity<List<Student>> getTop3StudentsByGpa() {
        return ResponseEntity.ok(studentService.getTop3ByGpa());
    }
}
```

#### 4.5. Run the Application
- Start the Spring Boot application:
  - In your IDE, run the main class (e.g., `DemoApplication.java`).
  - Or use the terminal:
    ```bash
    mvn spring-boot:run
    ```
- The application will run on `http://localhost:8080`.

---

### Step 5: Test the APIs
Use a tool like **Postman** or **curl** to test the APIs.

1. **Add a Student (POST /api/students)**:
   ```json
   {
       "studentId": "SV001",
       "name": "Nguyen Van A",
       "address": "123 Hanoi",
       "gpa": 8.5
   }
   ```
   Endpoint: `http://localhost:8080/api/students`
   Method: POST

2. **Update a Student (PUT /api/students/SV001)**:
   ```json
   {
       "name": "Nguyen Van B",
       "address": "456 Hanoi",
       "gpa": 9.0
   }
   ```
   Endpoint: `http://localhost:8080/api/students/SV001`
   Method: PUT

3. **Delete a Student (DELETE /api/students/SV001)**:
   Endpoint: `http://localhost:8080/api/students/SV001`
   Method: DELETE

4. **Find by Student ID (GET /api/students/SV001)**:
   Endpoint: `http://localhost:8080/api/students/SV001`
   Method: GET

5. **Find by Name (GET /api/students/search?name=Nguyen)**:
   Endpoint: `http://localhost:8080/api/students/search?name=Nguyen`
   Method: GET

6. **Get Top 3 by GPA (GET /api/students/top3)**:
   Endpoint: `http://localhost:8080/api/students/top3`
   Method: GET

---

### Step 6: Additional Notes
- **Error Handling**: The code includes basic error handling (e.g., throwing exceptions for non-existent students). You can enhance it with custom exceptions and global exception handlers.
- **Validation**: Add validation (e.g., `@NotNull`, `@Size`) to the `Student` entity using `javax.validation` constraints.
- **Security**: For production, secure the APIs with Spring Security and use HTTPS.
- **Testing**: Write unit tests using JUnit and Mockito for the service and controller layers.
- **Documentation**: Use Swagger/OpenAPI for API documentation by adding the `springdoc-openapi-ui` dependency.

---

This completes the setup and implementation. Let me know if you need clarification or additional features!