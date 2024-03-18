# Lab 9: Introduction to React.js

React is a declarative, efficient, and flexible JavaScript library for building interactive and dynamic user interfaces. It lets you compose complex UIs from small and isolated pieces of code called “components”.In this lab, students will learn the fundamentals of React.js and create an interactive quiz application.

## Deliverables
- [ ] Modify the implementation to separate the core and GUI components.
- [ ] Enhance the user interface to indicate the selected answer, providing a more visually appealing user experience
- [ ] Extend the Quiz component to make the "Next Question" button functional. It should move to the next question and display the total score when all questions have been answered.

## Instructions
Clone the Quiz App repository from: https://github.com/CMU-17-214/s24-rec09 and run

```
npm install
npm start
```
![Local Image](https://github.com/CMU-17-214/s24-rec09/blob/main/src/image/starterPic.png)

This will start the front-end server. You will be able to see a simple quiz GUI from the link http://localhost:3000/. You can update the front-end code as the server is running in the development mode (i.e., `npm start`). It will automatically recompile and reload.

In this starter code, you are provided with a Quiz class component.
The initial state includes a sample question, answer options, and a `selectedAnswer` value.
The `handleOptionSelect` function allows selecting an answer option and updates the `selectedAnswer` in the component's state.
The component uses JSX to return HTML-like markup directly, displaying the question, answer options, and the selected answer within the component's return statement.
> JSX is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file

### Core-GUI Separation 
In the starter code, you will observe that the `Quiz.tsx` file combines both the logic and the graphical user interface (GUI) of the quiz application. While this might be a convenient starting point, it is generally considered a best practice to separate the core logic of an application from its GUI components. This separation ensures better maintainability, code organization, and flexibility for future improvements.
Therefore, the first task is to practice Core-GUI Separation. For your convenience, We've provided a core implementation for you at [src/core/QuizCore.ts](https://github.com/CMU-17-214/s24-rec09/blob/main/src/core/QuizCore.ts). This core module encapsulates critical quiz operations. It's designed to manage the quiz's functionality independently of the GUI. Your task is to integrate this core with the user interface `Quiz.tsx`. Ensure that your GUI component correctly reflects the data from the QuizCore. Update your component to display the questions and answer options provided by the core. Take care to observe and update the user's selected options and other state changes effectively.

### Enhance User Experience
The starter code directly displays the user's current selection. Your task is to enhance the user experience by making is more visually appealing.  You have the creative freedom to improve the user interface.One way is to highlight the selected option. When a user clicks on an answer, it should be visually highlighted.

> Hint: You can consider using CSS to change the background color or apply a border to the selected option

### Manage User Interaction and Scoring
In the initial implementation, the "Next Question" button remains inactive – it neither progresses to the next question nor displays the final score upon completing all the questions. Your next task is to enhance the user interaction by making the "Next Question" button functional when appropriate and displaying the total score when all questions have been answered.

Here's what you need to do:
When a question is displayed, ensure that the "Next Question" button takes users to the following question. To achieve this, you should check if there is a next question available in the quiz. You can utilize the `hasNextQuestion()` method provided in the core logic.

When all questions have been answered, make a "Submit" button visible, and upon clicking it, display the total score. For simplicity, each question in the quiz is worth a score of 1 if answered correctly. You can utilize `the getScore()` method provided in the core logic.