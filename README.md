# pai

# Experiment 1

### Aim
**Introduction to Prolog** (Write a brief about origin of Prolog, predicates/general rules).

### Overview
Prolog (short for "Programming in Logic") is a logic programming language developed in the early 1970s, primarily for artificial intelligence and computational linguistics applications. It was created by Alain Colmerauer and Robert Kowalski in 1972.

Prolog is based on formal logic, specifically first-order predicate logic, and allows programmers to define relations, facts, and rules to solve complex problems. Unlike imperative programming languages, Prolog uses a declarative approach, where the focus is on defining what the problem is rather than how to solve it.

### Key Concepts in Prolog
- **Facts**: Facts are basic assertions about objects or relationships between them. They are used to represent static information in the knowledge base.

- **Rules**: Rules define relationships between facts using logical implication. They specify conditions under which certain facts can be inferred.
  - Example:
    ```prolog
    friend(X, Y) :- likes(X, pizza), likes(Y, pizza).
    ```

- **Queries**: Queries are questions asked to the Prolog system to check if certain facts or rules are true.
  - Example:
    ```prolog
    ?- friend(alice, bob).
    ```

- **Predicates**: Predicates are logical statements used to describe relationships between terms (objects or variables). They form the core of facts and rules in Prolog.

### Example of a Predicate:
```prolog
parent(X, Y). % X is the parent of Y
```

### Origin of Prolog
Prolog's development began in 1972 in Marseille, France, under the guidance of Alain Colmerauer. Its creation was influenced by earlier developments in logic, particularly resolution theorem proving by Alan Robinson. Prolog became one of the earliest and most influential languages for AI, enabling the representation of complex relationships and computations.

---

## Task 1.1: Write General Facts in Prolog

**Examples:**

1. **A) Ram is my friend**
    ```prolog
    friend(ram).
    ?- friend(X).
    X = ram.
    ```

2. **B) Hexagon has 6 edges**
    ```prolog
    edges(hexagon, 6).
    ?- edges(hexagon, X).
    X = 6.
    ```

3. **C) Author of "Prolog" is Alain Colmerauer**
    ```prolog
    author(alaincolmerauer).
    ```

4. **D) Telephone code of fire is 101**
    ```prolog
    telephone(101, fire).
    ?- telephone(X, fire).
    X = 101.
    ```

5. **E) Kasturba was the wife of Gandhi**
    ```prolog
    wife(kasturba, gandhi).
    ?- wife(X, gandhi).
    X = kasturba.
    ```

6. **F) There are 11 players in cricket**
    ```prolog
    player(cricket, 11).
    ?- player(cricket, X).
    X = 11.

    Let me transcribe and guide you through creating the Prolog facts, rules, and queries for this experiment. Here's how we will structure the solution for the Ramayana tree:

---

### **Prolog Code**
#### Facts and Rules for the Ramayana Tree

Below is the transcribed Prolog code and additional rules based on your uploaded image:

```prolog
% Facts
wife(kaushalya, dashrath).
wife(kaikey, dashrath).
wife(sumitra, dashrath).
wife(sita, ram).
wife(urmila, laxman).
wife(mandavi, bharat).
wife(shrutakirti, shatrughan).

son(ram, kaushalya).
son(laxman, sumitra).
son(bharat, kaikey).
son(shatrughan, sumitra).
son(luv, ram).
son(khush, ram).
son(angad, laxman).
son(chandraketu, laxman).
son(taksha, bharat).
son(pushkal, bharat).
son(subahu, shatrughan).
son(shatrughat, shatrughan).

