# Homework 1: Warm-Up with Flash Cards

In this assignment, you will complete a simple [flashcard](https://en.wikipedia.org/wiki/Flashcard) learning system. For now, we are keeping things simple and use an interactive command-line interface, one of the simplest and oldest user interfaces for computer programs. The goals of this assignment are to familiarize you with our course infrastructure, let you practice object-oriented programming in Java, and start using public libraries. While you will only write a little code for this assignment, you may spend significant time getting familiar with the language, infrastructure, and tooling.

## Provided Implementation

As is often common in software engineering practice, you won't start entirely from scratch but start with an existing implementation. Fortunately, it's even somewhat documented and clean, so you should be able to figure out what's happening by reading documentation and code. You may change existing code if you like. 

With the GitHub classroom link on Canvas create a Git repository with the provided starter code. You should use an IDE to load and edit the projects. We recommend (and will only provide support for) [VSCode](https://code.visualstudio.com/) for Java (and later TypeScript) development to reduce the tedium of switching between two IDEs, but you are welcome to use [IntelliJ](https://www.jetbrains.com/idea/) or other IDEs if you prefer (note you can get free access to Enterprise IntelliJ via an Education discount, which will give you access to TypeScript support).

## Tasks

**Task 1: Implement new card organizer.** Implement a new card organizer **RecentMistakesFirstSorter** by creating objects that implement the `CardOrganizer` interface. The organizer should work as follows: *"Orders the cards so that those that were answered incorrectly in the last round appear first. This reordering should be stable: it does not change the relative order of any pair of cards that were both answered correctly or incorrectly. So, if no cards were answered incorrectly in the last round, this does not change the cards' ordering."* 

Starting points: try to dissect the specification into its main components.  What should the behavior be under "typical" inputs (e.g., one card with a recent failure, one without; cards with several successes and failures), and what scenarios does it outline as exceptions? Do avoid implementing anything extra that is not part of the specification. 

We recommend to name your new sorter `RecentMistakesFirstSorter`. Your sorter should implement the *CardOrganizer* interface.

Note that only a relatively small amount of code is necessary to implement this new class, regardless of language. Only minimal changes will be required outside of your new class, in particular to test the new sorter by using it in place of the sorter the code starts with (`CardShuffler`).

**Task 2: Command-line interface.** There is already some implementation of a textual user interface that prints questions and reads answers.  But, the codebase implements a number of different card ordering and filtering mechanisms; the UI does not take advantage of them.  It also does not read in a filename for the card file; this is hard-coded.  This is not very user friendly.

Your task is to develop a proper command-line interface that parses provided arguments and sets up the right card deck and the organizing mechanisms. Parsing command-line options is a standard task that has been done many times before, no there is need to start entirely from scratch! Instead, you should find and use an **open-source library** for command-line options and use it to provide an interface comparable to this:

```
flashcard <cards-file> [options]

Options:
  --help          Show this help                                                                        
  --order <order> The type of ordering to use, default "random"
   						[choices: "random", "worst-first", "recent-mistakes-first"] 
  --repetitions <num> The number of times to each card should be answered
                  successfully. If not provided, every card is presented once,
                  regardless of the correctness of the answer.          
  --invertCards   If set, it flips answer and question for each card. That is, it 
                  prompts with the card's answer and asks the user
                  to provide the corresponding question. 
                  Default: false

```

(The program does not need to be runnable using the `flashcard` keyword as above; we just used that to illustrate concisely.)

Your code should provide these options and check that valid values are provided, reporting errors (and exiting) otherwise. When your program is started, parse these parameters with your library and then start the user interface with suitable parameters. For example, the program should read the cards from the file provided as command line argument and should flip the cards when `--invertCards` is provided. You should make your *RecentMistakesFirstSorter* from Task 1 available through this command line interface (this corresponds to the `"recent-mistakes-first"` option).  

If the program is called with the `--help` option, it should display a message similar to the one above and exit the program. It **does not** have to be exactly the same as the one we provide, but you should strive for something similar. A line at the top showing the usage of the command and listing all of the options with what they do is sufficient. You should look at the documentation for the library you choose to use as many provide functionality that helps you achieve this. 

Any combination of the options should be able to be applied at the same time; however, passing the `--help` flag with any other options should just display the help message and exit. Again, the library you use may provide you with a way to implement this functionality.

**All** of these options can be configured using the existing codebase, meaning you **do not need** to add any new functionality to the program. Rather, the only changes you need to make are to the program's dependencies and to its entry point, so that it functions as a command-line interface described above. All of your code for this task will therefore most likely be within `Main.java`. 

You are free to use any open source library on *Maven Central* for this project. There are many many choices with different levels of quality and documentation (e.g., [Apache Commons CLI](https://commons.apache.org/proper/commons-cli/), [jopt](https://github.com/jopt-simple/jopt-simple), [JArgs](http://jargs.sourceforge.net/)), explore them and pick one. Note, support and ease of use may be an important factor in choosing a library -- explore alternatives if a library is confusing, too complex, poorly documented, or uses language features you do not understand.

**Task 3: Additional Achievements.** There is already an implementation of one achievement, which is awarded if the user completes a round of questions with an average time less than 5 seconds per question.  Implement three more achievements, adding them to the AchievementType enum.  The achievements are specified as follows:

* CORRECT: all questions were answered correctly in the latest round
* REPEAT: at least one card has been answered more than 5 times
* CONFIDENT: at least one card has been answered correctly at least 3 times

**Infrastructure and quality requirements.** 

* Push all your code to GitHub using good practices (e.g., cohesive commits, descriptive commit messages). 
* Your code should compile and pass automated checks when executed with the build tool (`mvn site`). Your code should automatically be executed on [GitHub Actions](https://github.com/features/actions), a continuous integration service. Your build should succeed on GitHub Actions, however, GitHub Actions is not configured as an auto-grader for this assignment and does not perform any tests. Passing GitHub Actions is just a minimum bar, not a sufficient condition for completing the homework. You can find the results of the automated checks in the _Actions_ tab of your GitHub repository.
* Follow good design practices as discussed: Hide information where appropriate. Program against interfaces, not against classes.
* For all new code that you write, follow the [Java code conventions](https://www.oracle.com/java/technologies/javase/codeconventions-introduction.html). We have installed Checkstyle that will automatically check conformance to many style guidelines in your repository.
* If you add libraries, add them as *maven* dependencies. Do *not* copy library code into the repository.
* We will be testing your code by building a "fat JAR" with `mvn clean package`, and running it with `java -jar [your-executable] [argument-list]`. Please make sure that `mvn clean package` works with your code before you submit it.

**Hints.** The first labs cover some basics and best practices of working with Git and provides guidance on how to set up your development environment. The second lecture covers basic design principles for object-oriented design, especially encapsulation. The subsequent readings provides pointers to relevant language concepts, but you will probably need to engage with language documentation beyond the presented basic concepts yourself (for example, the provided code uses recent Java features). 

Descriptive commit messages are those where an experienced developer would be able infer what the scope of your changes is from just reading the commit message. Your commit messages do not necessarily need to explicity refer to files changed. They should describe the changes your commit will make in an imperative present tense sentence. Here are a few examples of descriptive commit messages: "Implement recent mistakes first sorter", "Fix CLI incorrectly handling repetitions", "Add documentation for recent mistakes first sorter". Avoid commit messages like "Finish Java" or "Add comments" as they don't have enough detail for someone to understand what exactly is being changed. 

In order to keep runtime minimum for the automated checks, all GitHub Action checks are run with a timeout of 2 minutes, which should be plenty of time to run the checks for this assignment. If you do run into an issue where your build fails and you think it was an internal GitHub issue with running the automated checks, you can manually rerun that test. If you go to the _Actions_ tab of your GitHub repository and click the failed build, at the top right you should see a button that says _Re-run all jobs_. Clicking that will rerun the test. If you still get a timeout issue even after this, try waiting a bit (maybe 15 minutes or so) then rerun again, or come to office hours.

## Submitting your work

Always push all code to GitHub. Once you have pushed your final code there and are done with the assignment, you should submit a link to your final commit on Canvas. A link will look like `https://github.com/CMU-17-214/<reponame>/commit/<commitid>`. You can get to this link easily when you click on the last commit (above the list of files) in the GitHub web interface. Paste this link into the text box on the assignment submission page located on Canvas and click submit. 

## Evaluation

The assignment is worth 150 points. We will grade the assignment with this rubric:

**New card organizer (25pt):**

- [ ] 10: The solution implements the above specification correctly and nothing more
- [ ] 5: The implementation is reasonably well documented, using the API documentation style of the language.
* [ ] 10: The implementation is well organized and does not expose unnecessary implementation details (encapsulation) and it programs against interfaces, not classes.
      

**Command-line processing (55pt):**

- [ ] 15: The implementation makes use of an external library, imported through a package manager.
- [ ] 20: The implementation parses and validates target files for card decks and all 4 options listed above. It rejects invalid options or arguments with an error message. Examples of invalid options or arguments include negative numbers for repetitions and organizers that don't exist or contain numbers.
- [ ] 20: The implementation responds correctly to the command-line options -- opens the right card deck, uses the right organization strategies, lists help, etc.

**Achievements (35pt):**
- [ ] 30: The solution implements the above specification correctly and nothing more (10 points for each achievement)
- [ ] 5: The implementation is reasonably well documented, using the API documentation style of the language.

**Infrastructure and style (35pt):**

* [ ] 10: The URL submitted to Canvas is in the specified format and links to a specific commit.
* [ ] 5: The build is executed and passes on GitHub Actions.
* [ ] 5: Most commits are reasonably cohesive
* [ ] 5: Most commit messages are reasonably descriptive
* [ ] 5: The Java code generally follows the Java style guidelines (e.g., as checked by CheckStyle)
* [ ] 5: The implementation is clean and concise. It does not introduce unnecessary variables or dead or out-commented code. 

