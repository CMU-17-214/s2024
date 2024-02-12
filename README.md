# Principles of Software Construction <small>Objects, Design, and Concurrency</small>


## Overview

Software engineers today are less likely to design data structures and algorithms from scratch and more likely to build systems from library and framework components. In this course, students engage with concepts related to the construction of software systems at scale, building on their understanding of the basic building blocks of data structures, algorithms, program structures, and computer structures. The course covers technical topics in four areas: (1) concepts of design for complex systems, (2) object oriented programming, (3) static and dynamic analysis for programs, and (4) concurrent and distributed software. Student assignments involve engagement with complex software such as distributed massively multi-player game systems and frameworks for graphical user interaction.

After completing this course, students will:

- Be comfortable with object-oriented concepts and with programming in the Java or JavaScript language
- Have experience designing medium-scale systems with patterns
- Have experience testing and analyzing your software
- Understand principles of concurrency and distributed systems

See a more detailed list of [learning goals](https://cmu-17-214.github.io/s2024/learninggoals.html) describing what we want students to know or be able to do by the end of the semester. We evaluate whether learning goals have been achieved through assignments and exams.

### Coordinates

Tu/Th 3:30 - 4:50 p.m. in WEH 7500

**[Jonathan Aldrich](https://www.cs.cmu.edu/~aldrich/)**, [TCS](https://www.covidcast.cmu.edu/visit/july-2021-campus-map) 422, office hours: see calendar

**[Charlie Garrod](https://www.cs.cmu.edu/~charlie/)**, [TCS](https://www.covidcast.cmu.edu/visit/july-2021-campus-map) 343, office hours: see calendar

**[Jeremy Lacomis](https://jeremylacomis.com/)**, [TCS](https://www.covidcast.cmu.edu/visit/july-2021-campus-map) 362, office hours: see calendar

Our TAs also provide an additional 15h of office hours each week; see details in the calendar.

The instructors have an open door policy: If the instructors' office doors are open and no-one else is meeting with us, we are happy to answer any course-related questions. Feel free to email us for appointments; we are also available over Zoom.

## Course Calendar
<iframe src="https://calendar.google.com/calendar/embed?src=c_81425b8a812ec3cfa08032ac52af2234d7a6a4f99f01ea991f1290c354fdf8ea%40group.calendar.google.com&ctz=America%2FNew_York" style="border: 0" width="800" height="600" frameborder="0" scrolling="no"></iframe>

## Schedule

The schedule below reflects our current plans, but will be updated throughout the semester.



<div id="schedule">
<table>
  <thead>
    <tr>
      <th>Date</th>
      <th>Topic</th>
      <th style="width: 30%">Reading assignments*</th>
    </tr>
  </thead>
  <tbody>
    <tr class="">
      <td>Tue, Jan 16</td>
      <td><a href="https://docs.google.com/presentation/d/1w53j54X7w8TOMeESE997axKLSGXoH3svhZMr9QY_YmQ/edit?usp=sharing">Introduction</a></td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Jan 17</td>
      <td><span class="rec">Lab 1</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/labs/lab01.md">Course Infrastructure Setup</a></td>
      <td></td>
    </tr>
    <tr class="">
      <td>Thu, Jan 18</td>
      <td><a href="https://docs.google.com/presentation/d/1b2Gv-uoAGUH-mvDk8-N4xskyNH1ijsDLnpJiDEH1dqk/edit?usp=sharing">OO basics, Dynamic dispatch, Encapsulation</a>; <a href="https://github.com/CMU-17-214/s2024/blob/main/examples/lect02simulation.zip">example code</a></td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr class="">
      <td>Tue, Jan 23</td>
      <td><a href="https://docs.google.com/presentation/d/16strBWb06qITlgkmWNDpAA8eS5QhACqLVxINcVZAQDI/edit?usp=sharing">IDEs, Build system, Continuous Integration, Libraries</a></td>
      <td>Required: <a href="https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/1feg4j8/alma991019578256404436">Effective Java, Items 15 and 16</td>
    </tr>
    <tr>
      <td>Wed, Jan 24</td>
      <td><span class="rec">Lab 2</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/labs/lab02.md">Encapsulation</a></td>
      <td></td>
    </tr>
    <tr class="">
      <td>Thu, Jan 25</td>
      <td><a href="https://docs.google.com/presentation/d/1t6OKuap0bjrd4ikglvhaYD6jOEubugm5oPjW7vWiybE/edit?usp=sharing">Specifications and Unit Testing, Exceptions</a></td>
      <td>Recommended: <a href="https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/1feg4j8/alma991000042699704436">Java Precisely</a> (Ch 3, 4, 9, 10, 11); <a href="https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/6lpsnm/alma991019576570404436">JavaScript: The Good Parts</a> (Ch. 3, 4, 9), <a href="https://www.typescriptlang.org/docs/handbook/intro.html">TypeScript Handbook</a> (Basics, Everyday Types, Object Types)</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Mon, Jan 29</td>
      <td><span class="assignment"><span class="hw">HW 1 due</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/assignments/hw1.md">Flash cards</a> (Intro to OO and Libraries)</td>
      <td></td>
    </tr>
    <tr class="">
      <td>Tue, Jan 30</td>
      <td><a href="https://docs.google.com/presentation/d/1Vc7WytEPcEWJ-KFT1jnfTBjzMe5NKmn1it7VV75cSu8/edit?usp=sharing">Test case design</a></td>
      <td><a href="https://www.testim.io/blog/unit-testing-best-practices/">Unit Testing Best Practices</td>
    </tr>
    <tr>
      <td>Wed, Jan 31</td>
      <td><span class="rec">Lab 3</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/labs/lab03.md">Unit testing</a></td>
      <td></td>
    </tr>
    <tr class="">
      <td>Thu, Feb 1</td>
      <td><a href="https://docs.google.com/presentation/d/1OBWr1jR9SG3twSKwRmhl0gC4V4aLb_0HxHYmr8xRFNk/edit?usp=sharing">Object-oriented analysis and UML</a></td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Mon, Feb 5</td>
      <td><span class="assignment"><span class="hw">HW 2 due</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/assignments/hw2.md">Testing</a> </td>
      <td></td>
    </tr>
    <tr class="">
      <td>Tue, Feb 6</td>
      <td><a href="https://docs.google.com/presentation/d/1HxO1VkY-ly0NAG2rC9faaJS2iaAuab-Va5qC87mAcf0/edit?usp=sharing">Responsibility assignment</a></td>
      <td><a href="https://www.safaribooksonline.com/library/view/applying-uml-and/0131489062">UML and Patterns</a>, Ch. 9-11, 15-16</td>
    </tr>
    <tr>
      <td>Wed, Feb 7</td>
      <td><span class="rec">Lab 4</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/labs/lab04.md">Design and UML</a></td>
      <td></td>
    </tr>
    <tr class="">
      <td>Thu, Feb 8</td>
      <td><a href="https://docs.google.com/presentation/d/1MqJ7VS2kpO5kltwyBKqirs0bWl3JuFO1vHGFmF5glVA/edit?usp=sharing">Design for Reuse: Inheritance and Composition</a></td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Tue, Feb 13</td>
      <td>Design Patterns</td>
      <td><a href="https://www.safaribooksonline.com/library/view/applying-uml-and/0131489062">UML and Patterns</a>, Ch. 17-18</td></td>
    </tr>
    <tr class="">
      <td>Wed, Feb 14</td>
      <td><span class="rec">Lab 5</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/labs/lab05.md">Inheritance and Delegation</a></td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Feb 15</td>
      <td>Refactoring and Anti-patterns</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Mon, Feb 19</td>
      <td><span class="assignment"><span class="hw">HW 3a due</span> <a href="https://github.com/CMU-17-214/s2024/blob/main/assignments/hw3.md">Santorini: Intro to Design</a></td>
      <td></td>
    </tr>
    <tr class="">
      <td>Tue, Feb 20</td>
      <td>Introduction to GUIs and Concurrency</td>
      <td><a href="https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/1feg4j8/alma991019576375404436">Design Patterns Explained</a> or <a href="https://refactoring.guru/design-patterns/catalog">Refactoring Guru</a> on Observer and Decorator</td>
    </tr>
    <tr>
      <td>Wed, Feb 21</td>
      <td><span class="rec">Lab 6</span> Anti-patterns and Refactoring</td>
      <td></td>
    </tr>
    <tr class="midterm">
      <td>Thu, Feb 22</td>
      <td class="midterm">Midterm 1</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Mon, Feb 26</td>
      <td><span class="assignment"><span class="hw">HW 3b due</span> Santorini: Design feedback</td>
      <td></td>
    </tr>
    <tr>
      <td>Tue, Feb 27</td>
      <td>Asynchrony in JavaScript</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Feb 28</td>
      <td><span class="rec">Lab 7</span> GUI intro</td>
    </tr>
    <tr>
      <td>Thu, Feb 29</td>
      <td>Concurrency and Hazards</td>
      <td><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop">Concurrency model and the event loop</a> + <a href="https://blog.sessionstack.com/how-javascript-works-event-loop-and-the-rise-of-async-programming-5-ways-to-better-coding-with-2f077c4438b5">How JavaScript works</a></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Tue, Mar 5</td>
      <td class="break">No class, Spring Break</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Mar 6</td>
      <td class="break">No lab, Spring Break</td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Mar 7</td>
      <td class="break">No class, Spring Break</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Tue, Mar 12</td>
      <td><span class="assignment"><span class="hw">HW 4 due</span> Refactoring</td>
      <td></td>
    </tr>
    <tr>
      <td>Tue, Mar 12</td>
      <td>Concurrency: Reactive Programming</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Mar 13</td>
      <td><span class="rec">Lab 8</span> Concurrency & Promises</td>
      <td></td>
    </tr>
    <td>Thu, Mar 14</td>
      <td>Distributed Systems -- Events everywhere</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Mon, Mar 18</td>
      <td><span class="assignment"><span class="hw">HW 3c due</span> Santorini: Final design</td>
      <td></td>
    </tr>
    <tr>
      <td>Tue, Mar 19</td>
      <td>Design for Robustness & Distributed Systems</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Mar 20</td>
      <td><span class="rec">Lab 9</span> ReactJS</td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Mar 21</td>
      <td>Libraries and Frameworks</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Mon, Mar 25</td>
      <td><span class="assignment"><span class="hw">HW 5 due</span> Concurrency</td>
      <td></td>
    </tr>
    <tr>
      <td>Tue, Mar 26</td>
      <td><bf>TBD</bf></td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Mar 27</td>
      <td><span class="rec">Lab 10</span> Test Double (Fakes, Mocks & Stubs)</td>
      <td></td>
    </tr>
    <tr class="midterm">
      <td>Thu, Mar 28</td>
      <td class="midterm">Midterm 2</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Tue, Apr 2</td>
      <td>API Design</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Apr 3</td>
      <td><span class="rec">Lab 11</span> Frameworks/Extensibility</td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Apr 4</td>
      <td>Organizing Systems at Scale: Modules</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Tue, Apr 9</td>
      <td><span class="assignment"><span class="hw">HW 6a due</span> Santorini: User Interface</td>
      <td></td>
    </tr>
    <tr>
      <td>Tue, Apr 9</td>
      <td>TBD</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Apr 10</td>
      <td class="break">No lab, Carnival</td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Apr 11</td>
      <td class="break">No class, Carnival</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Tue, Apr 16</td>
      <td>Supply Chain Security and Sustainability</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Apr 17</td>
      <td><span class="rec">Lab 12</span> Cloud Deployment</td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Apr 18</td>
      <td>Static vs dynamic typing, static analysis</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td>Tue, Apr 23</td>
      <td>DevOps</td>
      <td></td>
    </tr>
    <tr>
      <td>Wed, Apr 24</td>
      <td><span class="rec">Lab 13</span> Design Pattern Review</td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Apr 25</td>
      <td><span class="assignment"><span class="hw">HW 6b due</span> Santorini: God Cards</td>
      <td></td>
    </tr>
    <tr>
      <td>Thu, Apr 25</td>
      <td>Finale: Toward SE, Teams, Process</td>
      <td></td>
    </tr>
  </tbody>
  <tbody>
    <tr class="midterm">
      <td>TBD</td>
      <td>Final exam</td>
      <td></td>
    </tr>
  </tbody>
</table>
</div>


## Course Staff

Instructors: [Jonathan Aldrich](https://www.cs.cmu.edu/~aldrich/) [aldrich], [Charlie Garrod](https://www.cs.cmu.edu/~charlie/) [cgarrod], and [Jeremy Lacomis](https://jeremylacomis.com/) [jlacomis]

TAs: Aditya Kumar Mittal [akmittal],
Eileen Weizhen Xiao [ewxiao],
Jeffrey Hanyun Li [jhl4],
Jiaye Liu [jiayeliu],
Terry (Jielin) Li [jielinl],
Rajath Mahendrappa Kotyal [rajathmCMU],
Sitong Shang [sitongs],
Wenjun Zhou [wejunz2],
Yikang Cheng [yikangc],
Zhewei Tong [zheweit]

## **Course Syllabus and Policies**

### **Prerequisites**

- 15-122 or 15-211, or equivalent with instructor's permission
- The equivalent of 2 semester-long programming classes
  - Ability to write small programs in C (or Java, C#, or other imperative languages with pointers or references)
  - Ability to reason about programs using preconditions, postconditions, and invariants
  - Familiarity with a basic set of algorithms and data structures (linked lists, simple graph and sorting algorithms)

- 15-151 or 21-127, or equivalent with instructor's permission
  - Sound foundation of mathematical concepts; ability to reason formally




------



### **Grading** **and Deadlines**

Evaluation will be based on the following approximate percentages:

- 50% assignments
- 30% midterm exams and final exam
- 10% labs
- 10% participation and quizzes

This course does not have a fixed letter grade policy; i.e., the final letter grades will **not** be A=90-100%, B=80-90%, etc.

**Homework grading and regrading.** We try to be transparent in our rubrics in our assignments. Feel free to ask instructors or TAs clarification questions about the rubrics before the assignment is due. If you disagree with a grade, please submit a regrade request within 7 days on Gradescope. Regrade requests need a justification, explaining why our assessment is inconsistent with the rubric. Regrade requests without such justification will be closed.

Each student can *resubmit* any *one* assignment milestone and it will be regraded as if it was the first submission (see below).

**Participation and quizzes.** You should expect a quiz at the start of nearly every lecture and often additional in-class activities within the lecture. When a reading assignment is given, the quiz will typically touch on the content from the reading material. Otherwise (and sometimes in addition), the quiz centers around the content from the most recent lecture or two. A quiz will typically have 1-2 questions and is graded pass/fail.

**Labs.** Labs will be graded on a pass/fail basis during recitations. You will have a chance during recitation to improve your solution. See a description [here](https://github.com/CMU-17-214/s2024/blob/main/labs.md).

**Late work.** We understand that normal life events, including projects and exams in other courses and technical difficulties out of your control, can interfere with your ability to complete your work on time or attend lectures and recitations. Our philosophy is that our late work policy includes built-in flexibility but that the policy will be uniformly applied to all students in all circumstances. Exceptions to this policy will be made only with explicit accommodations, almost always involving a family or medical emergency with your academic advisor or the Dean of Student Affairs requesting the exception on your behalf.

We provide the following flexibility, no questions asked, no justification needed:

- For midterms and finals, we drop the worst of the three grades.
- For quizzes, we will drop up to four missed/failed solutions during the semester.
- For labs, we will drop up to four missed/failed solutions during the semester.
- For homework deadlines you have 5 free late days for the semester. You can exceed each deadline by up to three days (unless explicitly specified otherwise in the assignment, check carefully), for a penalty of 10% per day once you run out of free late days. Note that some homework assignments have multiple milestones with separate deadlines; there are typically around 9 homework deadlines in a semester – late days are assessed for each deadline independently.
- For a single homework deadline during the semester, you can redo and resubmit your work after it was graded. It will be regraded as if it was the first submission and you can regain all lost points. Each student can only do this once. We accept resubmissions until April 26th, 11:59pm. (While we do not recommend it, you can use this as arbitrary late days for a single deadline, receiving 0 points for missing the initial deadline and then resubmitting later).

Any work submitted beyond the flexibility provided by these mechanisms will receive feedback but no credit unless explicit accommodations were provided.



------



### **Attendance and remote participation**

This course, including recitations, is marked by the registrar as IPE ("delivered in-person, students are expected to be in the classroom during the course's scheduled meeting time"). We do not plan to make accommodations for remote attendance.

We strongly recommend attending lectures. We have regular in-class activities and quizzes that we expect you to complete in class. Attending recitations is required for grading labs.

In case of illness, quarantine, or other exceptional circumstances, we may be able to share recordings of lectures upon request on a case by case basis. Recordings may not be shared to protect the FERPA rights of all students in the classroom.



------



### **Textbooks**

This course will occasionally assign **mandatory readings**, from the two text books below. The CMU library has both physical and electronic copies of these books. You can access *all* of these books for free electronically through the CMU library.

- Larman, Craig. [*Applying UML and Patterns: An Introduction to Object-Oriented Analysis and Design and Iterative Development*](https://bookshop.org/books/applying-uml-and-patterns-an-introduction-to-object-oriented-analysis-and-design-and-iterative-development/9780131489066), 3rd Edition. Prentice Hall. ISBN 0-13-148906-2. [[CMU Library](https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/6lpsnm/alma991019576227704436)] This book describes basics of object-oriented design, responsibility assignment, and some design patterns used in the course. We will use the third edition, which covers the course's topics in more details than earlier editions. We will assign select chapters.
- Bloch, Joshua. [*Effective Java*](https://bookshop.org/books/effective-java-9780134685991/9780134685991), Third Edition. Addison-Wesley, ISBN 978-0-13-468599-1. [[CMU Library](https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/1feg4j8/alma991019578256404436)] This book covers many aspects of program design, not only those specific to Java. We will assign multiple chapters.

In addition, we list **several optional readings** that may be helpful with specific topics in the course. Especially if Java/Javascript is new to you, you might want to consider exploring additional books.

- Object-Oriented Design and Design Patterns
  - Alan Shalloway and James Trott. [*Design Patterns Explained: A New Perspective on Object-Oriented Design (2nd Ed.)*](https://bookshop.org/books/design-patterns-explained-a-new-perspective-on-object-oriented-design/9780321247148) [[CMU Library](https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/1feg4j8/alma991019576375404436)]
  - Gamma et al. [*Design Patterns: Elements of Reusable Object-Oriented Software*](https://bookshop.org/books/design-patterns-elements-of-reusable-object-oriented-software/9780201633610). Addison Wesley. ISBN 0-201-63361-2 [[CMU Library](https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/6lpsnm/alma991019576613104436)] (this is an excellent book, but more of a reference text than the *Design Patterns Explained* book. In addition, because it was the original patterns book, the examples are in C++ and Smalltalk, not Java)

- Java
  - *Note: Here are some popular textbook and online resources for learning Java.*
  - Sestoft. [*Java Precisely*](https://bookshop.org/books/java-precisely-third-edition/9780262529075). MIT Press, 2016. [[2nd edition in the CMU library](https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/1feg4j8/alma991016506989704436)] (this is a very concise reference with many good examples; it assumes that you already know other programming languages)
  - [Introduction to Programming Using Java](http://math.hws.edu/javanotes/) (free online textbook)
  - [Blue Pelican Java](http://www.bluepelicanjava.com/) (free online textbook)

- Javascript/Typescript
  - Douglas Crockford. [JavaScript: The good parts](https://bookshop.org/books/javascript-the-good-parts-the-good-parts/9780596517748). O'Reilly, 2008. [[CMU library](https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/6lpsnm/alma991019576570404436)]
  - Boris Cherny. [Programming Typescript: Making Your JavaScript Applications Scale](https://bookshop.org/books/programming-typescript-making-your-javascript-applications-scale/9781492037651). O'Reilly, 2019. [[CMU library](https://cmu.primo.exlibrisgroup.com/permalink/01CMU_INST/6lpsnm/alma991019642791104436)]




------



### **Time management**

This is a 12-unit course, and it is our intention to manage it so that you spend close to 12 hours a week on the course, on average. In general, 4 hours/week will be spent in class, 1 hour on labs, and 7 hours on assignments. Please feel free to give the course staff feedback on how much time the course is taking for you.



------



### **Research to Improve the Course:**

For this class, we are conducting research on teaching and learning. This research will involve some student work. You will not be asked to do anything above and beyond the normal learning activities and assignments that are part of this course. You are free not to participate in this research, and your participation will have no influence on your grade for this course or your academic career at CMU. If you do not wish to participate, please send an email to Chad Hershock (hershock@andrew.cmu.edu). Participants will not receive any compensation. The data collected as part of this research will include student grades. All analyses of data from participants’ coursework will be conducted after the course is over and final grades are submitted. The Eberly Center may provide support on this research project regarding data analysis and interpretation. The Eberly Center for Teaching Excellence & Educational Innovation is located on the CMU-Pittsburgh Campus and its mission is to support the professional development of all CMU instructors regarding teaching and learning. To minimize the risk of breach of confidentiality, the Eberly Center will never have access to data from this course containing your personal identifiers. All data will be analyzed in de-identified form and presented in the aggregate, without any personal identifiers. If you have questions pertaining to your rights as a research participant, or to report concerns to this study, please contact Chad Hershock (hershock@andrew.cmu.edu).



------



### **Collaboration policy and academic integrity**

The usual policies apply, especially the University Policy on Academic Integrity. We expect that your work on assignments, projects, and exams will be your own work. The key guiding principle of academic honesty in this course is: *"You may not copy any part of a solution to a problem that was written by another student (in this or prior iterations of the class), or was developed together with another student, or was delegated to another person. You may not look at another student's solution, even if you have completed your own, nor may you knowingly give your solution to another student or leave your solution where another student can see it."* Note that this implies that you cannot publicly post your solutions on GitHub (e.g., as part of a portfolio during job applications). We also expect and respect honesty when communicating with the course staff.

Any violation of this policy is cheating. We use automated systems to detect software plagiarism. These automated systems are highly effective and, so far, have detected software plagiarism almost every semester. The minimum penalty for cheating will be a zero grade for the whole assignment. Cheating incidents will also be reported through University channels, with possible additional disciplinary action (see the University Policy on Academic Integrity).

For labs and homeworks you are allowed to use various tools and help available to professional programmers, such as online documentation, online tutorials and support forums like Stackoverflow, and AI assistants like Copilot and ChatGPT. You are allowed to post technical questions about aspects of the homework elsewhere, as long as you do not ask other humans to complete the work for you. Whenever you use external resources like this, you are still fully responsible for the correctness of your solution and complying with licenses. Note that content generation tools often create plausible-looking but incorrect answers, which will not receive credit.

When you use AI assistants in homework, some assignments may require you to briefly describe their use and your experience with the homework submission.

Here are some examples of behavior that are inappropriate:

- Copying (or retyping) files, parts of files (such as source code, written text, or unit tests), quiz solutions, or exam solutions from another person or source, either in draft or final form, even if the file permissions are incorrectly set to allow it. This behavior is still clearly inappropriate even if you make modifications (such as style changes or minor logic modifications) from the original source.
- Searching for or viewing a current or past student's homework solution.
- Allowing someone else to view or copy your code, written assignment, quiz, or exam, either in draft or final form.
- Writing, using, or submitting a program that attempts to alter or erase grading information or otherwise compromise security of course resources.
- Lying to course staff.
- Making your work publicly available in a way that other students (current or future) can access your solutions, even if others’ access is accidental or incidental to your goals.

Here are some examples of acceptable behaviors:

- Solve technical problems by searching for the error message with Google or on StackOverflow.
- Copying code snippets from tutorials or StackOverflow into your own code.
- Importing libraries as part of your implementation. Reading documentation and examples of libraries. Copying libraries or utility files into your repository (bad practice to avoid, but not consider cheating).
- Copying code from labs or reference solutions provided in recitations.
- Using GitHub Copilot while writing your solution.
- Using ChatGPT to write or help write justifications in homework assignments, while checking the correctness of the answer.
- Looking at other students' solutions when explicitly instructed by the course staff, for example, as part of peer grading for labs, quizzes, or homework.

There is no statute of limitations for violations of the collaboration policy; penalties may be assessed (and referred to the university disciplinary board) after you have completed the course, and some requirements of the collaboration policy (such as restrictions on you posting your solutions) extend beyond your completion of the course.

If you have any question about how this policy applies in a particular situation, ask the instructors or TAs for clarification.



------



### **Audit Policy**

If you desire to audit the course, our general requirement is that you complete homeworks to achieve at least 50% of the total homework grade. Solutions do not need to be fully complete, but we encourage you to attempt to do so. We additionally encourage you to attend lectures and complete labs, but you are not required to do so. You should not attend our midterm exams or final exam.



------



### **Your health matters**

When we say "your health matters" we mean exactly that: Your health matters. We don't intend to imply that other peoples' health does not matter, or that your health matters more or less than theirs. We know that CMU can be a stressful, risky environment, and *your* health is the health that is relevant in this conversation. Worries about Covid-19 and possible remote classes do not help.

**Please take care of yourself**. Do your best to maintain a healthy lifestyle this semester by eating well, exercising, avoiding drugs and alcohol, getting enough sleep and taking some time to relax. This will help you achieve your goals and cope with stress.

All of us benefit from support during times of struggle. You are not alone. There are many helpful resources available on campus and an important part of the college experience is learning how to ask for help. Asking for support sooner rather than later is often helpful.

If you or anyone you know experiences any academic stress, difficult life events, or feelings like anxiety or depression, we strongly encourage you to seek support. Counseling and Psychological Services (CaPS) is here to help: call 412-268-2922 and visit their website at http://www.cmu.edu/counseling/. Consider reaching out to a friend, faculty or family member you trust for help getting connected to the support that can help.

If you are worried about affording food or feeling insecure about food, there are resources on campus who can help. Email the CMU Food Pantry Coordinator to schedule an appointment: cmu-pantry@andrew.cmu.edu

**Respect for diversity.** It is our intent that students from all diverse backgrounds and perspectives be well served by this course, that students’ learning needs be addressed both in and out of class, and that the diversity that students bring to this class be viewed as a resource, strength and benefit. It is my intent to present materials and activities that are respectful of diversity: gender, sexuality, disability, age, socioeconomic status, ethnicity, race, and culture. Your suggestions are encouraged and appreciated. Please let us know ways to improve the effectiveness of the course for you personally or for other students or student groups.

**Accommodations for students with disabilities.** If you have a disability and have an accommodations letter from the Disability Resources office, we encourage you to discuss your accommodations and needs with us as early in the semester as possible. We will work with you to ensure that accommodations are provided as appropriate. If you suspect that you may have a disability and would benefit from accommodations but are not yet registered with the Office of Disability Resources, we encourage you to contact them at access@andrew.cmu.edu.



------



### **Informal feedback on this course**

We are planning many changes to this course in this semester and not everything will work out smoothly the first time. We’d like you to provide ongoing feedback on your experience in the course, so that we can take into account your experience and adapt our practices to make the course work for you.

Outside of the regular course meetings and Piazza, you can submit feedback about anything in the course per email to the instructors or ask TAs to forward them anonymously. We will read every message submitted and use your feedback to try to improve the way we are teaching.