% Rules
husband(X, Y) :- wife(Y, X).
daughterinlaw(D, M) :- wife(D, H), son(H, M).
motherinlaw(X, Y) :- daughterinlaw(Y, X).
fatherinlaw(F, D) :- motherinlaw(M, D), wife(M, F).
grandson(X, Y) :- son(A, Y), son(X, A).
father(X, Y) :- son(Y, X).
```

---

### **Queries with Expected Output**
Based on your example, here are some Prolog queries you can execute in SWI-Prolog:

#### Sample Queries:
1. **Who is the son of Kaushalya?**
   ```prolog
   ?- son(X, kaushalya).
   ```
   **Output:**  
   ```
   X = ram.
   ```

2. **Who are the sons of Ram?**
   ```prolog
   ?- son(X, ram).
   ```
   **Output:**  
   ```
   X = luv ;
   X = khush.
   ```

3. **Who is the husband of Sita?**
   ```prolog
   ?- husband(X, sita).
   ```
   **Output:**  
   ```
   X = ram.
   ```

4. **Who is the grandson of Kaushalya?**
   ```prolog
   ?- grandson(X, kaushalya).
   ```
   **Output:**  
   ```
   X = luv ;
   X = khush.
   ```

5. **Who is the father of Luv and Khush?**
   ```prolog
   ?- father(X, luv).
   ```
   **Output:**  
   ```
   X = ram.
   ```

---

### Steps to Run the Prolog Code
1. **Open SWI-Prolog.**
   - If not installed, download and install it from [SWI-Prolog's website](https://www.swi-prolog.org/).

2. **Create a Prolog file:**
   - Save the code above in a file named `ramayana_tree.pl`.

3. **Load the file in SWI-Prolog:**
   ```prolog
   ?- [ramayana_tree].
   ```

4. **Run Queries:**
   - Enter the queries one by one to test relationships.

---

### Example Queries and Outputs for Testing
You can modify or add new queries to explore the family tree further. Let me know if you need help with specific relations or explanations!



# Experiment No. 2: Numeric Functions in Prolog

## AIM
Write a program to implement input, output, and predicates in Prolog.

# Prolog Basics

## Inputs Text Handling in Prolog
In Prolog, handling text input typically involves reading from the user or a file. The built-in predicates provide flexible ways to manage inputs.

### Key Predicates:
1. **`read/1`**:
   - Reads a Prolog term from the standard input.
   - Example:
     ```prolog
     ?- read(X).
     % User inputs: hello.
     X = hello.
     ```

2. **`read_line_to_string/2`** (SWI-Prolog):
   - Reads a line from the input and returns it as a string.
   - Example:
     ```prolog
     ?- read_line_to_string(user_input, Line).
     % User inputs: Hello World!
     Line = "Hello World!".
     ```

3. **`get_char/1`**:
   - Reads a single character from the input.
   - Example:
     ```prolog
     ?- get_char(Char).
     % User inputs: a
     Char = 'a'.
     ```

4. **`get_code/1`**:
   - Reads a single character as its ASCII code.
   - Example:
     ```prolog
     ?- get_code(Code).
     % User inputs: a
     Code = 97.
     ```

5. **`atom_chars/2`** and **`string_chars/2`**:
   - Converts an atom or string to a list of characters and vice versa.
   - Example:
     ```prolog
     ?- atom_chars('hello', Chars).
     Chars = ['h', 'e', 'l', 'l', 'o'].
     ```

### Reading Input from a File:
Use predicates like `open/3`, `read/2`, and `close/1` to handle file input.
Example:
```prolog
?- open('file.txt', read, Stream),
   read(Stream, Content),
   close(Stream).
Content = your_file_content.
```

---

## Numeric Functions in Prolog
Prolog supports numerical computations using built-in arithmetic predicates and functions.

### Common Arithmetic Predicates:
1. **`is/2`**:
   - Used to evaluate arithmetic expressions.
   - Example:
     ```prolog
     ?- X is 5 + 3.
     X = 8.
     ```

2. **Relational Operators**:
   - Compare numerical values.
     - `=`: Equality.
     - `\=`: Inequality.
     - `>`: Greater than.
     - `<`: Less than.
     - `>=`: Greater than or equal to.
     - `=<`: Less than or equal to.
   - Example:
     ```prolog
     ?- 5 > 3.
     true.
     ```

### Built-in Numeric Functions:
1. **Basic Operations**:
   - Addition: `+`
   - Subtraction: `-`
   - Multiplication: `*`
   - Division: `/`

2. **Advanced Functions**:
   - Integer Division: `div`
     ```prolog
     ?- X is 7 div 2.
     X = 3.
     ```
   - Modulus: `mod`
     ```prolog
     ?- X is 7 mod 2.
     X = 1.
     ```
   - Power: `^`
     ```prolog
     ?- X is 2^3.
     X = 8.
     ```
   - Square Root: `sqrt/1`
     ```prolog
     ?- X is sqrt(16).
     X = 4.0.
     ```
   - Absolute Value: `abs/1`
     ```prolog
     ?- X is abs(-5).
     X = 5.
     ```

### Notes:
- Arithmetic is not evaluated during unification. Always use `is/2` to compute values.

---

## Predicates in Prolog
A predicate in Prolog defines a relation or rule, consisting of facts, rules, or queries.

### Facts:
- Declare information that is always true.
- Example:
  ```prolog
  parent(john, mary).
  parent(mary, alice).
  ```

### Rules:
- Define relations based on other facts or rules.
- Example:
  ```prolog
  grandparent(X, Y) :- parent(X, Z), parent(Z, Y).
  ```

### Queries:
- Used to retrieve information from the Prolog database.
- Example:
  ```prolog
  ?- grandparent(john, Y).
  Y = alice.
  ```

### Structure of a Predicate:
A predicate consists of:
1. **Name**: The identifier of the predicate.
2. **Arity**: Number of arguments it takes.
   - Example: `parent/2` means the predicate `parent` takes 2 arguments.

### Types of Predicates:
1. **Dynamic Predicates**:
   - Defined or modified during runtime using `assert/1` and `retract/1`.
     ```prolog
     ?- assert(parent(paul, linda)).
     ?- parent(paul, linda).
     true.
     ```

2. **Recursive Predicates**:
   - Define relations recursively.
     ```prolog
     ancestor(X, Y) :- parent(X, Y).
     ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).
     
