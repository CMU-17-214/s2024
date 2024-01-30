# Homework 2: Unit Testing

In this assignment, you will test the FlashCards system that you expanded in the previous homework.

This assignment will give you experience creating unit tests against a specification and to cover code with tests as you write it. You will practice following dedicated testing strategies and best practices for unit testing. You will automate your tests with continuous integration and use test coverage tools.

Specifically, you will perform *structural testing* and *specification testing* for the Java implementation in your Homework 1 repo. 

## Starter code

Continue to work with the code from Homework 1. If you have made any changes to file names or interfaces in the provided code in the directories `cards`, `data`, or `ordering` please restore them to the original names and interfaces and do not change them in this assignment.

If you prefer a fresh start,  you can start over by creating a new branch off the first commit (find id of the first commit with `git log` in branch and follow these [instructions](https://stackoverflow.com/questions/7167645/how-do-i-create-a-new-git-branch-from-an-old-commit)) and then copy over your implementation for `RecentMistakesFirstSorter`. Your hw1 implementation of the command-line parser is not relevant for this homework.

## Tasks

### Part 1: Infrastructure setup

Set up the project so that you can write and execute unit tests. We explain *JUnit* both in class and provide an example setup in a lab, but you are welcome to use other test frameworks. Make sure that tests are automatically executed with `mvn test` and as part of the GitHub Actions build. We recommend also to identify how you can view test coverage in your IDE or in a generated report.


### Part 2: Specification-base testing

Read the public interface specification of every method in the FlashCard source code, except the exclusions below (don't forget your new `recentMistakesFirstSorter`). Write test cases that check whether the implementation covers the specification completely and precisely as best as possible -- even if the implementation is wrong! You may find implementation issues in your newly added `recentMistakesFirstSorter`; make sure to fix such bugs so that your tests all pass.

That means:

- Consider the input space and the specification to *intentionally* select valid and invalid inputs as tests.
- Write a test that confirms that everything that is stated works as expected. Guard against "typical" mistakes, such as off-by-one errors or forgetting to implement one part of a multi-faceted specification.
- Do not test what is not specified. Many specifications allow some flexibility and tests should not reject valid implementations of a specification. For example, if the potential nullity of a parameter is not stated, do not write a test that fails if the parameter is `null`. That might be intuitively (and realistically) undesirable behavior, but if it is not in the specification, it should not be tested. (Specifications are often a bit incomplete like that; writing comprehensive specifications can be tedious.)
- Ideally, follow a test design strategy discussed in class, such as *boundary value analysis*.

The goal is to achieve 100% specification coverage and to write tests that are good at detecting defects. Note that specification coverage is not automatically measurable.

We will evaluate the quality of your tests by injecting bugs into the implementations to see whether your tests catch them. We will also inject allowed changes to the implementation that do not violate the specification to see whether your tests still pass as expected. You can perform the same kind of experiments yourself to evaluate the quality of your tests by injecting some mistakes yourself (e.g., replacing `<` by `>` or by `<=`, injecting off-by-one errors by adding `+1` to expressions, or checking if the questions and answers are case-insensitive).

When writing test cases, make sure you follow good practices for test design, as discussed in class and the reading.

**What to test.** 

Minus the below exceptions, you should test **all functions that have specifications** in the original code base, including the new `recentMistakesFirstSorter` that you added.

You do _not_ need to test: 

- `toString`, `get*` methods: these contain trivial or non-essential functionality. Your tests may, of course, use getter methods.
- `Main.java` and any code written for parsing command line options: these depend heavily on your implementation in homework 1, for which we specified no interface.
- `loadCardsFromFile()` function in `CardLoader.java`: this deals with I/O.
- `CardShuffler.java`: randomness is hard to test.
- `UI.java`: you will not need to test UI.

Please note that the last four exclusions would not be industry-standard. They are nontrivial to test, though. We will show you later in the course how you can test such functionality.

Our reference implementation has about 40 tests.  As a hint, for `CardOrganizer.java`, there are many different possible combinations of sorters and repeaters.  You should _not_ need to test all combinations to achieve suitable specification coverage!


### Part 3: Structural testing

Write structural tests in **Java** for the files under the `achievement` folder to achieve 100% *branch* coverage. You do not need to test `UI.java` which is where achievements are displayed. You do not need to achieve a branch coverage goal for any other code, and we will not evaluate your test quality for the achievements with injected bugs.

*Hint:* You can call the `isAchieved` method for an AchievementType Enum as follows: `AchievementType.CORRECT.isAchieved(x, y)` where `x` is a long and `y` is a `CardDeck`. Changing CORRECT to a different enum will allow you to test each `isAchieved` method. 

As in Part 2, follow the best practices for unit testing.

**Report coverage** 

Extend the project's build system (Maven's `pom.xml`) so that it creates a coverage report with `mvn site`. The third lab provides a template. After you are finished with your tests, when you generate and open a coverage report, you should see 100% branch coverage for the `edu.cmu.cs214.hw1.achievement` package.

### Part 4: Documentation and Reflection

Add a file `reflection.md` to the root folder of your repository with the following sections:

In section **Testing strategy** briefly describe whether you followed any specific test case design strategy, such as boundary value analysis, when creating tests. Briefly explain, why you did or did not use these techniques. (about 1 paragraph)

In section **Specification vs structure testing** briefly reflect on your experience with the two different testing approaches by providing examples from your code. Was one harder or better than the other for you? (about 1 or 2 paragraphs)

If you used AI tools such as ChatGPT or Copilot for any part of homework 1 or 2, add a section **AI Tools** describing what you tried them for and whether you found them useful (open ended).

## Submitting your work

Always submit all code to GitHub. Once you have pushed your final code there, submit a link to your final commit in the format `https://github.com/CMU-17-214/<reponame>/commit/<commitid>`  on Canvas (the link identifies the right commit and branch for us, in case you do not work in the main branch). You can get this link easily when you click on the last commit (above the list of files) in the GitHub web interface. 

## Evaluation

The assignment is worth 100 points. We will grade the assignment with this rubric:

* [ ] Submissions that do not provide a link in the expected format can not be graded and will not receive credit.

**Specification-based Tests (30pt):**

- [ ] 10: No tests fail on a correct implementation. We will swap out the code in `cards`, `data`, and `ordering` for five different correct implementations of the provided specification. Points will be awarded proportional to the number of implementations that pass your test suite.
- [ ] 20: At least one test fails for each of about 20 bugs we introduce in an otherwise correct implementation. We will run your code against multiple new implementations in `cards`, `data`, and `ordering` that are entirely correct except for a single bug. One or more of your tests should fail because of said bug. Points will be awarded proportional to the number of bugs discovered by your test suite.

**Structural Tests (20pt):**

- [ ] 20: Test cases achieve perfect branch coverage on the required classes (10pt partial credit for >90% branch coverage).

**Test Quality (20pt)**
We will analyze 5 randomly sampled tests:
- [ ] 5: Tests are independent.
- [ ] 5: Tests are cohesive and small.
- [ ] 5: Tests avoid excessive redundancies.
- [ ] 5: Tests are readable (e.g., meaningful names, comments).

**Infrastructure and style (20pt):**

* [ ] 5: The project is set up to generate coverage reports (on the command line or in a file) with `mvn site` 
* [ ] 5: GitHub Actions runs tests for the Java code automatically.
* [ ] 5: The build passes on GitHub Actions
* [ ] 5: Most commits are reasonably cohesive and most commit messages are reasonably descriptive

**Reflection (10pt):**

- [ ] 5: Your writing on your testing strategy demonstrates an understanding of one or more relevant test case design strategies and supports your decision whether or not to adopt these.
- [ ] 5: Your reflection on the two forms of testing shows that you have given thought to the strengths and weaknesses of each based on your experience. The reflection is grounded in concrete experiences, not generic statements.
