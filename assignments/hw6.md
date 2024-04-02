
# Homework 6: Return to Santorini


In this final assignment, we return to Santorini and implement a user interface and god cards. This assignment has two milestones. 


* Provide a web-based *user interface* for people to play the game (both players share a screen) with React.
* Make your implementation *extensible* to support god cards in Java. You will update your design and provide implementations for three god cards.

You will continue with your Santorini code from Homework 3 in the same repository. We recommend to update your implementation and design documents based on feedback received for HW3, as fixing design issues will make it easier to extend the program and we will grade extended versions of these again, as described below. If you like you can create a new branch for this assignment. 



## Milestone 6a: User Interface

Implement a web-based user interface for the game in React. The user interface should be functional, allowing two players (sharing a screen) to select the initial spots for their workers, and to play the game taking moves and build actions until one player wins. You can also allow two users connect to the same server from different browsers for a match, but this is not required and would be more difficult to implement.


Generally, we leave details of the user interface to you. The user interface can be very simple. A five-by-five grid of buttons is likely sufficient with a button panel on the side for skipping optional actions and starting a new game. In the simplest case, you can represent workers by letters and towers with symbols on each button, e.g., `[[ ]]` for an empty level two tower, `[ X ]` for a tower with a worker from player *X*, and `[[[O]]]` for a tower with a dome. Background colors might indicate the active worker or valid locations for the next move or build. Text above the grid might indicate whose turn it is and what the next action is or who won. We do not grade for how pretty the game is.

In this homework, we are requiring you to implement the user interface using React. We recommend a client-server solution where a React frontend communicates over JSON with your Java backend. For a client/server design, you need to design and make API calls to your backend: The backend will provide a response to the frontend (most likely to be the current game states), and then the frontend will update its user interface based on the response. We have no restriction on which frameworks or libraries can be used, but we ask you to use React for at least some of your frontend code.

**Design requirements:** Decouple the user interface from the core game. That is, the core game should not have any dependency on parts of the user interface, where the backend API (e.g., NanoHTTP, express) is considered as part of the user interface. A simple way to test this is to check that the core implementation compiles and passes tests when all GUI code is deleted. 

Decide deliberately what state should be stored in the game and what state is managed by the GUI code; decide deliberately where actions/inputs are validated. Decompose the frontend into cohesive React components/functions. 

**Infrastructure requirements:** Extend your GitHub Actions to compile all code (in two steps as Homework 5 if needed) and run your tests. You do *not* need to write automated tests for the user interface (but you are welcome to try). You might want to write tests for the backend API.

**Documentation requirements:** In your `README.md` add a section "Starting a Game" that explains how to start the game from the command line (e.g., what sequence of maven or npm commands do we need to call). Ideally the game's user interface is self-explanatory (e.g., explains what logos mean, has textual instructions on what to do next), but if it is not clear how to play the game for *somebody who knows the rules*, explain this in the README too.




## Milestone 6b: God Cards

Redesign the game to support god cards according to the rules of the game. As described in the rules of the game, each player can pick a god card which modifies possible actions, winning conditions, or other aspects of the game. The game should be designed to be easily extensible for different god cards. This will require that you plan in the base code to make state available to implementations of god cards and allow god cards to change the behavior of the base game. For example, you may want to provide extension points to extend the implementation of what is considered a valid move, to modify what action a player can take next, or to store additional state. In a good extensible implementation of the game, god cards can be implemented with few lines of code each and minimal coupling.

You also need to extend your UI to support users to play with and without God Cards.

**Required god cards:** Implement the following four god cards to demonstrate that your system is extensible: Demeter, Hephaestus, Minotaur, and Pan. 

* **Demeter**: Your Worker may build one additional time, but not on the same space. 
* **Hephaestus:** Your Worker may build one additional block (not dome) on top of your first block. 
* **Minotaur**: Your Worker may move into an opponent Worker’s space, if their Worker can be forced one space straight backwards to an unoccupied space at any level.
* **Pan**:  You also win if your Worker moves down two or more levels. 

UI hint for Demeter and Hephaestus: You will likely need a way to indicate that the player wants to skip the optional second build, e.g., with a "pass" button or by clicking on the worker's current location.

**Design requirement:** In your implementation, the god cards must be entirely decoupled from the base game. The GUI can set up god cards by passing them to the game or wrapping game objects. The base game should not refer to any concepts of specific God cards or store specific state for the god cards. For example, the base game should not use `if (player.hasAtlasGod) (...)` within `Board.isValidMove(...)`. Of course the god cards can interact with the base game, call functions, register callbacks, and so forth. 

You should expect that you may need to substantially revise your base game design to make the game extensible. A good initial design will make this easier.

**Design documentation and justification:** Revisit the design documentation and justification from Homework 3 to make the following updates.