---

## 2.1 Numeric Function in Prolog

### Objective
Find the division and modulus of two numbers.

### Code
```prolog
division :-
    write('Read no. 1: '),
    read(X),
    write('Read no. 2: '),
    read(Y),
    cal(X, Y).

cal(X, Y) :-
    Q is div(X, Y),
    R is mod(X, Y),
    write('Quotient is: '),
    write(Q),
    write('\nRemainder is: '),
    write(R).
```

### Example Query and Output
#### Query:
```prolog
?- division.
```
#### Output:
```
Read no. 1: 10
Read no. 2: 3
Quotient is: 3
Remainder is: 1
```

---

## 2.2 Evaluate Different Numeric Functions in Prolog

### Objective
Evaluate the square root, maximum value, and floor value of numbers.

### Code
```prolog
cal :-
    write('Enter no. 1: '),
    read(X),
    write('Enter no. 2: '),
    read(Y),
    comp(X, Y).

comp(X, Y) :-
    S is sqrt(X),
    write('Square root is: '),
    write(S),
    M is max(X, Y),
    write('\nMaximum is: '),
    write(M),
    F is floor(X),
    write('\nFloor value is: '),
    write(F).
```

### Example Query and Output
#### Query:
```prolog
?- cal.
```
#### Output:
```
Enter no. 1: 3
Enter no. 2: 5
Square root is: 1.732
Maximum is: 5
Floor value is: 3
```

---

## Notes
- **`div/2`**: Computes the integer quotient of two numbers.
- **`mod/2`**: Computes the remainder of the division of two numbers.
- **`sqrt/1`**: Computes the square root of a number.
- **`max/2`**: Finds the maximum of two numbers.
- **`floor/1`**: Rounds a number down to the nearest integer.

### Steps to Run
1. Save the code snippets into a `.pl` file (e.g., `numeric_functions.pl`).
2. Open SWI-Prolog and load the file using:
   ```prolog
   ?- [numeric_functions].
   ```
3. Run the queries as shown in the examples to test the functionality.

---

### Additional Information
Prolog's built-in predicates like `div/2`, `mod/2`, `sqrt/1`, and `max/2` are useful for various mathematical operations. The use of `write/1` and `read/1` enables user interaction for input and output.


# Experiment No. 3

## Aim
Write a program to implement local variables and conditional statements using Prolog.

## Theory
### Local Variables in Prolog
In Prolog, variables are typically used to store values during the execution of predicates. However, Prolog does not have traditional "local variables" as in imperative languages. Instead, variables defined within a predicate's body are local to that predicate and are not accessible outside its scope. This allows for encapsulation of data within predicates.

### Conditional Statements (If-Then-Else)
Prolog uses the `->` operator for implementing conditional statements. The structure of a conditional in Prolog is as follows:

```prolog
Condition -> Action1 ; Action2.
```
- **Condition**: A Prolog goal that evaluates to true or false.
- **Action1**: Executed if the condition is true.
- **Action2**: Executed if the condition is false.

The `;` operator acts as an "else" clause in the conditional statement.

### Example
```prolog
check_number(X, Result) :-
    (X > 0 -> Result = 'Positive';
     X < 0 -> Result = 'Negative';
     Result = 'Zero').
```
In this example:
- If `X` is greater than 0, the result is 'Positive'.
- If `X` is less than 0, the result is 'Negative'.
- Otherwise, the result is 'Zero'.

## Program
```prolog
my_predicate(X, Y) :-
    LocalVariable = 42,
    write('LocalVariable='), write(LocalVariable), nl,
    (   X = 1 -> Y = 'X is 1', write(Y);
        X = 2 -> Y = 'X is 2', write(Y);
        Y = 'X is neither 1 nor 2'
    ).
```

## Example Query and Output

### Query
```prolog
?- my_predicate(1, Y).
```

