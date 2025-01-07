6. Practice Assignments
Task 1: Create a "CodingGita Students" database

------use codinggita  

Create a new MongoDB database called CodingGita. Add two collections:

students: Name, roll number, department, year, courses enrolled.
courses: Course code, name, credits, instructor.
Insert sample data into both collections.

-------db.students.insertMany([
  { 
    "name": "Jenil",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 103,
    "department": "Electrical Engineering",
    "year": 3,
    "coursesEnrolled": ["EE101", "EE102"]
  }
]);



--------db.courses.insertMany([
  { 
    "courseCode": "CS101", 
    "courseName": "Introduction to Programming", 
    "credits": 3, 
    "instructor": "Prof. Sharma" 
  },
  { 
    "courseCode": "CS102", 
    "courseName": "Data Structures", 
    "credits": 3, 
    "instructor": "Prof. Gupta" 
  },
  { 
    "courseCode": "CS103", 
    "courseName": "Algorithms", 
    "credits": 3, 
    "instructor": "Prof. Kapoor" 
  },
  { 
    "courseCode": "EE101", 
    "courseName": "Basic Electrical Engineering", 
    "credits": 4, 
    "instructor": "Prof. Verma" 
  },
  { 
    "courseCode": "EE102", 
    "courseName": "Circuit Theory", 
    "credits": 4, 
    "instructor": "Prof. Yadav" 
  }
]);


Task 2: Perform CRUD operations

Add a few more students and courses to the database.

-------db.students.insertMany([
  {
    name: "ABC",
    rollNumber: "103",
    department: "Electrical Engineering",
    year: 1,
    coursesEnrolled: ["EE101", "EE102"]
  },
  {
    name: "DEF",
    rollNumber: "104",
    department: "Computer Science",
    year: 2,
    coursesEnrolled: ["CS101", "CS201"]
  }
])


--------db.courses.insertMany([
  {
    courseCode: "CS201",
    name: "Algorithms",
    credits: 4,
    instructor: "Dr. Clark"
  },
  {
    courseCode: "EE101",
    name: "Circuit Theory",
    credits: 3,
    instructor: "Dr. Adams"
  }
])



Query data based on:
Department (e.g., "Computer Science").
---------
db.students.find({ department: "Computer Science" })


Year (e.g., "2").
-------
db.students.find({ year: 2 })

Courses enrolled (e.g., "CS101").
-------
db.students.find({ coursesEnrolled: "CS101" })

Update the courses for a specific student (e.g., adding a new course).

-------
db.students.updateOne(
  { name: "Dristi" },
  { $push: { coursesEnrolled: "CS201" } }
)

Delete a student or course from the database.

-------
db.students.deleteOne({ name: "DFF" })

db.courses.deleteOne({ courseCode: "CS102" })