* **Update domain analysis:** Extend your domain model, system sequence diagram, and behavior contracts in `domain-model.pdf`, `system-sequence-diagram.pdf`, `contract.pdf` to include the new concept of god cards in the game. To keep things simple, you do not need to show all cards. For these three documents, it is sufficient to just include the god card *Minotaur* as a single concrete example. For the contract you can assume that *the active player has the Minotaur card* and the opposing player has no card.
* **New justification for extension mechanisms:** Explain in about one paragraph how you redesigned your game to be extensible. In addition, as in Deliverable 5 and 6 of Homework 3, provide a justification with reference to design goals/principles/heuristics/patterns and discuss alternatives you considered and tradeoffs you made. If you used design pattern(s) explain which you used and why you used them, if you did not use any design patterns explain why not. Turn this in as a new `extension-justification.pdf` file.
* **Updated object model:** Update your object model in `object-model.pdf` to reflect your extension mechanisms and the *Demeter* card.
* **Update justification for building action:** Extend your discussion in `build-justification.pdf` of how the game validates and performs a build action assuming that *the active player has the Demeter card* and the opposing player has no card. Update both the justification and the object-level interaction diagram.

You do not need to include any GUI-related code in the models. You do not need to update `state-justification.pdf`. We will grade the design documents with a similar rubric to Homework 3, so if you have unaddressed grading feedback, you might want to take this into consideration when refining the documents.

**Testing:**  Also update your test suite to test the functionality of the game logic (unit tests), of the god cards (unit tests), and of the game with and without god cards (integration tests). As before, we do not set any specific coverage goals but ask you to use your own judgment about how much testing is useful for you to have confidence in your implementation. 


## Submitting your Work

For each milestone, submit a link to your final commit on Canvas as usual in the format `https://github.com/CMU-17-214/<reponame>/commit/<commitid>`. As in HW3, ensure the project is built and your tests are executed in Github Actions.

For Milestone 6a, make sure that your repository has updated versions of `README.md` in the root directory of your repository. For Milestone 6b, make sure that your repository has the new `extension-justification.pdf` in the root directory of your repository.




## Evaluation

This assignment is worth 300 points, 120 for Milestone 6a and 180 for Milestone 6b.

Homework submissions with a link in the wrong format will not receive any points.

**Milestone 6a user interface (90 points)**


* [ ] 10: Separation of GUI and core: The core of the game is independent of the GUI (works with GUI code deleted). Both are separated in different locations of the project. There are no GUI-related concepts (including a backend server providing an API) in the implementation of the core game, and the GUI code does not reimplement the game concepts.
* [ ] 80: The game is functional, playable through the user interface:

  * [ ] 5: User Interface is clear and easy to use. Users can operate the game basically by clicking their mouse.
  * [ ] 10: Instructions in the `README.md` file are sufficient to understand how to start and play the game (assuming user knows the rules)
  * [ ] 5: Game starts and can be restarted (e.g., 'new game' button)
  * [ ] 5: Both players can place the initial workers (e.g. by clicking an empty grid)
  * [ ] 5: The GUI indicates the current player
  * [ ] 10: The GUI indicates available actions (valid move/build actions) or rejects invalid actions
  * [ ] 5: The game recognizes the end of a turn and moves to the next player
  * [ ] 15: The game and GUI correctly update after a move action
  * [ ] 15: The game and GUI correctly update after a build action
  * [ ] 5: Correctly identifies and shows the winner of the game

**Milestone 6a implementation quality (30 points)**


* [ ] 10: Game builds all code and passes tests on Github Actions
* [ ] 10: Code quality and style: Code meets language's conventions, is reasonably well documented, reasonably clean (e.g., avoids dead code), avoids common programming errors (e.g., == vs equals in Java)
* [ ] 10: Reasonably cohesive commits and reasonable commit messages

**Milestone 6b god card design and justification (55 points)**

 * [ ] 10: The implemented design allows god cards to allow additional (optional) actions (e.g., for Demeter and Hephaestus). God cards can be added without changing the implementation of the game's core classes (i.e., no hard coding with if statements).
 * [ ] 10: The implemented design allows god cards to change winning rules (e.g., for Pan). God cards can be added without changing the implementation of the game's core classes (i.e., no hard coding with if statements).
 * [ ] 10: The implemented design must allow god cards to move other workers as part of the current player's actions (e.g., for Minotaur). God cards can be added without changing the implementation of the game's core classes (i.e., no hard coding with if statements).
 * [ ] 10: The implemented design across all models makes reasonable decisions about responsibility assignment, avoids unnecessary coupling, and has reasonable cohesion.
 * [ ] 10: The justification in `extension-justification.pdf` uses suitable design terminology and discusses design alternatives in a meaningful way, demonstrating an engagement with design principles and tradeoffs.
 * [ ] 5: The justification in `extension-justification.pdf` identifies all used design patterns (if any) and justifies their use or why no design patterns were used.