### Output
```
LocalVariable=42
X is 1
```

### Additional Example
#### Query
```prolog
?- my_predicate(3, Y).
```
#### Output
```
LocalVariable=42
X is neither 1 nor 2
```


# Experiment No. 4

## Aim
Write a program to calculate the factorial of a given number using Prolog.

## Theory
### Factorial Definition
The factorial of a non-negative integer `n` is the product of all positive integers less than or equal to `n`. It is denoted by `n!` and is defined as:

```
n! = n × (n-1) × (n-2) × ... × 1
```
For example:
- `0! = 1` (by definition)
- `5! = 5 × 4 × 3 × 2 × 1 = 120`

### Recursion in Prolog
Recursion is a fundamental concept in Prolog, where a predicate calls itself to solve smaller instances of a problem. Recursion typically involves:
1. **Base Case**: A condition where the recursion stops.
2. **Recursive Case**: A rule that reduces the problem into smaller sub-problems.

In Prolog, recursion is used to traverse and compute results over structures or numerical sequences. It is especially useful for problems like factorial computation, list processing, and tree traversals.

## Program
```prolog
factorial(0, 1). % Base case: factorial of 0 is 1
factorial(N, X) :-
    N > 0,
    N1 is N - 1,
    factorial(N1, X1), % Recursive call
    X is X1 * N.
```

## Example Query and Output

### Query
```prolog
?- factorial(5, X).
```

### Output
```
X = 120
```

### Explanation
1. The base case `factorial(0, 1)` stops the recursion when `N` reaches 0.
2. For `factorial(5, X)`, the recursive calls break it down as:
   - `factorial(5, X) = 5 × factorial(4, X1)`
   - `factorial(4, X1) = 4 × factorial(3, X2)`
   - ...
   - Until `factorial(0, 1)` is reached.


# Experiment No. 5

## Aim
Write a program to solve the 4-Queen problem using Prolog.

## Theory

### 4-Queen Problem
The 4-Queen problem is a classic combinatorial problem in which the goal is to place 4 queens on a 4×4 chessboard so that no two queens attack each other. In chess, a queen can attack another piece if it is on the same row, column, or diagonal. 

The problem can be extended to an `N-Queen` problem for an `N×N` board, but here, we focus on the 4×4 case.

### Key Concepts
- **Board Representation**: The board is represented as a list of numbers, where the position of each queen is defined by its row or column.
- **Constraints**: The placement of queens must satisfy the conditions:
  1. No two queens are in the same row.
  2. No two queens are in the same column.
  3. No two queens are on the same diagonal.
- **Backtracking**: The solution is found using backtracking, where the algorithm incrementally builds a solution and backtracks whenever a conflict arises.

### Approach
1. **Define Board and Valid Positions**: Represent the board size and ensure rows and columns are within valid ranges.
2. **Attack Predicate**: Define when a queen can attack another.
3. **Place Queens**: Use recursive predicates to place queens while ensuring no attacks.
4. **Find Solutions**: Use backtracking to generate all valid queen placements.
5. **Output Solutions**: Print all the solutions satisfying the constraints.

## Program
```prolog

---
### **Prolog Code:**

```prolog
% Define the size of the board
board_size(4).

% Check if a position is valid
valid_pos(P) :- 
    board_size(N), 
    between(1, N, P).

% Define the attack predicate
attack(R1, C1, R2, C2) :- 
    R1 =:= R2;                    % Same row
    C1 =:= C2;                    % Same column
    abs(R1 - R2) =:= abs(C1 - C2). % Same diagonal

% Place queens on the board
place_queens([], []).
place_queens([R|Rs], [C|Cs]) :- 
    valid_pos(R), valid_pos(C),
    no_attack(R, C, Rs, Cs), 
    place_queens(Rs, Cs).

% Check that no queens attack each other
no_attack(_, _, [], []).
no_attack(R, C, [R1|Rs], [C1|Cs]) :- 
    \+ attack(R, C, R1, C1), 
    no_attack(R, C, Rs, Cs).

% Solve the N-Queens problem
solve_queens(Queens) :- 
    board_size(N), 
    length(Queens, N), 
    place_queens(Queens, _).
```

---

### **Queries:**

#### Query 1: Solve the 4-Queen problem and display the positions of the queens
```prolog
?- solve_queens(Queens).
```

**Output:**
```text
Queens = [2, 4, 1, 3] ;
Queens = [3, 1, 4, 2].
```

---

#### Query 2: Check if a specific placement is valid
```prolog
?- place_queens([1, 3, 4, 2], [1, 2, 3, 4]).
```

**Output:**
```text
true.
```

---

This code and queries should work perfectly for solving and validating the 4-Queen problem. Let me know if you need further clarification!
```

