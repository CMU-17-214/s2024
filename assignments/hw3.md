# Homework 3: Santorini (Part 1)

In this assignment, you will design and implement the core logic of a board game called Santorini (2 players, without god cards) in Java and you will review other designs for this game. The focus of this assignment is on considering design alternatives for code. This assignment is intended as a gentle introduction to modeling on a relatively simple problem. It is intended to be low stakes and you will have opportunities to receive feedback and learn from mistakes. In Homework 6, we will revisit the game and extend it with god cards and with a GUI. 

**This homework has 3 milestones:**

* Milestone 3a: You will design and implement the core of Santorini.
* Milestone 3b: You will critique other designs and implementations of Santorini.
* Milestone 3c: You have an opportunity to revise your design and implementation based on our and other students' feedback. 

Milestone 3a and 3c are evaluated with the same criteria. Milestone 3a will be graded but will not count toward your final grade; instead we will regrade your design in Milestone 3c.



This assignment has the following learning goals:

* Demonstrate a comprehensive design and development process including object-oriented analysis, object-oriented design, and implementation.

* Demonstrate the use of design goals to influence your design choices, assigning responsibilities carefully, using design patterns where appropriate, discussing trade-offs among alternative designs, and choosing an appropriate solution. The core logic of your solution must be testable and completely independent from your solution’s eventual graphical user interface (GUI).

* Communicate design ideas clearly, including design documents that demonstrate fluency with the basic notation of UML class diagrams and interaction diagrams, the correct use of design vocabulary, and an appropriate level of formality in the specification of system behavior.

To start the assignment, use the GitHub classroom link from the Canvas assignment to create your personal repository.  It will only contain a template for one design document -- you will check in both your design documents and your code to this repository. Consult the appendix for guidance on how to make a new Maven project. 



## Milestone 3a: Design and Implementation

You will analyze, design, and implement the game Santorini without god cards (see appendix for rules). You should focus on the game-related functionality of the program, not its user interface. Think of playing the game by calling a sequence of methods, which you could execute in a test case; it is also helpful to think about and possibly sketch out the GUI and how it interacts with the game at this early stage. Note that the game (without god cards) is fairly simple, so you likely won't need more than a few classes/objects/methods.

Textbooks often describe a sequential process where the solution is designed before it is implemented. You might find it more convenient to start with coding and iteratively change and refactor the code until you are happy with the design, to create UML diagrams as documentation after the fact. In practice, developers may shift between different strategies and orders of formal design, exploratory coding, and sketching diagrams. We recommend to start at least with some domain analysis and rough modeling. If you adopt a coding-first approach, make sure that you think carefully about your design and are willing to substantially change your code if you discover problems.

### Analysis & Design

For analysis and design we expect you to create a number of design documents.

We strongly recommend to not auto-generate models from code with tools, as those are often of low quality. Diagrams should be consistent with one another and other diagrams submitted with the homework.

**Deliverable 1: Domain model.** Create a domain model describing the important concepts of the game. Your domain model should be represented by a UML class diagram; you may optionally include a glossary. For more information on domain models, see Chapter 9 of Larman’s Applying UML and Patterns. Turn this in as <code>domain-model.pdf</code> in the root directory of your git repository.

**Deliverable 2: System sequence diagram.** Create a system sequence diagram identifying all interactions between a user and the system when the user plays the game. The system sequence diagram should help you determine what interactions the high-level system makes available to its users. For more information on system sequence diagrams, see Chapter 10 of Larman’s Applying UML and Patterns. Turn this in as <code>system-sequence-diagram.pdf</code>.

**Deliverable 3: Behavioral contract.** Provide behavioral contracts for the following interaction initiated by the user: _The user attempts to move a worker_. The contract should explicitly describe the preconditions and postconditions for the interaction, and your behavioral contract should be consistent with your domain model and interaction diagrams. Constructing behavioral contracts should help you envision important changes of internal state of the game when a player interacts with the game. You may provide explicit examples to clarify your contract. For more information on contracts, see Chapter 11 of Larman’s Applying UML and Patterns. Turn this in as <code>contract.pdf</code>.

**Deliverable 4: Object model.** Create an object model of your game, documented as a UML class diagram. The object model should describe the classes and interfaces of your design, as well as their key associations (with cardinalities), attributes, and methods. For more information on class diagrams, see Chapter 16 of Larman’s Applying UML and Patterns. Model only the core of the game, not GUI elements or test code. Turn this in as `object-model.pdf`.

