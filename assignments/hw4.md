# Homework 4: Design Improvement of Static Website Generator

In this assignment, you will work with an existing non-trivial code base that has several design flaws. This mirrors a common setting in practice where you will join a team that has already a code base to work with and that code base is not in the best shape but still needs to be extended and maintained. You will work to improve the design of the program without changing its behavior (known as refactoring). You will not fix all issues but will make some improvements to the code base. You will spend most of the time reading existing code and looking for design problems. For changes you make, you will justify your changes with the design vocabulary (design goals, principles, heuristics, patterns) introduced in class.

This assignment will give you more experience with critiquing object-oriented design and deliberately applying various design strategies, in a small and incremental fashion.

## Context 

**Static website generators.** Static website generators are tools that generate [static web pages](https://en.wikipedia.org/wiki/Static_web_page) from various inputs. It allows users to create and customize web pages without writing HTML code directly. This can be used for project pages but also for sophisticated content managment systems. At the same time, static web pages are cheap and easy to deploy and host and do not require a server that interprets code when serving web pages. For example, they can be hosted on [CMU web space](https://www.cmu.edu/computing/services/comm-collab/websites/awps/index.html). Commonly, the page is simply regenerated when any of the inputs change, possibly automated.

Static web sites have become very popular with [GitHub Pages](https://pages.github.com/). By default, GitHub uses [Jekyll](https://jekyllrb.com/) as a popular static web site generator, but [many other exist](https://staticsitegenerators.net/) and it can be easy to write a custom one.  Sometimes it is easier to write a new generator then try to work with the complexity or limitations of existing ones. For example, the 17214 web page was long generated with a custom static website generator, taking as input markdown files, a Google Doc spreadsheet with the schedule, and a directory with slides.

**The project.** In this homework, you take over a custom static website generator written to support a webpage for student clubs, that contain articles and events. The code is kind of functional, but not quite finished, and it is poorly designed in many ways. The original authors wanted to introduce events and a calendar and have written much code for it, but the complexity got out of hand so events never got finished. Also, nobody has worked on making the produced website look nice yet. Documentation is fairly sparse and there are no automated tests, just an example project.

The project roughly works like this: Everything is organized as a project (top-level directory). A project has a title and is owned by an organization, configured in a yaml file. Each directory represents an event or an article. Events and articles can have other events or articles within them.  Events or articles can have pictures and videos. They can be organized by topics (tags). Events have a name and a start and end date. The front page lists recent article/events and a calendar of upcoming events.

The project has three stages: a parser loads data ([markdown](https://daringfireball.net/projects/markdown/) files, [YAML](https://en.wikipedia.org/wiki/YAML) files, etc) from the disk (`parser` directory), the loaded data is represented as internal data structures (`project` directory), and finally, the content is written as HTML files (`rendering` directory) using a template engine. A command-line interface (`CLI`) coordinates all of this and can print summaries and statistics.



**Refactoring.** Refactoring is the improvement of code without changing its functionality. For example, to address the anti-pattern of a god class and improve cohesion of the implementation, a developer may decide to move methods from one class to another (and update all calls to the method). This change improves design but does not modify functionality; the same method will still be called, just in a different place. Many refactorings are done manually, but some can be automated by IDEs. Especially simpler things like renaming variables or extracting code to a new method are well supported, but even more complex operations like extracting an interface from a class or pushing methods along class hierarchies are implemented in some IDEs. It is usually a good idea to commit regularly as you refactor and make changes. If something goes wrong, you can always go back to the last commit.

**Relationship to real-world projects.** When joining a software engineering team in industry you almost always will join an existing project rather than starting from scratch. Most projects will be much much bigger than this one and documentation is rarely ever great. How much testing is done also differs widely between organizations. Reading existing code and understanding a subsystem without needing to know everything about every detail of the code is an important and very common skill. Research shows that software engineers in practice often spend much more than 50 percent of their time on understanding existing code rather than writing new code. Taking notes when reading the code or sketching UML diagrams or other diagrams of the structures in a program (usually informally and incompletely) is quite common to get an overview and understanding how pieces of a system fit together.

Real-world code often has design problems, where prior code was poorly written or the problem changed and the software has only been patched as necessary. This is usually true for other's peoples code and just as well for your own. Almost never does a team have the luxury of rewriting the entire system from scratch. Also nobody wants to do massive code changes of existing code out of fear of breaking existing functionality. Teams often even have a hard time getting permission to do minor improvements when management thinks they could work on new code instead (this has lead to an entire discussion around "[technical debt](https://en.wikipedia.org/wiki/Technical_debt)" as a way to get management to provide time for maintenance). In practice, it is much more common to do small and incremental design fixed as one continues to develop the system (boy scout rule ["leave your code better than you found it"](https://deviq.com/principles/boy-scout-rule)). Practitioners use automated refactorings a lot, but also do many manual ones. Sometimes a somewhat larger redesign might be necessary to enable new functionality, but also here it will usually only affect a small part of the system.

In this assignment, we intentionally will expect you to be very explicit about arguments why certain designs are bad and how they can be improved. In addition, we require you to create a partial object model for one of your fixes. While you may not write this all down in practice, sometimes you may need to make similar arguments to colleagues to argue why a specific change is beneficial (when it is always easier to leave the code as is). We provide guidance to look for specific kinds of design problems.

You will do multiple small design improvements and one slightly larger redesign to solve a specific problem ("SubSubSubSubSubArticles"). While not fully realistic, you will do design improvements without adding new functionality. You can consider this as a useful step for preparing for adding the new functionality for events in the future. 

## Design Problems

In this assignment, you will address one instance of each of the following design problems:

1. **Responsibility Assignment** -- fields or methods are in inappropriate places
2. **Code Duplication** -- duplicate code that could be abstracted and reused using methods, inheritance, delegation, or design patterns
3. **Coupling** -- unnecessary coupling
4. **Cohesion** -- objects, classes, or methods that severely violate cohesion (e.g., god class)
5. **Extensibility** -- unnecessarily difficult to extend code (i.e., extensions require modifications of existing methods, possibly in multiple places)
6. **Encapsulation** -- object/class violates encapsulation principles
7. **Instanceof** -- the use of `instanceof` is often an indication of a design problem
8. **SubSubSubSubSubArticles** -- the way nested articles are represented in the implementation is problematic

## Task

We provide you with both a Java implementation and a TypeScript implementation in branches of the starter repository. For this homework, **you can choose** which one you are working with. You can switch to the branch you'd like to work on by typing `git checkout <BRANCH>` into your terminal where `<BRANCH>` is either TypeScript or Java depending on which language you'd like to use for this assignment. By submitting a link to the final commit of your solution, we will see which one you worked on.


**Improve design.** Your task is to incrementally and in small steps improve the design and implementation of the project to make it easier to maintain and extend in the future. You do *not* need to implement new functionality. 

*Step 1:* Look for a design problem in the implementation that fits one of the design problems listed above. You will probably need to spend quite some time getting an overview of the code and understanding parts of it.

*Step 2:* Create a GitHub issue with the design problem in the title (e.g., "Fix coupling problem"). The issue text should point out a specific problem at a specific location in the code and explains *why* the specific code is problematic (e.g., why the coupling is bad in this specific case). We provide a GitHub issue template outlining this step that you may use when you open the issue.

*Step 3:* Fix the design problem and commit the fix with a meaningful commit message. 

*Step 4:* Close the issue with a message that explains *how* you fixed the issue and link the issue to the commit that fixed it. A fix may address multiple problems, and the same commit can be linked in multiple issues.

*Step 5:* Repeat the steps above until you have addressed all 8 design problems.

When done, we expect to find 8 closed issues in your repository.

You do not need to fix all design problems in the code but only a subset as needed for creating and closing 8 issues corresponding to the 8 design problems above. We expect that different students will fix different problems, and that different students will fix the same problem in different ways -- this is okay, as long as the fix improves the design problem and does not introduce new obvious problems.

**Document structure change.** For the "SubSubSubSubSubArticles" problem **only**, create a partial *object model* of the system *after* your fix. It should only involve the classes related to articles as needed to explain your fix. Make sure the diagram is consistent with your final implemented solution.

Commit the diagram as `sub-articles.pdf` in the root directory of the branch you are working on.

**Hints for design problems.** The code has many problems, often more than four problems of each kind. Several methods are really in the wrong place. Some methods clearly do a lot more work than they should and depend on knowing details of other objects. Lots of encapsulation violation throughout the code. The way topics are stored is weird. The way sorting is managed seems rather inflexible and repetitive. There is a lot of copy pasted code that could be abstracted, including several methods in several files and entire files. There are lots of `instanceof` checks that are a sign of possibly bad design. Some of these problems may benefit from using a design pattern, but for most problems a design pattern is not needed. Usually, reasoning with design heuristics and design principles is sufficient.

One part of the design seems particularly problematic: The way articles are nested is very hard to extend (design problem "SubSubSubSubSubArticles" above). There is one design pattern we discussed in lecture that would make this design much better, where the same operations can be applied to articles, subarticles, and content of those articles uniformly in a hierarchy. Making this change is nontrivial and will require changes to multiple code fragments where articles and their content is used. You can probably delete the SubArticle and SubSubArticle classes afterward. You may want to start with a few smaller problems to get familiar with the code base before getting to this one.

**Reusing design changes.** Note that some design fixes can address to multiple of the design problems above. For example, the fix to "SubSubSubSubSubArticles" will likely address multiple other design problems too. Hence it may be possible to close multiple issues with the same fix. Keep in mind that your explanations for why the design change you made fixed the issue will most likely need to be different. 

We expect that a typical solution will perform 4 to 6 refactorings to cover the 8 design problems.

**Excluded code.** Focus primarily on the data structures to represent the project (`project` directory) and how it is used by the `Renderer` and the `CLI`. You can ignore the parser (file `ProjectParser`). We also do not expect you to make any changes to the template engine (in file `TemplateEngine` and the `data` directory and `.hbs` and `.css` files) though you may need to understand what is generated here to understand other parts of the program. 


## Submitting your work

Always submit all your changes to GitHub. Once you have pushed your final code and the partial object model there, submit a link to your final commit on Canvas. A link will look like `https://github.com/CMU-17-214/<reponame>/commit/<commitid>`. You can get to this link easily when you click on the last commit (above the list of files) in the GitHub web interface. We expect to find (closed) issues in the repository you link to.

## Evaluation

The assignment is worth 110 points. We expect to grade the assignment approximately with this rubric:

- [ ] 20pt: The implementation was improved in some from. The improved implementation still compiles on GitHub Actions and provides the same functionality as the original implementation. Improvements like supporting deeper nesting of articles or supporting events are okay, but breaking the existing functionality is not. 
- [ ] 56pt: For each of the first 7 design problems  (responsibility assignment, code duplication, coupling, cohesion, extensibility, encapsulation, and instanceof; not "SubSubSubSubSubArticles"):
  - [ ] 4pt: There is an issue on GitHub that (a) names the design problem in the title, (b) identifies an instance of the problem in the code, and (c) explains *why* this is a problem. The issue's text demonstrates an understanding of the design problem.
  - [ ] 4pt: The issue is (a) closed with (b) a description of the fix and (c) a link to the commit(s) that contain the fix so that we can find the fix in the implementation. The change indeed improves the design as described without introducing new obvious design problems.
- [ ] 14pt: For "SubSubSubSubSubArticles": An issue (named "SubSubSubSubSubArticles" or similar) describes why the old implementation was problematic. The issue is closed with a link to the commit(s) that contain the fix and a description of how it was improved in a way that demonstrates an understanding of design reasoning and the used design pattern (if any). The fixed implementation better handles articles and subarticles with less code duplication and better implementations for common functionality like `getTopics`, `printSize`, and parent/child relationships. 
 - [ ] 10pt. The repository contains a partial object model in `sub-articles.pdf` in the root directory of your branch that describes the design fix for the "SubSubSubSubSubArticles" problem. It needs only include the classes involved with your fix. The diagram should be consistent with the actual implementation, use suitable notation, and be at the right level of abstraction.
- [ ] 10pt: The Git commits are cohesive and have meaningful descriptions that indicate what fix they are part of. The changes did not introduce severe style or readability issues. 

*If the submitted link does not have the right format, we will not be able to grade your solution and will assign 0 points.*



## Appendix: Technical Hints


**Viewing the webpage.**  The code can be executed with the provided sample project which executes most of the functionality of the project. To make this easier, we set up `mvn exec:exec` / `npm run example` to execute the program with arguments `-d testProject --list-articles --all --list-events --topics --clean --size` which executes most code of the project. Of course, you can also run the program from within your IDE using a configured launch.json with these arguments. These commands generate a directory called `_static` by default that contains all the HTML and CSS files to render the webpage.

When you initialize the starter repository, we recommend that you generate the webpage with the initial code and rename that directory (to e.g. `_static_original`), so you can have a reference to the original webpage. Refer to the [Testing Section](#testing) for the commands to re-generate the webpage directory as you refactor and ensure the new output is the same as the original. If you begin refactoring without doing so and want a reference, you can check out the initial commit and generate the webpage with the starter code. 

To view the webpage, go to the directory and open `index.html`. From VSCode, you can either click on 'Open in Default Browser' or 'Copy Path' and paste that into the address bar of your browser.


**Testing.** The project does not have any automated tests and you do not need to write any. To test that your fixes did not break the functionality of the project, you can compare the output produced by the program after your changes to the directory generated by the original code. While comparing the output on one example is not guaranteeing that the refactoring is behavior-preserving for all inputs, it provides assurance that nothing obvious was broken. To do this comparison, use a `diff` tool to compare the old generated output with the new one. Similarly you can save the command-line output into a file and compare the output before and after a fix. We recommend to perform the diff with  `diff -r -I 'class="date">' -I 'class="created-date">' -I "last updated" _static _static_original` (where `static_original` is the renamed original directory) in your command line to display any differences in the output of the program, while ignoring timestamp differences in the output. If no functionality was changed, there will be no output from this diff command. In addition, opening the `index.html` file for each the of the generated directories in your browser and visually comparing them is a quick way to help confirm the website generates properly. 
