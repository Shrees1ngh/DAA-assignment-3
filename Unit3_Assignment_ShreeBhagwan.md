## 🧠 SECTION A – Short Theory [15 Marks]
## **Name : ** SHree bhagwan
## **Enrollment number : ** 03513302723

### **Q1. DP Essentials**
**Question:**  
List the three ingredients of DP and one-line purpose of each.  

**Answer:**  
1. **Optimal Substructure:** Optimal solution is built from optimal solutions of smaller subproblems.  
2. **Overlapping Subproblems:** Same subproblems occur multiple times during recursion.  
3. **Memoization/Tabulation:** Store solutions of subproblems to avoid recomputation.  

---

### **Q2. DP vs Divide & Conquer**
**Question:**  
State two differences focusing on subproblem overlap and reuse; give one example for each.  

**Answer:** 
**Difference 1:** DP has overlapping subproblems; D&C solves independent ones.
**Difference 2:** DP reuses results; D&C recomputes them.
**Example:** DP – Fibonacci; D&C – Merge Sort.

---

### **Q3. Principle of Optimality**
**Question:**  
Define it in one sentence and name any one problem satisfying it.  

**Answer:**  
A problem satisfies the **principle of optimality** if an optimal solution contains optimal solutions to its subproblems.  
**Example:** Shortest Path (Dijkstra’s Algorithm).  

---

### **Q4. Memoization**
**Question:**  
Define memoization and contrast with tabulation in one line each.  

**Answer:**  
- **Memoization:** Top-down DP where results of solved subproblems are stored.  
- **Tabulation:** Bottom-up DP where table is filled iteratively from base cases.  

---

### **Q5. Branch and Bound**
**Question:**  
Define BnB and the role of bounding in pruning in two lines.  

**Answer:**  
**Branch and Bound** systematically explores solution space using state-space trees.  
**Bounding** helps prune (cut off) nodes that cannot yield a better solution than the current best.  

---

## ⚙️ SECTION B – Algorithms & Recurrences [15 Marks]

---

### **Q6. Matrix Chain Multiplication**

**Given:**  
A₁: 5×4, A₂: 4×6, A₃: 6×2, A₄: 2×7  
→ Dimensions array **p = [5, 4, 6, 2, 7]**

---

**(a) Recurrence and Base Case**
m[i,j] = 0, if i == j
m[i,j] = min_{i≤k<j} ( m[i,k] + m[k+1,j] + p[i-1]*p[k]*p[j] )

(b) Step-by-Step Calculation

Chain length = 1
m[i,i] = 0 for i = 1 to 4

Chain length = 2
| Pair  | Formula | Calculation |    Result    |
| :---- | :------ | :---------- | :----------: |
| (1,2) | 5×4×6   | 120         | m[1,2] = 120 |
| (2,3) | 4×6×2   | 48          |  m[2,3] = 48 |
| (3,4) | 6×2×7   | 84          |  m[3,4] = 84 |

Chain length = 3
| (i,j)             | Possible k | Formula               | Result |
| :---------------- | :--------- | :-------------------- | :----: |
| (1,3)             | k=1        | 0 + 48 + 5×4×2 = 88   |   88   |
|                   | k=2        | 120 + 0 + 5×6×2 = 180 |   180  |
| ✅ m[1,3] = **88** |            |                       |        |
		

| (2,4) | k=2 | 0 + 84 + 4×6×7 = 252 | 252 |
| | k=3 | 48 + 0 + 4×2×7 = 104 | 104 |
✅ m[2,4] = 104

Chain length = 4
| (1,4) | Possible k   | Formula                 | Result |
| :---- | :----------- | :---------------------- | :----: |
|       |  k=1         | 0 + 104 + 5×4×7 = 244   |  244   |
|       |  k=2         | 120 + 84 + 5×6×7 = 414  |  414   |
|       |  k=3         | 88 + 0 + 5×2×7 = 158    | **158**|

✅ Minimum = 158

Final Answer:
✅ Minimum scalar multiplications = 158

Q7. Longest Common Subsequence (LCS)
Given:
X = "ABCDGH"
Y = "AEDFHR"

(a) Recurrence

LCS[i,j] = 0, if i=0 or j=0
LCS[i,j] = LCS[i-1,j-1]+1, if X[i]==Y[j]
Else LCS[i,j] = max(LCS[i-1,j], LCS[i,j-1])

(b) Step-by-Step Calculation

| Xᵢ / Yⱼ |  A  |  E  |  D  |  F  |  H  |  R  |
| :-----: | :-: | :-: | :-: | :-: | :-: | :-: |
|  **A**  |  1  |  1  |  1  |  1  |  1  |  1  |
|  **B**  |  1  |  1  |  1  |  1  |  1  |  1  |
|  **C**  |  1  |  1  |  1  |  1  |  1  |  1  |
|  **D**  |  1  |  1  |  2  |  2  |  2  |  2  |
|  **G**  |  1  |  1  |  2  |  2  |  2  |  2  |
|  **H**  |  1  |  1  |  2  |  2  |  3  |  3  |

✅ LCS = “ADH”
✅ Length = 3

