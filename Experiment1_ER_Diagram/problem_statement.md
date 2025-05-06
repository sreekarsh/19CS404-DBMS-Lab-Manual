# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

*User Requirements:*
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

*User Requirements:*
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Student Name

## Scenario Chosen:
University

## ER Diagram:
![image](https://github.com/user-attachments/assets/9ca136ee-9ae6-4918-b091-ed9d5f908241)


## Entities and Attributes:

Department: Dept ID, Dept Name
Student: Reg. No, Name, Date of Birth, Phone No, Email, Program Name, Dept Name
Course: Course ID, Course Name, Program Name, Credits, Lab/Theory
Professor: Teacher ID, Name, Phone No, Course ID
Prerequisite: Prerequisite Course ID, Prerequisite Course Name, Course ID


## Relationships and Constraints:

Admission (Department–Student): (1:M, Total–Total)
Enrollment (Student–Course): (M:M, Total–Total)
Taught by (Course–Professor): (1:M, Total–Total)
Before Enrollment (Course–Prerequisite): (1:M, Partial–Total)

## Extension (Prerequisite):

In the ER diagram, prerequisites are modeled using a separate entity named *Prerequisite. This entity contains attributes such as *Prerequisite Course ID, Prerequisite Course Name, and Course ID, which links it to the main course. The relationship between *Course* and *Prerequisite* is named *Before Enrollment* and follows a one-to-many (1\:M) cardinality. This means a single course can have multiple prerequisites, but each prerequisite entry is tied to only one course. This design allows flexibility in assigning and managing prerequisites without cluttering the Course entity. It also ensures data consistency and simplifies prerequisite tracking. Total participation exists from the Prerequisite side, while Course has partial participation.


## Design Choices:

Entities like *Student, **Course, **Department, and **Professor* were chosen to represent key academic elements. Relationships such as *Enrollment* and *Taught by* show real-world interactions. *Prerequisite* was modeled separately to handle multiple prerequisites per course. A many-to-many relationship was used for enrollment to reflect real scenarios. We assumed each student belongs to a department, and not all courses need prerequisites. These choices ensure a clear, flexible, and normalized design.

## RESULT
Thus, the ER Diagram for university databse is developed successfully.
