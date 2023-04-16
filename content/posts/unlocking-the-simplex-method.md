---
title: Unlocking the Simplex Method
subtitle: A linear algebraic approach
category:
  - Mathematics
author: El Ghemary Farah
date: 2022-04-16T02:16:24.940Z
featureImage: /uploads/fractal-2173803_1920.jpg
---
Imagine you're a computer Scientist tasked to optimize a real-life problem. You know that the best way to find the optimal solution is to use the simplex method. As a mathematics undergraduate, this is how I first encountered the simplex method, and I was stressed out and overwhelmed by the sheer amount of complicated calculations involved. It didn't make any sense, and I found it difficult to use it for solving real-life Problems. However, everything changed when I started visualizing the calculations in terms of vectors and planes, everything click into place. In this Article, I want to share my understading of the simplex method, and show you how to use Linear Algebra to think about it in an ituitive way. Whether you're a fellow math student or a math enthousiast looking to deeping your understanding of the Simplex Method.   

> Linear Programming is a generalization of Linear Algebra. It is capable of handling a variety of problems, ranging from ﬁnding schedules for airlines or movies in a theater to distributing oil from reﬁneries to markets. The reason for this great versatility is the ease at which constraints can be incorporated into the model\
> -- Steven J. Miller (2007) An Introduction to Linear Programming.   

Many real-life problems can be formulated as linear programs, hence LPs are a mathematical modeling technique to determine the best possible solution given a set of constraints and objectives. For example Maximizing the profit of a company, or minimize their production costs.

Let's Consider the following example of an LP

![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20%5Cleq%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20%5Cleq%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2%20%5Cgeq%200)

To ensure that our model is indeed a linear program, it must satisfy three conditions: 

* ﻿All variables are continuous
* ﻿The objective and constraints are linear.
* ﻿There must be a s single objective to either maximize or minimize the function.

### The Standardization of an LP

The Simplex method requires a standard form of the LP to work properly, which means satisfying this two requirements:     

* all the constraints are equations. This restriction ensures that we have a fixed amount of resources and it is easier to manipulate and analysis our LP, it allows us to use algebraic techniques to solve it.       
* The right hand side and all the variables are non negative. The right hand side represents the resources available, This restriction ensures that the feasible region is closed and bounded, and it ensures that we are not dealing with negative resources which is impossible in the real-world.    

**To standardize our LP :**

* converting (=<) inequalities into equations : we add a non negative slack variable to the left hand side, which represents the unused amount of resources
* converting (>=) inequalities into equations : we substrate a non negative surplus variable, which represents how much we exceeds the limits.    

Considering the example I previously mentioned, the standard form for the LP would be:

![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20&plus;%20x_3%20=%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20&plus;%20x_4%20=%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2,%20x_3,%20x_4%20%5Cgeq%200)

The fundamental idea of the simplex method is to improve the feasible solution at each iteration until we reach the optimal one. summarized as the following algorithm

1. Start with an initial feasible solution.
2. Check if the current solution is optimizing my function. If it is, stop and return the solution.
3. If it is not optimal, find a neighboring feasible solution that improves the objective function.
4. Repeat steps 2-3 until the optimal solution is found.

What dos that mean Geometrically ? 

The fundamental theorem of linear programming provides us with an important insight : if our set of feasible solutions is a convex set, we can assume that the optimal solution is one of the vertices of the feasible polytope. This property allows us to iterate efficiently a dramatically reduced number of solutions.     

Using this insight, let's improve our previous algorithm

1. Choose an initial feasible solution, which corresponds to a vertex of the feasible region.
2. Check if the current solution is optimizing my function. If it is, stop and return the solution.
3. If not, examine the neighboring vertices to find the one that improves the objective function the most.
4. Move to that neighboring vertex and continue the process from step 2 until we reach the optimal solution.

## To modify

Let's Apply this to the previous example of our LP

1. Let's choose the origin as the initial vertex (0,0)

  ![](https://latex.codecogs.com/svg.image?x_1%20=%20x_2%20=%200) ![](https://latex.codecogs.com/svg.image?x_3&space;=&space;3,&space;x_4&space;=&space;5&space;and&space;z&space;=&space;0)\
  ![alt text](https://github.com/elghemary/farah/assets/uploads/(0.0).png?raw=true)

2. Choose a neighbor :

   from the graph we can see the moving from the origin to the vertex in ![](https://latex.codecogs.com/svg.image?x_2) will increase our objective function faster than the vertex in ![](https://latex.codecogs.com/svg.image?x_1)

   so we choose ![](https://latex.codecogs.com/svg.image?x_1) as the basic
3. Choose the one that gets to zero first

   If we increases ![](https://latex.codecogs.com/svg.image?x_2) then ![](https://latex.codecogs.com/svg.image?x_4) decreases to

   so ![](https://latex.codecogs.com/svg.image?x_4) is the non-basic
4. (0,5) is our current vertex:

   ![](https://latex.codecogs.com/svg.image?x_3%20=%203%20-%20x_1%20=%203)

   ![](https://latex.codecogs.com/svg.image?z%20=%2010)

## To modify

### A linear Algebraic Approach of the Algorithm

The feasible solution set of a linear program can be defined Algebraically as a linear combination of basis vectors. These basis vectors are selected in such a way that they span the solution set. To obtain these basis vectors we start by writing our linear system in the form of matrices. 

Given our previous example,  We define A as the Matrix that represents the coefficients of our constraints A = 

Since the feasible solution set is defined by the 2 constraints of our LP, we must define the basis with 2 vectors. Therefore,  we can then generate 6 submatrices from A.

To reduce these vectors basis into feasible bases, we must ensure that they're invertible to satisfy Bx=b (then being able to find the feasible solution)

By finding a basis for a feasible solution, we are essentially identifying the set of basic variables that correspond to a particular corner point of the feasible region. This translate into moving from one basic feasible solution to another, which does improve our function.

After reducing the feasible set, the final step is to calculate the reduced cost function related to each basis. If the fucntion is postive, we still have resources that can be used, indicating our solution is not optimal. If it is negative, we have used all our resources, and we found the basis of our LP. Congratulation! the solution calculated using this basis is a  BFS