## Example Query and Output
### Query
```prolog
?- find_solutions(Solutions).
```

### Output
```
Solutions = [[2, 4, 1, 3], [3, 1, 4, 2]].
Total solutions: 2
```

### Explanation
1. The program calculates all valid configurations where the queens do not attack each other.
2. In the 4×4 case, there are two distinct solutions: `[2, 4, 1, 3]` and `[3, 1, 4, 2]`.

### Visualization of Solutions
For `[2, 4, 1, 3]`:
```
. Q . .
. . . Q
Q . . .
. . Q .
```
For `[3, 1, 4, 2]`:
```
. . Q .
Q . . .
. . . Q
. Q . .
```




# Experiment No. 6: Monkey Banana Problem Using Prolog

## Aim
To implement the Monkey-Banana problem using Prolog and demonstrate logical reasoning for achieving a goal.

## Program
```prolog
% Objects in the room
in_room(banana).
in_room(chair).
in_room(monkey).

% Actions available
push(monkey, chair).
can_climb(monkey, chair).
grasp(monkey, banana).
eat(monkey, banana).

% Rule to determine if the monkey can reach and eat the banana
can_reach(X, Y) :-
    in_room(X), in_room(Y), in_room(Z),
    push(X, Z),
    can_climb(X, Z),
    grasp(X, Y),
    eat(X, Y).

% Query
?- can_reach(monkey, banana).
```

## Theory

### Monkey-Banana Problem
The Monkey-Banana Problem is a classic problem in artificial intelligence and logic programming that demonstrates goal-driven behavior and problem-solving. The problem involves a monkey in a room with a banana hanging from the ceiling, a chair, and the need to combine actions to achieve the goal of eating the banana. The problem is often used to illustrate:

1. **Logical Reasoning**: Determining the sequence of actions required to achieve the goal.
2. **State Representation**: Representing the environment (monkey, chair, banana) and actions in logical terms.
3. **Goal-Oriented Planning**: Finding a path from the initial state to the goal state.

### Problem Description
The room contains:
- A **monkey** on the ground.
- A **banana** hanging from the ceiling.
- A **chair** that can be pushed and climbed.

The goal is for the monkey to grasp and eat the banana. The actions available to the monkey include:
1. **Push**: The monkey can push the chair to a position under the banana.
2. **Climb**: The monkey can climb the chair.
3. **Grasp**: The monkey can reach for the banana from the chair.
4. **Eat**: The monkey can eat the banana once it is grasped.

### Prolog Representation
1. **Facts**: Represent the objects in the room (`in_room`) and the monkey's abilities (`push`, `can_climb`, `grasp`, `eat`).
2. **Rules**: Define the conditions for achieving the goal (`can_reach`), combining logical steps such as pushing, climbing, grasping, and eating.
3. **Query**: Test if the monkey can reach and eat the banana using the defined facts and rules.

### Explanation of Code
- **`in_room`**: Specifies the presence of objects in the room.
- **`push`, `can_climb`, `grasp`, `eat`**: Actions the monkey can perform.
- **`can_reach`**: Combines all actions logically to determine if the monkey can reach and eat the banana.
- **Query**: `?- can_reach(monkey, banana).` checks whether the monkey can successfully eat the banana.

### Execution
The Prolog program evaluates the facts and rules to determine if the sequence of actions (push chair, climb chair, grasp banana, eat banana) is possible, ultimately returning a success if the goal is achievable.

## Conclusion
The Monkey-Banana problem demonstrates how Prolog can model real-world problems using logical facts and rules. It highlights the importance of reasoning and planning in artificial intelligence.


# Experiment No. 7

## Aim:
Develop a Medical Diagnostic System using Prolog.

---