**Deliverable 5: Justification for handling state.** The implementation needs to store state about the status of the game (at least players, current player, worker locations, towers, and winner). One key design question is usually what objects should store what state. For each kind of state the game needs to store explain where you store it. Using the template provided in the starter repository, provide a justification (with reference to design goals/principles/heuristics) for your responsibility assignment for state; discuss the alternatives you had considered and the trade-offs they entailed that led you to choose this particular design (essentially, your design process). Ensure that your answer is consistent with your object model. Turn this in as `state-justification.md`.

**Deliverable 6: Justification for building action.** Reason about how the implementation determines what is a valid build (either a normal block or a dome) and how it performs the build. Identify what actions are needed and which objects and methods are responsible for performing those actions. Provide a justification (with reference to design goals/principles/heuristics) for your decision on assigning responsibilities; discuss the alternatives you had considered and the trade-offs they entailed that led you to choose this particular design (essentially, your design process). Include the relevant parts of an **object-level interaction diagram** (using method names and calls) for your final design. For more information on interaction diagram notation, see Chapter 15 of Larman’s Applying UML and Patterns. Turn this in as `build-justification.pdf` containing both the text of your answer and the interaction diagram.



In summary, we expect 6 files for the design part of this assignment: `/domain-model.pdf`, `/system-sequence-diagram.pdf`, `/contract.pdf` (for moving a worker), `/object-model.pdf`, `/state-justification.md` (for responsibility assignment regarding state), and `build-justification.pdf` (for responsibility assignment regarding the build action). 

To submit these documents, (a) push them to the root directory of your Santorini repository on Github and (b) submit them as a zip file for peer review to Canvas. *Do not include your AndrewID or name in any of the documents so that peer review can be performed anonymously.*

### Implementation & Test

Implement the game in Java. As usual, document your code for all public functions.

It is encouraged that your tests should include unit tests as well as integration tests that set up the game and play sequences of turns. To achieve that, it is a good strategy to write tests while you implement each function, and go back to add a little more tests in case you missed any important test cases and functionality after you complete your implementation.

There is no specific numeric goal for testing (neither for your codes or for our grading), but we expect to see tests of individual key functions (e.g. move and build functions) and tests of sequences of multiple actions of game play. But we are NOT looking for coverage of every possible corner case, and we will NOT inject bugs to evaluate the bug-finding ability of your test suites like Homework 2. Remember that this homework is not all about tests, and you should not spend too much time writing **complete** test suites. However, as a useful and necessary step in software construction, tests are helpful in that they can help you build confidence that your implementation is correct at a high level and that your interfaces are easy to use. 

We would like you to run your code by calling the methods directly. We do not expect a user interface, either in command line or graphical, in this assignment. You may find it useful to create a simple command line interface when you are developing the code, but we don’t expect or recommend that you do so.

Your implementation should determine when somebody has won by moving to the third level. You do not need to detect that a player won because the other player cannot move.

You should update your design documents from milestone 3a based on insights gained from the implementation. You can develop models and code in any order and typically there will be some iteration. However, we expect that the submitted final models and code align.

**Deliverables:** Commit all your code to your GitHub repository and ensure that your project is built and tested on Github Actions -- which you will need to set up yourself (see appendix 3). 

## Milestone 3b: Peer Review

You will review other solutions to milestone 3a and will point out design problems. This is an exercise in critically reflecting on other designs and identifying common design problems.

About 3 days after the milestone 3a deadline, we will assign you 2 or 3 design documents (not code) from milestone 3a. In addition to  solutions from other students, we might provide you with designs from the course staff that have known problems. You will submit your reviews of these solutions according to a provided rubric on Canvas. Your reviews will be visible to author of those solutions. Reviews are anonymous (reviewers will not know the authors of the solutions and authors will not know the identity of the reviewers). Your reviews should be conducted through the Canvas peer review system with the rubric, not simply as comments for each assigned review.

We will evaluate whether your reviews correctly point out design problems that exist or incorrectly point out problems where code is well designed.

(We do not expect you to spend more than 1 hour per review.)

## Milestone 3c: Revised Design and Implementation

Based on our milestone 3a feedback and peer feedback received after milestone 3b, you now have the opportunity to redesign your solution. We encourage you to rethink your design based on the feedback and refactor it or start from scratch. If your solution for milestone 3a received full credit and you received no useful feedback from milestone 3b, you do not need to perform any changes and can submit the same commit URL.

You may use other design ideas you saw in milestone 3b as inspiration to improve your own design, but you are fully responsible yourself for the correctness the designs you submit.

Briefly describe changes between your milestone 3a and 3c solution (if any) in `/changes.pdf` or `/changes.md`.

We will assess milestone 3c with the same rubric as milestone 3a. We are looking for the same deliverables as in milestone 3a.





## Submitting your work

