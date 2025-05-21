# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Sanjai S

## Scenario Chosen:
University 

## ER Diagram:
![UNIVERSITY DATABASE](https://github.com/user-attachments/assets/58dd2f2f-c88b-4ccc-a719-6216b47200c4)


## Entities and Attributes:
Student: Register no, Name, Date of Birth, Email id, Dept, Year enrolled

Faculty: Faculty Id, Name, Department, Phone no, Email Id, Courses taught

Course: Course Id, Course name, Credits

Slots: Classroom no, Timings, Capacity

Hostel: Hostel Id, Room no, Warden

Library: Location, Department

Clubs: Name, Technical, Cultural, Sports

Final Exam: GPA, Score

Mode of Transport: Bus, Personal Vehicle

## Relationships and Constraints:
1. Chooses (Student → Slots)

Cardinality: Many-to-One (Many students can choose one slot)

Participation: Partial (Not all students must choose slots)

2. Enrolls (Student → Course)

Cardinality: Many-to-Many (A student can enroll in many courses and a course can have many students)

Participation: Partial (A student may or may not enroll)

3. Attempts (Student → Course)

Cardinality: Many-to-Many (A student can attempt many courses; a course can be attempted by many students)

Participation: Partial

4. Joins (Faculty → Faculty)

Cardinality: One-to-One (Each faculty joins once)

Participation: Total (All faculty must join)

5. Teaches (Faculty → Course)

Cardinality: One-to-Many (One faculty can teach many courses)

Participation: Partial (Faculty may or may not teach courses)

6. Borrows (Student → Library)

Cardinality: Many-to-One (Many students borrow from one library)

Participation: Partial (Not all students borrow)

7. Evaluation (Student → Final Exam)

Cardinality: One-to-One (One student has one final evaluation)

Participation: Total (All students must have evaluation)

8. Stays in (Student → Hostel)

Cardinality: Many-to-One (Many students stay in one hostel)

Participation: Partial (Some students may not stay in hostel)

9. Travel (Student → Mode of Transport)

Cardinality: One-to-One (Each student chooses one mode: Bus or Personal Vehicle)

Participation: Partial (Some students may not need transport)
...

## Extension (Prerequisite):
Prerequisite Modeling:

In this ER diagram, prerequisites are implicitly handled under the "Attempts" and "Enrolls" relationships between Student and Course.

If needed, a Prerequisite relationship between Course and Course can be added (self-relationship), indicating that one course is a prerequisite for another.

## Design Choices:
Entities like Student, Faculty, Course, Hostel, Library, Clubs were chosen because they are core components of a university system.

Slots were added to capture the timetable and capacity management.

Final Exam entity was introduced separately to focus on evaluation (GPA, Score) rather than just linking marks inside Student or Course.

Mode of Transport was separated because not all students need it; it also provides flexibility to extend for new transport modes later.

Relationships like Enrolls, Attempts, Teaches help maintain real-world connections between students, courses, and faculty.

Participation (total/partial) and cardinality (1:1, 1:N, N:M) decisions were based on practical university scenarios (e.g., one student can enroll in many courses but must have one GPA).

## RESULT
A clear and normalized ER diagram for a university database was successfully designed.

It captures major activities like enrollment, teaching, staying, traveling, evaluation, and participation in clubs.

The structure supports future extensions easily (e.g., adding Prerequisite courses, Billing systems).

Relationships are properly defined with correct cardinality and participation, making the database design robust and realistic.
