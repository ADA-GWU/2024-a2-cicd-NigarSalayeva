First of all for running the project, we need java version 17
I used "export JAVA_HOME=`/usr/libexec/java_home -v 17.0.10`", and firefox downloaded. 
Commands for run:
mvn clean install
mvn -N wrapper:wrapper
Then you can test your cases.
Test cases and their explanation:
### FunctionalityTests.java

This class contains tests related to the functionality of the `StudentService` class.

#### Test Case 1: testStudentSearchById()
- **Description:** Tests the functionality of finding a student by ID.
- **Explanation:** It mocks the behavior of the `studentRepository` to return a student when `findById()` is called with ID 1. Then, it calls `getStudentById()` method of `studentService` and asserts that the result is not null.

#### Test Case 2: testStudentSearch()
- **Description:** Tests the functionality of searching for students by first or last name.
- **Explanation:** It creates three sample students and a list of students. Mocks the behavior of `studentRepository` to return the list of students when `findAll()` is called. Then, it calls `getStudentByEitherName()` method of `studentService` and asserts that the number of found students matches the expected count.

#### Test Case 3: testFindUsersByFirstName()
- **Description:** Tests the functionality of finding users by their first name.
- **Explanation:** It mocks the behavior of `studentRepository` to return a list of students with a specific first name. Then, it calls `findByName()` method of `studentRepository` and asserts that the result is not null and contains one element.

### UnitTests.java

This class contains unit tests for various functionalities related to students and courses.

#### Test Case 1: testTotalCourses()
- **Description:** Tests if the number of courses corresponds to the added courses for a student.
- **Explanation:** It generates a random number of courses, creates a student, adds those courses to the student, and then asserts that the number of courses for the student matches the expected count.

#### Test Case 2: testCreditCalculation()
- **Description:** Tests if the total credits correspond to the sum of added credits for a student's courses.
- **Explanation:** It generates a random number of courses with random credits, creates a student, adds those courses to the student, calculates the total credits, and then asserts that the total credits match the sum of the added credits.

#### Test Case 3: testStudentNameNotNull()
- **Description:** Tests if the first name of a student is not null.
- **Explanation:** It creates a student, sets a first name, and then asserts that the first name is not null.

#### Test Case 4: CreateUser()
- **Description:** Tests the functionality of creating a user via a web interface.
- **Explanation:** It simulates filling out a form to create a new student on a web page. It enters data for student ID, first name, last name, and email, and then submits the form.

#### Test Case 5: CheckUser()
- **Description:** Tests if a user is successfully created by checking their presence in the list of students.
- **Explanation:** It checks if the student added in the previous test (`CreateUser()`) is present in the list of students displayed on a web page. It searches for the first and last name of the student and asserts their presence.
