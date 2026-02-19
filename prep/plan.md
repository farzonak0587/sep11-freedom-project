# Plan

## Tool: Kaboom.js
## Product: A reaction-focused game that asks simple questions with answers written in misleading colors. The goal is for the player to choose the right answer quickly.

---

## Timeline

#### MVP

- [ ] **Project Setup & Basic Layout: (deadline: Monday, 3/2)**
  - [ ] In index.html, create the structure for the game:
  - [ ] An area to display the question.
  - [ ] A set of answer buttons (for user clicks).
  - [ ] A score display.
  - [ ] A timer display.

- [ ] **Display Questions and Answers: (deadline: Monday, 3/9)**
  - [ ] Questions Array:
  - [ ] Store the questions and answers in JavaScript as an array of objects. Each object should contain: A question string. An array of answer options (including the correct answer).
  - [ ] Use event listeners (DOM) to detect when the user clicks one of the answer buttons. When clicked, check if the answer is correct and update the score accordingly.

- [ ] **Timer and Scoring: (deadline: Monday, 3/16)**
  - [ ] Create a score tracker using a variable in JavaScript. Each time the user selects the correct answer, increase the score by 1.
  - [ ] When time runs out or the user answers, check if they got the question right, update the score, and either move to the next question or end the game.
  - [ ] Create a  countdown timer will be set up that shows on the screen and decreases every second to show how much time left to answer the question.

- [ ] **Answer Color Trick: (deadline: Monday, Monday, 3/23)**
  - [ ] For the “brain trick,” use CSS to randomly change the colors of the answer buttons (e.g., displaying the word "Blue" in red font, etc.).
  - [ ] When the game ends (e.g., after a set number of questions or when the player answers incorrectly a certain number of times), display a game over screen with the final score.

- [ ] **Styling: (deadline: Monday, 3/6)**
  -   [ ] Add all the CSS to make it look better, pleasing and like a funner game.

- [ ] **Bug Fixes + Final Touches: (deadline: Monday, 4/13)**
  -   [ ] Test the game thoroughly to make sure all features (question flow, timer, scoring, game over) are working as expected.

#### Beyond MVP

- [ ] **More Responsive:**
  - [ ] Ensure the game is responsive, meaning it works well on both small and large screens.

- [ ] **Final Touches:**
  - [ ] Do a final round of testing, making sure the game works from start to finish, and all elements are functioning correctly.


<!-- EXAMPLE

## Tool: APIs
## Product: Green Glass Door riddle app

## Timeline

### MVP

- [ ] Front-end
  - [x] Webpage to collect input from user (deadline: 4/15)
  - [ ] Webpage to display "yes, but a ___ can't" or "no, but a ___ can" (deadline: 5/1)
- [x] Back-end
  - [x] Use regex to test whether or not the word can go through the GGD (deadline: 3/1)
  - [x] Use the Twinword API to find related words (deadline: 3/15)
    - [ ] Iterate through the words until an opposite example can be found (deadline: 4/1)

#### Beyond MVP

- [ ] Use another API to make sure the opposite example is a noun
- [ ] Automate notification of API limit to make sure I don’t exceed free quota
- [ ] A multiple choice quizzer that will test the user’s knowledge of the solution

-->





<!-- DO NOT USE THIS YET

#### Peer Feedback

| Name | Glows | Grows |
| -------- | ------- | ------- |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

-->
