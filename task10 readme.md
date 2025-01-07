
Task 1: Add multiple students
Insert at least 5 students into the students collection with unique roll numbers, names, departments, years, and subjects enrolled.
---------------
db.students.insertMany([
    { rollNumber: 1, name: "Jenil", department: "Computer Science", year: 2, subjects: ["NodeJS", "React"] },
    { rollNumber: 2, name: "Aarav", department: "Information Technology", year: 1, subjects: ["MongoDB", "React"] },
    { rollNumber: 3, name: "Ishita", department: "Computer Science", year: 2, subjects: ["NodeJS", "React Native"] },
    { rollNumber: 4, name: "Sanya", department: "Electrical Engineering", year: 3, subjects: ["Python", "NodeJS"] },
    { rollNumber: 5, name: "Rohan", department: "Mechanical Engineering", year: 4, subjects: ["MongoDB", "React"] }
]);




Task 2: Add multiple subjects
Insert 4 subjects into the subjects collection, each with 3 to 5 topics.
-------
db.subjects.insertMany([
    { name: "NodeJS", topics: ["JavaScript", "Express", "API Development"] },
    { name: "React", topics: ["Components", "State Management", "Hooks"] },
    { name: "MongoDB", topics: ["Data Modeling", "Queries", "Aggregation"] },
    { name: "Python", topics: ["Syntax", "Data Structures", "OOP Concepts", "File Handling"] }
]);



Task 3: Query students based on subject enrollment
Query the students collection to find all students who are enrolled in NodeJS.
-----
db.students.find({ subjects: "NodeJS" }, { name: 1, rollNumber: 1, _id: 0 });



Task 4: Add a new topic to a subject
Add a new topic to the NodeJS subject.
-----
db.subjects.updateOne(
    { name: "NodeJS" },
    { $push: { topics: "Authentication" } }
);


Task 5: Query subjects with multiple topics
Query the subjects collection to find subjects that contain at least 4 topics.
--------


Task 6: Update student enrollment
Add the subject "React Native" to Jenil's subjects.
-----
db.students.updateOne(
    { name: "Jenil" },
    { $addToSet: { subjects: "React Native" } }
);

Task 7: Query all students
Query all students in the database and print out their names and enrolled subjects.
-----

db.students.find({}, { name: 1, subjects: 1, _id: 0 });


Task 8: Update multiple students' year
Update the year for all students in the Computer Science department to year 3.
------
db.students.updateMany(
    { department: "Computer Science" },
    { $set: { year: 3 } }
);


Task 9: Add new topics to multiple subjects
Add new topics to React, NodeJS, and MongoDB subjects. Ensure each subject gets at least one new topic.
----
db.subjects.updateMany(
    { name: "React" },
    { $push: { topics: "Performance Optimization" } }
);

db.subjects.updateMany(
    { name: "NodeJS" },
    { $push: { topics: "Websockets" } }
);

db.subjects.updateMany(
    { name: "MongoDB" },
    { $push: { topics: "Indexing" } }
);


Task 10: Remove a topic from a subject
Remove the topic "Express" from the NodeJS subject.
-------
db.subjects.updateOne(
    { name: "NodeJS" },
    { $pull: { topics: "Express" } }
);


Task 11: Query all students in a specific year
Query and return all students in year 2 or year 3.
------
db.students.find(
    { year: { $in: [2, 3] } },
    { name: 1, rollNumber: 1, year: 1, _id: 0 }
);


Task 12: Delete a student by roll number
Delete a student from the database using their roll number.
-------
db.students.deleteOne({ rollNumber: 3 });


Task 13: Delete all students from a department
Delete all students who belong to the Electrical Engineering department.
----------
db.students.deleteMany({ department: "Electrical Engineering" });


Task 14: Retrieve all topics for a subject
Query the MongoDB subject and retrieve all topics listed for it.
------
db.subjects.findOne({ name: "MongoDB" }, { topics: 1, _id: 0 });


Task 15: Count the number of subjects in which a student is enrolled
Write a query that returns the number of subjects each student is enrolled in
---------
db.students.aggregate([
    {
        $project: {
            name: 1,
            rollNumber: 1,
            subjectCount: { $size: "$subjects" }
        }
    }
]);
