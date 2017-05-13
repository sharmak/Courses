## MOOC link 
https://www.edx.org/course/optimization-methods-business-analytics-mitx-15-053x
## Introduction (Lecture 1)
 * Opitmization is finding the best solution
   * Find the best strategy
   * Find the best product 
   * Find the best use of time
   * Maximize profit
   * Minimize cost
   * Find the shortest path 
* Optimization is everywhere
  * Mathematical Model 
  * Real world problem to mathematical model
* When an optimization model is useful in practice ? 
  * All models are wrong but some are useful (George Box)
* Application 
   * Marketing
   * Finance
   * Many more
* Optimization Problem
  * Given a collection of numbers partition them inot two groups such that the difference in the sums as small as possible.
  * Example 7, 10, 13, 17, 20, 22
     * {7, 17, 20} {10, 13, 22}
  * Exercise {1,2,4,8,16, 32} 
     * Best Partition {1,2,4,8,16} {32}
  * Tom pie eating contest
     * Tom is in pie eating contest that lasts 1 hour
     * Each tore that he eats takes 2 minutes
     * Each apple pie that he eats takes 3 minutes
     * He receives 4 points for each torte
     * He receives 5 points for each pie
     * What should tom eat to maximize points?
  * Solution
     * What are decision variables (Represents Tom's decisions)
        * One way:
          * Eating Torte (x), Eating Pie (y) [4x + 5y]
        * Another way:
          * Let v be total time Tom spends in eating tortes
          * Let w be the total time Tom spends in eating pie 
     * Objective function [4x + 5y]
        * Linear function 
     * Constraints
        * Time is 60 minutes 2*x + 5*y <= 60
        * x >=0 , y >= 0  [ Non nagativity Constraints ]
        * x is integer, y is integer [Integrality Contraints ]
     * Code
``` python
from scipy.optimize import linprog
A = np.array([[2, 5]])
c = np.array([4,5])
b = np.array([60])
linprog(c, A, b, bounds=((0,None), (0, None)),options={"disp":True})
```
 * Optimization Paradigm
   * Objective function
     * Minimize cost or 
     * Maximize expected return
   * Constraints
     * Must be linear equalities or inequalities
     * \> or < are not permitted
 * Non Linear Optimization Problems
   * Objective function does not need to be linear
   * Constraints doesn't need to be linear
   * Example max 9v + 13w st v*w <= 10 v >= 0 w > 0 
   * Non linear programs are harder to solve 
 
 * Optimization Tricks
  * Absolute constraints
    * We now know how to transform constraints of the form |ax+by| <= c. We convert them into two constraints
    * We can use the same logic for |ax+by|>= c as the region for the contraints becomes non convex which can't be solved by LP as the feasbile region must be a bounded area.
  * Max Min constraints
    * Max min {50x1, 25x2, 20x3, 14x4}
    * Add new constraints Max {z} with constraints z <= 50x1 z <= 25x2  z <= 20x3 z <= 14x4
    * We can use the Min max problems as well 
  * Ratio Constraints
    * Idea is to use the denominator and convert the equation to linear equation.
    
    

