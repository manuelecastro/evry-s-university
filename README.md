# evry's-university
You were hired to build a system to manage Evry's University. Your job is to create a Java application that includes the entities (classes) below. You may include/remove/edit attributes, just explain why. You may include more details/functionalities, just describe them at the end of this document.

## How to start?

Clone this repository and create your main branch based on your name (firstname-lastname)

```
git clone git@github.com:thiago-buarqque/evry-s-university.git
cd evry-s-university
git checkout -b firstname-lastname
```

**Do not code into the main branch, it will give you an error when uploading to Github. You must use your branch to perform your exercises and send a PR every time a functionality is ready or you want a review for some reason.**

> Note: If you find something that is not coherent, let me know.

### What will you learn/exercise?

- POO (inherit, abstraction, and encapsulation)
- Recursion
- Data structure
- Java features
    - Lists
    - Enums
    - Dates
- Design pattern (Singleton)

# E N T I T I E S

1. **Employee**
   - `employeeId`: Long
   - `name`: String
   - `email`: String
   - `department`: Department
   - `hireDate`: Date
   - `salary`: Double

2. **Professor (extends Employee)**
   - `classes`: List<Class> // Includes the current semester classes and past classes
   - `officeRoom`: Room
   - `specialization`: String

3. **AdministrationEmployee (extends Employee)**
   - `role`: EmployeeRole (Ex: 'Dean', 'Secretary') // Imagine that the Dean can change anything in the system (like grades, classes, add/remove employees). The secretary does the same, except add/remove employees.
   - `officeRoom`: Room

4. **Student**
   - `studentId`: Long
   - `firstName`: String
   - `lastName`: String
   - `email`: String
   - `enrollmentDate`: Date
   - `course`: Course
   - `grades`: List<Grade>

5. **Department**
   - `departmentId`: Long
   - `name`: String
   - `building`: String
   - `professors`: List<Professor>
   - `adminStaff`: List<AdministrationEmployee>
   - `coursesOffered`: List<Course>

6. **Class**
   - `classId`: Long
   - `closeDate`: Date
   - `name`: String
   - `department`: Department
   - `room`: Room
   - `openDate`: Date
   - `professor`: Professor

7. **Room**
   - `roomId`: Long
   - `building`: String
   - `roomNumber`: String
   - `capacity`: Integer
   - `department`: Department

8. **Grade**
   - `student`: Student
   - `class`: Class
   - `gradeValue`: GradeValue (this is an enum, the possible values are A, B, C, D, E, and F)

9. **Course**
   - `name`: String
   - `id`: Long
   - `department`: Department
   
10. **GradeValue** (enum)
   - A, B, C, D, E, F

11. **EmployeeRole** (enum)
   - 'Dean', 'Secretary'
   
# R E Q U I R E M E N T S


1. The `Student` must be able to:
    a. Check their current classes;
    b. Check past classes (the class must show the student's grade);
    c. Quit a class.
2. The `Professor` must be able to:
    a. Grade students;
    b. List their classes;
    c. List the students from a `Class`. In this functionality, you must present the option to sort the students by alphabetical order (a to z or z to a). Sort the students using Merge Sort or Quick Sort. If you have difficulties coding these algorithms, code the Selection Sort.
3. The `Secretary` employee must be able to:
    a. Add/remove/update students;
    b. Add/remove students from a course;
    c. Add/remove students from classes;
    d. Close classes (if a class has the endDate set, it's closed, nothing in it can be updated)
4. The `Dean` employee must be able to do everything the Secretary can plus:
    a. Add/remove employees

# N O T E S

- Use the employeeId and studentId as the identifier to log in to the system (this is the matrícula), there is no password for now.
- Create a global class that will act as a database, and use the **Singleton** design pattern to access it when needed. The `Database` class would look like this.

```
Class Database {
    private List<Student> students = new ArrayList();
    private List<Employee> employees = new ArrayList();
    private List<Professor> professors = new ArrayList(); // professors are also employees, when registering a professor, create the object, add it to the `employees` list, and then to the professors' list. Do the opposite when removing.
    // ... other entities
    
    // Methods
    
    // Find<Entity>ById(Long id) -> find the Entity (Student, Professor, etc) by id
    // Update<Entity>(Long id) -> update the Entity (Student, Professor, etc) by id
    // Remove<Entity>(Long id) -> remove the Entity (Student, Professor, etc) by id
    // List<Entity>() -> List all Entities (Student, Professor, etc)
}
```

**Happy coding!!**