**Milestone 6b design diagrams (notation, consistency, completeness) (40 points)**

 * [ ] 5: The updated domain model in file `domain-model.pdf` describes the vocabulary of the extended problem with reasonable completeness, uses suitable notation (right UML boxes, named associations with cardinalities, association vs field, reasonable naming), and is at the right level of abstraction.
 * [ ] 5: The updated system sequence diagram in file `system-sequence-diagram.pdf` is reasonably complete, uses suitable notation, and is at the right level of abstraction. It includes the setup for god cards.
 * [ ] 5: The updated behavior contract in file `contract.pdf` is reasonably complete regarding pre- and post-conditions under the assumption that the active player has the *Minotaur* card.
 * [ ] 10: The updated  `build-justification.pdf` clearly describes and justifies how build actions are validated and performed. The model describes the behavior for the case where the active player has the Demeter card. We will check:
   - a. It is clear from the description what checks are performed to determine whether a build action is valid and how the state of the game is updated when the action is performed.
   - b. The description matches the interaction diagram.
   - c. The responsibility assignment for each method involved in checking and performing builds is justified with suitable design vocabulary (design goals/principles/heuristics/patterns). The assigned responsibilities and justifications are plausible.
   - d. The justification demonstrates an engagement with design principles and tradeoffs, and discusses design alternatives in a meaningful way.
   - e. It is clear how the base game and the *Demeter* god card interact.
 * [ ] 5: The updated interaction diagram in `build-justification.pdf` is reasonably complete, uses suitable notation, is at the right level of abstraction, and is consistent with the object model (called methods exist in target class, caller has access to target objects). The model includes the behavior of the Demeter card for the case where the active player has the Demeter card.
 * [ ] 10: The updated object model in file `object-model.pdf` is reasonably complete, uses suitable notation (right UML boxes, named associations with cardinalities, association vs field, reasonable naming), and is at the right level of abstraction. The updated model also covers the extension mechanisms of the base game and the Demeter card. It is consistent with the system sequence diagram.

**Milestone 6b god card implementation (65 points)**

 * [ ] 20: The four required god cards are implemented in the game and work as specified.
 * [ ] 20: The game and god cards are tested at a reasonable level. Tests include unit tests of individual functionality and integration test of the game with different god cards. The tests follow good practices (e.g. redundancy, independence, readability).
 * [ ] 10: The implementation is consistent with the design documents.
 * [ ] 15: The user interface supports god cards, including allowing users select god cards and allowing users to control their extra actions (e.g., build again).

**Milestone 6b general implementation quality (20 points)**

* [ ] 10: Game builds and passes tests on Github Actions
* [ ] 5: Code quality and style: Code meets language's conventions, is reasonably well documented, reasonably clean (e.g., avoids dead code), avoids common programming errors (e.g., == vs equals in Java)
* [ ] 5: Reasonably cohesive commits and reasonable commit messages

**Milestone 6b bonus points (0-24 points)** 

 * [ ] 4: points per additional god card listed in the appendix, if it is implemented correctly, not hard-coded in the base game, tested, and usable through the user interface



## Appendix: God Cards

You can find the original rules of Santorini including all god cards at: https://roxley.com/products/santorini

We consider only basic god cards. The bold ones are required:


 * Apollo: Your Worker may move into an opponent Worker’s space by forcing their Worker to the space yours just vacated.


 * Artemis: Your Worker may move one additional time, but not back to its initial space. (UI hint: You will likely need a way to indicate that the player wants to skip the optional second move, either with a "pass" button or by clicking on the worker's current location)


 * Athena: During opponent’s turn: If one of your Workers moved up on your last turn, opponent Workers cannot move up this turn.


 * Atlas: Your Worker may build a dome at any level. (UI hint: you can implement this in the user interface similar to Hephaestus, giving the player an second optional build action; this build action is interpreted as building a dome)


 * **Demeter**: Your Worker may build one additional time, but not on the same space. (UI hint: You will likely need a way to indicate that the player wants to skip the optional second build, e.g., with a "pass" button or by clicking on the worker's current location)


 * **Hephaestus**: Your Worker may build one additional block (not dome) on top of your first block. (UI hint: You will likely need a way to indicate that the player wants to skip the optional second build, e.g., with a "pass" button or by clicking on the worker's current location)


 * Hermes: If your Workers do not move up or down, they may each move any number of times (even zero), and then either builds. (UI hint: Rather than allowing multiple move actions, it might be easier to indicate all possible target spaces where a worker can move too)


 * **Minotaur**: Your Worker may move into an opponent Worker’s space, if their Worker can be forced one space straight backwards to an unoccupied space at any level.


 * **Pan**: You also win if your Worker moves down two or more levels.


 * Prometheus: If your Worker does not move up, it may build both before and after moving.