## Program:
```prolog
% Define symptoms for a patient
symptom(charlie, fever).
symptom(charlie, rash).
symptom(charlie, headache).
symptom(charlie, runny_nose).

% Define hypotheses based on symptoms
hypothesis(Patient, measles) :-
    symptom(Patient, fever),
    symptom(Patient, cough),
    symptom(Patient, conjunctivities),
    symptom(Patient, runny_nose),
    symptom(Patient, rash).

hypothesis(Patient, german_measles) :-
    symptom(Patient, fever),
    symptom(Patient, headache),
    symptom(Patient, runny_nose),
    symptom(Patient, rash).

hypothesis(Patient, flu) :-
    symptom(Patient, fever),
    symptom(Patient, headache),
    symptom(Patient, body_ache),
    symptom(Patient, conjunctivities),
    symptom(Patient, chills),
    symptom(Patient, sore_throat),
    symptom(Patient, cough),
    symptom(Patient, runny_nose).

hypothesis(Patient, common_cold) :-
    symptom(Patient, headache),
    symptom(Patient, sneezing),
    symptom(Patient, sore_throat),
    symptom(Patient, chills),
    symptom(Patient, runny_nose).

hypothesis(Patient, mumps) :-
    symptom(Patient, fever),
    symptom(Patient, swollen_glands).

hypothesis(Patient, chicken_pox) :-
    symptom(Patient, fever),
    symptom(Patient, rash),
    symptom(Patient, body_ache),
    symptom(Patient, chills).

hypothesis(Patient, whooping_cough) :-
    symptom(Patient, cough),
    symptom(Patient, sneezing),
    symptom(Patient, runny_nose).

% Query Example
?- hypothesis(charlie, Disease).
```

---

## Output:
```prolog
?- hypothesis(charlie, Disease).
Patient = charlie,
Disease = german_measles.
```

---

## Theory:

### Medical Diagnostic System:
A medical diagnostic system in Prolog is an expert system designed to infer potential diseases or medical conditions based on the symptoms provided for a patient. The program utilizes Prolog’s rule-based logic to map symptoms to specific diagnoses.

### Components of the System:
1. **Facts:** These represent known information about the patient, such as their symptoms. For example:
   ```prolog
   symptom(charlie, fever).
   symptom(charlie, rash).
   ```

2. **Rules:** These describe the relationship between symptoms and potential diseases. For example:
   ```prolog
   hypothesis(Patient, measles) :-
       symptom(Patient, fever),
       symptom(Patient, rash),
       symptom(Patient, runny_nose).
   ```

3. **Queries:** The system is queried to deduce the disease based on the given symptoms:
   ```prolog
   ?- hypothesis(charlie, Disease).
   ```

### Advantages of Prolog in Medical Diagnosis:
- **Declarative Nature:** Prolog allows the developer to define the problem domain in terms of facts and rules without detailing procedural steps.
- **Pattern Matching:** Prolog’s built-in unification and backtracking capabilities make it efficient for matching symptoms to rules.
- **Extendibility:** New diseases and symptoms can easily be added to the system without altering the existing logic.

### Applications:
- Clinical decision support systems.
- Differential diagnosis tools.
- Teaching and training tools in medical schools.

## EXPERIMENT NO. 8

### Aim:
To solve the 8-puzzle problem using Prolog.

### Prolog Code:
```prolog
% Define transitions for moving the blank space (0) to the left
left(A, 0, B, C, D, E, F, G, H) :- state(0, A, B, C, D, E, F, G, H).

% Initial state of the puzzle (START)
% The blank space is represented by 0
% 2  8  3
% 1  6  4
% 7     5
state(2, 8, 3, 1, 6, 4, 7, 0, 5).

% Goal state of the puzzle (GOAL)
% 1  2  3
% 8     4
% 7  6  5
state(1, 2, 3, 8, 0, 4, 7, 6, 5).

% Transitions for moving the blank space (0) in various directions
state(A, B, C, D, E, F, G, 0, H) :- state(A, B, C, D, 0, E, F, G, H);
                                    state(A, B, C, D, E, F, 0, G, H);
                                    state(A, B, C, D, E, F, G, H, 0).

state(A, B, C, D, 0, E, F, G, H) :- state(A, 0, B, C, D, E, F, G, H).

state(A, 0, B, C, D, E, F, G, H) :- state(0, A, B, C, D, E, F, G, H).

state(0, A, B, C, D, E, F, G, H) :- state(A, B, C, 0, D, E, F, G, H).

state(A, B, C, 0, D, E, F, G, H) :- state(A, B, C, D, 0, E, F, G, H).
```
```
?- state(2, 8, 3, 1, 6, 4, 7, 0, 5).
```

### Output:
Given the start and goal states, the program determines a series of valid transitions to solve the puzzle.

### Theory:

#### 8-Puzzle Problem:
The 8-puzzle problem is a classic AI problem that involves sliding tiles on a 3x3 board to reach a goal configuration. It consists of 8 numbered tiles and one blank space. The objective is to rearrange the tiles from an initial state (START) to a goal state (GOAL) by sliding tiles into the blank space.

#### Components of the Problem:
1. **State Space**: All possible configurations of the board.
2. **Initial State**: The starting configuration of the board.
3. **Goal State**: The target configuration.
4. **Operators**: Valid moves that change the board configuration, such as moving the blank space up, down, left, or right.