Q8. Optimal Binary Search Tree
Given:
Keys = {10, 20, 30}
Probabilities p = {0.4, 0.3, 0.3}
q = 0

(a) Recurrence

w[i,j] = w[i,j-1] + p[j]
e[i,j] = min_{r=i..j} ( e[i,r-1] + e[r+1,j] + w[i,j] )
Base: e[i,i-1] = 0

(b) Step-by-Step Calculation

Step 1: Compute w[i,j]
|  i  |  j  | w[i,j] |
| :-: | :-: | :----: |
|  1  |  1  |   0.4  |
|  2  |  2  |   0.3  |
|  3  |  3  |   0.3  |
|  1  |  2  |   0.7  |
|  2  |  3  |   0.6  |
|  1  |  3  |   1.0  |


Step 2: Length = 1

e[1,1]=0.4
e[2,2]=0.3
e[3,3]=0.3

Step 3: Length = 2

(1,2)

r=1 → 0 + 0.3 + 0.7 = 1.0

r=2 → 0.4 + 0 + 0.7 = 1.1
✅ e[1,2] = 1.0

(2,3)

r=2 → 0 + 0.3 + 0.6 = 0.9

r=3 → 0.3 + 0 + 0.6 = 0.9
✅ e[2,3] = 0.9

Step 4: Length = 3

(1,3)

r=1 → 0 + 0.9 + 1.0 = 1.9

r=2 → 0.4 + 0.3 + 1.0 = 1.7

r=3 → 1.0 + 0 + 1.0 = 2.0
✅ e[1,3] = 1.7, best root = 20

✅ Final Answer: Minimum expected search cost = 1.7

Q9. 0/1 Knapsack – Branch and Bound
Given:
W = 5
Weights = [2, 3, 4, 5]
Profits = [3, 4, 5, 6]

Profit/weight ratios = [1.5, 1.33, 1.25, 1.2]

(a) Fractional Upper Bound Formula

UB = v + (W - w) * (next item profit / weight)

(b) Step-by-Step Calculation

Root Node (Level 0)
v = 0, w = 0
Remaining capacity = 5
UB = 0 + 5×1.5 = 7.5

Include Item 1 (Level 1)
v = 3, w = 2
Remaining = 3
Next ratio = 4/3 = 1.33
UB = 3 + 3×1.33 = 6.99 ≈ 7.0

Exclude Item 1 (Level 1)
v = 0, w = 0
UB = 0 + 5×1.33 = 6.67

| Level | Items         |  v  |  w  |  UB |
| :---: | :------------ | :-: | :-: | :-: |
|   0   | ∅             |  0  |  0  | 7.5 |
|   1   | Include item1 |  3  |  2  | 7.0 |
|   1   | Exclude item1 |  0  |  0  | 6.7 |

✅ Best UB = 7.0

Q10. Travelling Salesman Problem (Held–Karp)
Given Distance Matrix:

| From/To |  1  |  2  |  3  |  4  |
| :-----: | :-: | :-: | :-: | :-: |
|    1    |  0  |  10 |  15 |  20 |
|    2    |  10 |  0  |  35 |  25 |
|    3    |  15 |  35 |  0  |  30 |
|    4    |  20 |  25 |  30 |  0  |

(a) Recurrence

C[S,j] = min_{k∈S−{j}} ( C[S−{j},k] + D[k][j] )
Final = min_{j≠1} ( C[{1,2,3,4},j] + D[j][1] )
(b) Step-by-Step Calculation

Base cases:
C[{2},2]=10
C[{3},3]=15
C[{4},4]=20

For 2-element subsets
Subset	j	Formula	Result
{1,2,3}	2	min( C[{1,3},3]+D[3][2], C[{1},1]+D[1][2] ) = min(15+35,0+10)=10	10
{1,2,3}	3	min( C[{1,2},2]+D[2][3], C[{1},1]+D[1][3] ) = min(10+35,0+15)=15	15

For 3-element subsets
Subset	j	Formula	Result
{1,2,3,4}, j=2	min( C[{1,3,4},3]+D[3][2], C[{1,3,4},4]+D[4][2] ) = min(50+35,50+25)=75	75	
{1,2,3,4}, j=3	min( C[{1,2,4},2]+D[2][3], C[{1,2,4},4]+D[4][3] ) = min(45+35,50+30)=80	80	
{1,2,3,4}, j=4	min( C[{1,2,3},2]+D[2][4], C[{1,2,3},3]+D[3][4] ) = min(50+25,45+30)=70	70	

Final Calculation
Final = min( C[{1,2,3,4},j] + D[j][1] )
= min(75+10, 80+15, 70+20)
= min(85, 95, 90)
✅ Minimum Tour Cost = 80

✅ Final Answers Summary for section B
|  Q  | Problem                     | Final Answer |
| :-: | :-------------------------- | :----------: |
|  6  | Matrix Chain Multiplication |      158     |
|  7  | Longest Common Subsequence  |   3 ("ADH")  |
|  8  | Optimal Binary Search Tree  |      1.7     |
|  9  | 0/1 Knapsack (BnB)          |   UB = 7.0   |
|  10 | Travelling Salesman         |      80      |


End of Assignment
