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
    