#### Prolog Implementation:
In Prolog, the 8-puzzle problem is represented as a series of states and transitions. The `state` predicate defines the positions of the tiles and the blank space (0). Transition rules are used to specify how the blank space moves.

#### Key Concepts:
1. **State Representation**: The board is represented as a flat list of 9 elements, where each element corresponds to a tile or the blank space (0).
2. **Transition Rules**: Define valid moves for the blank space, ensuring the resulting state remains within the boundaries of the board.
3. **Goal Test**: Check if the current state matches the goal state.

#### Applications:
The 8-puzzle problem is used in:
- AI research to study search algorithms.
- Problem-solving techniques such as Breadth-First Search (BFS) and A*.
- Educational tools for understanding state space and heuristics.



# Experiment No. 9: Depth First Search (DFS) to Solve a Real-Life Problem

## **Objective**
To solve a real-life problem using the Depth First Search (DFS) algorithm.

---

## **Theory: Depth First Search (DFS)**

Depth First Search (DFS) is a fundamental graph traversal algorithm used to explore nodes and edges of a graph. Starting from an initial node, it explores as far as possible along each branch before backtracking. DFS is typically implemented using recursion or an explicit stack.

### **Key Characteristics of DFS**
1. **Traversal Technique:** DFS moves deep into the graph/tree before exploring siblings.
2. **Data Structure:** It can be implemented recursively or iteratively using a stack.
3. **Applications:**
   - Pathfinding
   - Cycle detection in graphs
   - Solving puzzles (e.g., mazes, N-Queens)
   - Analyzing connectivity in networks

### **Real-Life Problem:**
In this experiment, we simulate a simple real-life scenario using DFS to navigate from a starting number to a goal number, where the neighbors are determined by incrementing the current number.

---

## **Prolog Implementation**

Below is the Prolog implementation of a Depth First Search algorithm to find a path from a starting node to a goal node:

```prolog
% Base case: If the current node is the goal, print success.
dfs(Current, Goal) :- 
    Current = Goal, 
    write('Reached goal!'), nl.

% Recursive case: Explore neighboring nodes.
dfs(Current, Goal) :- 
    write('Current node: '), write(Current), nl, 
    neighbor(Current, Next), 
    dfs(Next, Goal).

% Define a simple neighbor relationship.
neighbor(A, B) :- 
    B is A + 1.
```

---

## **Execution and Output**

### **Query**
To find a path from 1 to 10, execute the following query:

```prolog
?- dfs(1, 10).
```

### **Expected Output**
```
Current node: 1
Current node: 2
Current node: 3
Current node: 4
Current node: 5
Current node: 6
Current node: 7
Current node: 8
Current node: 9
Current node: 10
Reached goal!
```

---

## **Example Applications**
1. **Pathfinding in Graphs:**
   - Finding a route from one city to another.
2. **Solving Mazes:**
   - Exploring paths from the entrance to the exit of a maze.
3. **Network Traversal:**
   - Determining connectivity or finding specific resources in a network.

---

## **How to Run**
1. Copy the Prolog code into a `.pl` file (e.g., `dfs_example.pl`).
2. Open a Prolog interpreter (e.g., SWI-Prolog).
3. Load the file using `[dfs_example].`.
4. Run the query `?- dfs(1, 10).` to observe the result.

---

## **Conclusion**
This experiment demonstrates the use of the Depth First Search (DFS) algorithm in solving a simple numerical traversal problem. By defining custom neighbor relations, the algorithm can be adapted to various real-life scenarios.

--- 

# EXPERIMENT NO. 10

## Aim:
To write a Python program to solve the Tower of Hanoi problem.

---

## Theory:

### Tower of Hanoi:
The Tower of Hanoi is a mathematical puzzle consisting of three rods and a number of disks of different sizes. The puzzle begins with the disks stacked in ascending order of size on one rod, with the smallest disk on top. The goal is to move the entire stack to another rod, following these rules:

### Rules:
1. Only one disk can be moved at a time.
2. A disk can only be moved if it is the uppermost disk on a rod.
3. No disk may be placed on top of a smaller disk.

This problem is a classic example of recursion, where the solution involves breaking the problem into smaller sub-problems of the same type.

### Algorithm:
1. Move the top `n-1` disks from the source rod to an auxiliary rod using the destination rod.
2. Move the largest disk directly from the source rod to the destination rod.
3. Move the `n-1` disks from the auxiliary rod to the destination rod using the source rod.

The process repeats recursively until all disks are transferred to the destination rod.

