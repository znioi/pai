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
% Define the board size
board_size(4).

% Define the valid range for rows and columns
valid_pos(P) :- board_size(N), between(1, N, P).

% Define the attack predicate
attack(R1, C1, R2, C2) :-
    R1 =:= R2;             % Same row
    C1 =:= C2;             % Same column
    abs(R1 - R2) =:= abs(C1 - C2).  % Diagonal

% Place queens on the board
place_queens([], []).
place_queens([R|Rs], [C|Cs]) :-
    valid_pos(R), valid_pos(C),
    no_attack(R, C, Rs, Cs),
    place_queens(Rs, Cs).

% Check for no attacks
no_attack(_, _, [], []).
no_attack(R, C, [R1|Rs], [C1|Cs]) :-
    \+ attack(R, C, R1, C1),
    no_attack(R, C, Rs, Cs).

% Solve the 4-Queens problem
solve_queens(Queens) :-
    board_size(N),
    numlist(1, N, Rows),
    permutation(Rows, Queens),
    place_queens(Queens, _).

% Find and print all solutions
find_solutions(Solutions) :-
    findall(Q, solve_queens(Q), Solutions).

% Example usage
?- find_solutions(Solutions), length(Solutions, Count), write('Total solutions: '), write(Count).
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



    