For milestone 3a, submit your work in two locations: (1) Submit a link to your final commit to Canvas. All design documents should be located in the root directory of your repository.  (2) Upload all 6 design documents in a single zip file (not including any code or other files) to Canvas for peer review. **Make sure your submissions for 3a do not include your AndrewID or your name. These submissions will be assigned to your classmates for peer review.**

For milestone 3b, you will perform code review directly on Canvas.

For milestone 3c, you will again submit a link to your final commit to Canvas. All design documents should be located in the root directory of your repository. 

As usual, the link must have the format `https://github.com/CMU-17-214/<reponame>/commit/<commitid>`.



## Evaluation

The assignment is worth 230 points total, divided as follows:

* 30 points for submitting reasonably complete designs and implementation at Milestone 3a
* 170 points for the correctness/quality of the designs and implementation, assessed in both Milestone 3a and Milestone 3c. We will only count the Milestone 3c grade.
* 30 points for peer review in Milestone 3b.



*If the submitted link does not have the right format, we will not be able to grade your solution and will assign 0 points.*

Specifically, we expect to grade the homework with the following rubric:

**Initial submission (30 points, milestone 3a)**

1. [ ] 10: The GitHub submission includes a reasonably complete version of all design documents that demonstrate a good-faith attempt at modeling the problem (`domain-model.pdf`,  <code>system-sequence-diagram.pdf</code>, <code>contract.pdf</code>, `object-model.pdf`, `build-justification.pdf`, and `state-justification.md`)
2. [ ] 10: The design documents and only design documents are submitted in a zip file to Canvas without obvious identifying information (no name or AndrewID in any of the documents)
3. [ ] 10: The GitHub submission includes reasonably complete code and tests that demonstrate a good-faith attempt at implementing the game.

**Domain analysis (25 points, milestone 3a/c):**

3. [ ] 10: The domain model in file <code>domain-model.pdf</code> describes the vocabulary of the problem with reasonable completeness, uses suitable notation (right UML boxes, named associations with cardinalities, association vs field, reasonable naming), and is at the right level of abstraction
4. [ ] 10: The system sequence diagram in file <code>system-sequence-diagram.pdf</code> is reasonably complete, uses suitable notation, and is at the right level of abstraction.
5. [ ] 5: The behavior contract in file <code>contract.pdf</code> is reasonably complete regarding pre- and post-conditions and at the right level of abstraction.

**Object-oriented design and justification (70 points, milestone 3a/c):**

6. [ ] 15: The object model in file `object-model.pdf` is reasonably complete, uses suitable notation (right UML boxes, named associations with cardinalities, association vs field, reasonable naming), and is at the right level of abstraction. 
7. [ ] 10: The interaction diagram in `build-justification.pdf` is reasonably complete, uses suitable notation, is at the right level of abstraction, and is consistent with the object model (called methods exist in target class, caller has access to target objects).
8. [ ] 20: Responsibility assignment for the state is clearly explained, appropriate and well justified  in `state-justification.md`. We will check:
   - a. It is clear from the description where players, current player, worker locations, towers, and the winner are stored. 
   - b. The description matches the object model.  
   - c. The responsibility assignment for each piece of state is justified with suitable design vocabulary (design goals/principles/heuristics/patterns). The assigned responsibilities and justifications are plausible.
   - d. The justification demonstrates an engagement with design principles and tradeoffs, and discusses design alternatives in a meaningful way. 

9. [ ] 20: Responsibility assignment for checking and performing build actions is clearly explained, appropriate, and well justified in `build-justification.pdf`. We will check:
   - a. It is clear from the description what checks are performed to determine whether a build action is valid and how the state of the game is updated when the action is performed.
   - b. The description matches the interaction diagram.
   - c. The responsibility assignment for each method involved in checking and performing builds is justified with suitable design vocabulary (design goals/principles/heuristics/patterns). The assigned responsibilities and justifications are plausible.
   - d. The justification demonstrates an engagement with design principles and tradeoffs, and discusses design alternatives in a meaningful way. 

10. [ ] 5: Responsibility assignment for checking and performing a move action is appropriate (as recognizable from the object model and implementation; no description or justification requirement).

**Implementation and testing (75 points, milestone 3a/c):**

