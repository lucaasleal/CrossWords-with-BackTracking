# Crossword Generator — AI Constraint Satisfaction

This project implements an AI capable of generating **Crossword Puzzles** from scratch. It models the puzzle as a **Constraint Satisfaction Problem (CSP)** and solves it using **Backtracking Search** combined with powerful heuristics and inference algorithms like **AC-3**.

## 🧠 Project Idea

The core challenge is to fill a grid of empty slots with words from a vocabulary list such that all constraints are satisfied.
* **Unary Constraints:** Every word must be the correct length for its slot.
* **Binary Constraints:** Where two words cross, they must share the same character (e.g., if "Horizontal 1" crosses "Vertical 2" at the 3rd letter, both must have the same letter at that intersection).

The AI doesn't just guess randomly; it uses logic to prune impossible choices and heuristics to find the solution efficiently.

## 📊 Data Modeling

The problem is modeled as a mathematical graph where:
* **Variables:** The open slots in the puzzle (defined by row, column, direction, and length).
* **Domains:** The set of all possible words that can fill a specific slot.
* **Edges:** Represent overlaps between variables (intersections).

Input data is provided via text files:
* `structure.txt`: Defines the grid layout (`#` for walls, `_` for empty spaces).
* `words.txt`: A dictionary of available words to use.

## ⚙️ Technologies Used

* **Python 3**
* **Constraint Satisfaction Problems (CSP)**
* **Backtracking Search** (Recursive algorithm)
* **AC-3 Algorithm** (Arc Consistency for inference)
* **Heuristics:** MRV (Minimum Remaining Values), Degree Heuristic, LCV (Least Constraining Value)
* **Pillow (PIL)**: Library used to generate the final image of the crossword.

## 🧩 How the Algorithm Works

1.  **Enforce Consistency:** Before searching, the AI uses **AC-3** to enforce Arc Consistency, removing words from domains that fundamentally conflict with neighbors.
2.  **Variable Selection:** It chooses which slot to fill next using **MRV** (fewest options left) and **Degree Heuristic** (most neighbors), following the "fail-first" principle.
3.  **Value Selection:** It chooses which word to try using **LCV** (Least Constraining Value), picking words that rule out the fewest options for neighbors ("fail-last").
4.  **Backtracking:** It recursively attempts to fill the grid. If a conflict arises, it backtracks (undoes the last step) and tries a different word.

## ▶️ How to Run the Project

Clone the repository and navigate to the project directory:

```bash
git clone [https://github.com/lucaasleal/CrossWords-with-BackTracking.git](https://github.com/lucaasleal/CrossWords-with-BackTracking.git)
cd CrossWords-with-BackTracking
```

Requirements: You will need to install the Pillow library to generate image outputs:
```bash
pip install Pillow
```

Run example with provided data:
```bash
python generate.py data/structure1.txt data/words1.txt output.png
```

## Outputs

📌 Example
<img width="1400" height="900" alt="image" src="https://github.com/user-attachments/assets/43d3cd1f-6541-4ea6-994f-5265da1e6ce9" />


## 🚀 Possible Improvements
Implement Forward Checking during the backtracking loop.\
Optimize the revise function for larger vocabularies.\
Add a GUI to create custom structures visually.

## 📚 Inspiration
Inspired by CS50’s Introduction to Artificial Intelligence, specifically the module on Optimization and Constraint Satisfaction Problems.

## 👤 Author
@lucaasleal