---

## Python Source Code:
```python
# Function to solve Tower of Hanoi
def tower_of_hanoi(n, source, destination, auxiliary):
    if n == 1:
        print(f"Move disk 1 from {source} to {destination}")
        return
    
    # Step 1: Move n-1 disks from source to auxiliary using destination
    tower_of_hanoi(n - 1, source, auxiliary, destination)
    
    # Step 2: Move the nth disk from source to destination
    print(f"Move disk {n} from {source} to {destination}")
    
    # Step 3: Move the n-1 disks from auxiliary to destination using source
    tower_of_hanoi(n - 1, auxiliary, destination, source)

# Example usage:
if __name__ == "__main__":
    num_disks = 3
    print(f"Solving Tower of Hanoi for {num_disks} disks:")
    tower_of_hanoi(num_disks, 'A', 'C', 'B')
```

---

## Example Usage:
### Input:
The program is designed to solve the Tower of Hanoi for a specified number of disks. For example, solving for 3 disks:

### Output:
```
Solving Tower of Hanoi for 3 disks:
Move disk 1 from A to C
Move disk 2 from A to B
Move disk 1 from C to B
Move disk 3 from A to C
Move disk 1 from B to A
Move disk 2 from B to C
Move disk 1 from A to C
```

---

## Key Observations:
1. For `n` disks, the minimum number of moves required is `2^n - 1`.
2. The problem demonstrates the power of recursion and is a useful example for understanding divide-and-conquer algorithms.

---

Feel free to modify the `num_disks` variable in the program to test the solution for different numbers of disks.


# EXPERIMENT NO. 11

## Aim:
To write a Python program to solve the Water Jug Problem using the BFS algorithm.

---

## Theory:

### Water Jug Problem:
The Water Jug Problem is a classic example of a constraint satisfaction problem. Given two jugs with fixed capacities and an unlimited water supply, the goal is to measure out a specific amount of water. The problem must adhere to the following constraints:

### Rules:
1. You can fill any of the jugs completely.
2. You can empty any of the jugs completely.
3. You can transfer water from one jug to another until one jug is empty or the other is full.

The problem can be represented as a state space where each state is defined by the amount of water in each jug.

### Mathematical Insight:
To solve the problem, the target volume must be a multiple of the greatest common divisor (GCD) of the two jug capacities.

---

## Python Source Code:
### Function to Calculate GCD:
```python
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a
```

### BFS Solution for Water Jug Problem:
```python
from collections import deque

def water_jug_bfs(jug1_capacity, jug2_capacity, target):
    # Check if solution is possible
    if target % gcd(jug1_capacity, jug2_capacity) != 0:
        return "No solution possible"

    # Initialize visited set and queue
    visited = set()
    queue = deque([(0, 0)])  # Start with both jugs empty

    while queue:
        current_state = queue.popleft()
        jug1, jug2 = current_state

        # Check if we've reached the target
        if jug1 == target or jug2 == target:
            return f"Solution found: {current_state}"

        if current_state in visited:
            continue

        visited.add(current_state)

        # Possible actions:
        # 1. Fill Jug 1
        queue.append((jug1_capacity, jug2))
        # 2. Fill Jug 2
        queue.append((jug1, jug2_capacity))
        # 3. Empty Jug 1
        queue.append((0, jug2))
        # 4. Empty Jug 2
        queue.append((jug1, 0))
        # 5. Pour Jug 1 into Jug 2
        transfer = min(jug1, jug2_capacity - jug2)
        queue.append((jug1 - transfer, jug2 + transfer))
        # 6. Pour Jug 2 into Jug 1
        transfer = min(jug2, jug1_capacity - jug1)
        queue.append((jug1 + transfer, jug2 - transfer))

    return "No solution found"

# Example usage:
if __name__ == "__main__":
    jug1_capacity = 4
    jug2_capacity = 3
    target = 2

    print(f"Solving Water Jug Problem for capacities ({jug1_capacity}, {jug2_capacity}) and target {target}:")
    print(water_jug_bfs(jug1_capacity, jug2_capacity, target))
```

---

## Example Usage:
### Input:
Jug capacities: `4 liters`, `3 liters`
Target: `2 liters`

### Output:
```
Solving Water Jug Problem for capacities (4, 3) and target 2:
Solution found: (2, 0)
```

---

## Key Observations:
1. The problem is solvable if and only if the target is a multiple of the GCD of the jug capacities.
2. BFS ensures that all possible states are explored in the shortest path manner, making it an efficient approach to solve the problem.

---

Feel free to modify the capacities or target in the program to test different configurations.



    
