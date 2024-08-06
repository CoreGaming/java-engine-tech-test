# Core Gaming Game Logic Developer - Tech Test 

## The Test 

The purpose of this test is to create simple game logic based on the detailed specifications and prove its correctness.

We realise that everyone has different levels of skill and experience when it comes to development, so we have split the test into multiple tasks. If you do not have the knowledge to complete all questions, that's okay. We want to see how you approach the problem and get a feel for how you code. This also gives you an opportunity to present yourself at your best while working in the comfort of your home.

The test itself emulates the basic flow of applications we develop on a daily basis.

It might help to start with a quick research of what `Slot Machine` is online;

If you have any questions, please feel free to get in touch with your point of contact. We’ll get back to you as soon as possible. 

### Technical Requirements
 * Git
 * Java 8 (JDK 8)
 * Maven 3.5.4
 * Ability to view *.xlsx files

## Review Criteria 

* Understanding of tasks
* Ability to follow instructions
* Correct implementation
* Code organisation and clarity 
* Unit tests usage and results
* Progress via git commit history

## Submission Requirements 

1. Please replace the contents of this README.md with: 

    a. A short note explaining the technology choices you have made. 

    b. Any instructions required to run your solution. 

2. Please send us your submission as a **git bundle** attachment showing your commit history with all your commits in the master branch. 

Please note that we will have to return all submissions that:
* Fail to build
* Fail unit tests

## Notes

* Don't spend more than 4 hours on this test.
* If you've added anything you particulary like or consider noteworthy, make sure to point it out to us.

### Setup and Details
 * Clone the repository contents.
 * In the command line, navigate to the project's root folder.
 * Build all modules with:
```
mvn clean install -DskipTests
```
 * To run an HTTP web server, execute: 
```
java -jar Server/target/Server-1.0.1-jar-with-dependencies.jar
```
 * To run tests, in another command line execute: 
```
cd Client && mvn test
```
 * Watch the output for any test `fail`/ `pass` information.
 * All data tables can be found in the 'profile.xlsx' file under titled tabs. You do not have to parse the xlsx file.

### Basic Tasks

#### Before you continue, please ensure that the default project builds successfully and all unit tests are passing ####

1. Find and familiarize yourself with the Server, Client, and unit tests source files. Hint: The `test` is structured as a simple client-server application. The server is responsible for performing logic and generating responses to client requests. The client sends requests and contains a test suite which is used to validate given behaviours.
2. Add a `table` client request and implement a server response that returns a randomly chosen `Value` from `BasicWeightTable` based on the percentage `Chance`. Hint: For this step, ignore data in the `99% confidence level` column.
3. Implement a statistical test (or tests) which would run multiple `table` requests and check aggregated responses against the expected occurrences defined in `BasicWeightTable`. Hint: How many times do you think `Value: £3.00` will be returned from the server? For this step, you can use the `100k runs error margin` value to compare the results with 99% confidence and check if your implementation is correct. How do you interpret `error margin`?
4. It might help to improve the communication protocol by switching to some marshallable (via an existing library) data format e.g. JSON or another one you're comfortable with. Following tasks will require some data analysis of the comms. Make sure to update your tests accordingly.

#### More Interesting Tasks

1. Add a `spin` request which will return a 3x3 matrix of symbols. Use `Symbols` and `Reels` tables. For every reel, randomly choose one position and populate the whole matrix column with results starting at that drawn position. Hint: Think of slot machines with reels/wheels. How can those behave? What could be the chances of each symbol being selected?
2. For each result where the middle row of your matrix satisfies one of the rules defined in `Win patterns`, return the associated `Value` along with the pattern that has been satisfied (if any). Hint: Does order matter?
3. Implement a statistical test (or tests) which would run multiple `spin` requests and check aggregated responses against the `Expected chance` defined in the `Win patterns` table. Hint: Again, you can use the `100k runs error margin` value to compare the results with 99% confidence and check if your implementation is correct. 
4. Add `Return To Player` (RTP) value as a percentage for both `table` and `spin`, assuming each request costs `£3.50`. To make it harder, we will not provide you with a table to compare your results this time. Hint: To find the requested result, compare the total cost spent on initiating requests and total value returned in responses. You can use a 1% margin error for RTP comparison.