11. [ ] 30: All core functionality of the game is implemented and follows all rules as specified. Specifically we check that your code does the following: initializes the game, rejects invalid moves, rejects invalid builds, updates the state after moving, updates the state after building, determines the winner, ends the game
12. [ ] 10: The implementation aligns with models. We will look for: same names, state and methods in the same classes/objects, associations' cardinalities reflect implementation, and interactions possible as shown in diagrams.
13. [ ] 10: The implementation is well tested, using both unit tests and integration tests. The key functions like validating a move, a build, and tests of sequences of game play are tested at a reasonable level. The tests follow good practices (e.g. redundancy, independence, readability. NOT including the completeness of test suites).
14. [ ] 5: The public methods of the code are well documented.
15. [ ] 5: The build and tests are automated on Github Actions and succeed.
16. [ ] 5: Commits are reasonably cohesive; commit messages are reasonable.
17. [ ] 10: The implementation practices reasonable style, and the codes can pass a reasonable linter check (e.g. checkstyle.xml from previous homework).



**Peer review (30 points, milestone 3b):**

18. [ ] 10: Reviews are provided for all solutions, following the provided rubric. 
19. [ ] 10: The reviews identify real design problems, if any.
20. [ ] 10: The reviews do not point out good design decisions as problems, if any.



## Appendix 1: Santorini Rules

Santorini has very simple rules, but the game is very extensible. You can find the original rules [online](https://roxley.com/products/santorini). You can find a copy of the game in the common space of TCS Hall on campus. Beyond the actual board game, you can also find a mobile app that implements the game if you want to try to play it.

In a nutshell, the rules are as follows: The game is played on a 5 by 5 grid, where each grid can contain towers consisting of blocks and domes. Two players have two workers each on any field of the grid. Throughout the game, the workers move around and build towers. The first worker to make it on top of a level-3 tower wins. Note that though the official rules require that if a player cannot further move any worker, they will lose, **you do not need to automatically detect this winning condition in your solution**. You also don’t need to handle more than two players.

As set up, both players pick starting positions for both their workers on the grid. (For simplicity, in Homework 3 and 6, *you can assume a player A always starts*). Players take turns. In each turn, they select one of their workers, move this worker to an adjacent unoccupied field, and afterward add a block or dome to an unoccupied adjacent field of their new position. Locations with a worker or a dome are considered occupied. Workers can only climb a maximum of one level when moving. Domes can only be built on level-3 towers. You can assume there are infinite tower/dome pieces to play.

That's it. You probably want to play a few rounds to get a feel for the game mechanics. There are god powers that modify the game behavior, but those will not be relevant until Homework 6.



## Appendix 2: Notation & Tools

To ease communication and avoid ambiguity, we expect all models to use UML notation for class and sequence diagrams. Chapters 9, 10, 15, and 16 of Larman’s Applying UML and Patterns provide many details and guidance on UML notation. We do not require much formality, but we expect that associations are used rather than attributes where appropriate and that each association includes a name and cardinalities. Attributes and methods should be specified correctly, but we do not require precise descriptions of visibility or types. 

It is important that your models demonstrate an understanding of appropriate levels of abstraction. For example, your domain model should not refer to implementation artifacts, and your object model should not include low-level details such as getter and setter methods, unless they aid the general understanding of your design. 

UML contains notation for many advanced concepts, such as loops and conditions in interaction diagrams. You may use UML notation for these advanced concepts, but we do not require you to do so. If you find you need advanced concepts, you may describe such concepts with your own notation or textual comments, as long as you clearly communicate your intent. 

To maximize clarity, we recommend that you draw UML diagrams with software tools. We do not require specific tools, and you may share tool-related tips on Piazza. There are several easy to use online tools like [Draw.io](https://draw.i/) and [Yumly](https://yuml.me/), and also many desktop tools and IDE plugins. We strongly recommend that you do not mechanically extract models from a software implementation; such mechanically generated models are almost always at an inappropriate level of abstraction. We will accept handwritten models or photographs of models (such as whiteboard sketches) if the models are clearly legible.



## Appendix 3: Setting up your project

For Java, you can generate the default setup for a Maven project from the command line with `mvn archetype:generate` and use `maven-archetype-quickstart` as the template. This will set up an initial `pom.xml` file and some example directories.

We recommend to set up the Checkstyle plugin. You can look at the `pom.xml` file from homework 1 for how to do this (`maven-checkstyle-plugin`) and can also copy the checkstyle configuration in `checkstyle.xml`.

We recommend to set up a `.gitignore` file to avoid committing generated files. See homework 1 for an example.

We require you to set up GitHub actions to compile and test the project. You can adapt the setup from homework 1 in `.github/workflows`.

Further reading: [Maven - How to create a Java project](https://mkyong.com/maven/how-to-create-a-java-project-with-maven/), [Maven Archetype Plugin – archetype:generate](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html), [Maven – Introduction to the POM](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html), [Maven – Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html), [ignoring files in Git](https://www.atlassian.com/git/tutorials/saving-changes/gitignore), [Quickstart for GitHub Actions](https://docs.github.com/en/actions/quickstart)
