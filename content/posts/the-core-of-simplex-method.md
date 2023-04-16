---
title: The Core of Simplex Method
subtitle: A Linear Algebraic approach
category:
  - Mathematics
author: El Ghemary Farah
date: 2023-04-16T15:04:28.069Z
featureImage: /uploads/(3.2).png
---
The simplex method is one of the best ways to optimize a real-life problem. As a mathematics undergraduate, this is how I first discovered this algorithm. However, I was overwhelmed by the sheer amount of the complicated calculations involved. First, It didn't make any sense, but everything click into place when I started visualizing the calculations in terms of vectors and planes.

 In this Article, I want to share my understanding of the simplex method, and show you how to use Linear Algebra to think about it in an intuitive way. Whether you're a fellow math student or a math enthusiast looking to deepen your understanding of the Simplex Method.   

> Linear Programming is a generalization of Linear Algebra. It is capable of handling a variety of problems, ranging from ﬁnding schedules for airlines or movies in a theater to distributing oil from reﬁneries to markets. The reason for this great versatility is the ease at which constraints can be incorporated into the model\
> -- Steven J. Miller (2007) An Introduction to Linear Programming.   

Many real-life problems can be formulated as linear programs, hence LPs are a mathematical modeling technique to determine the best possible solution given a set of constraints and objectives. For example Maximizing the profit of a company, or minimize their production costs.

Let's Consider the following example of an LP

![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20%5Cleq%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20%5Cleq%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2%20%5Cgeq%200)

To ensure that our model is indeed a linear program, it must satisfy three conditions: 

* ﻿All variables are continuous
* ﻿The objective and constraints are linear.
* ﻿There must be a single objective to either maximize or minimize the function.

#### The Standardization of an LP

The Simplex method requires a standard form of the LP to work properly, which means satisfying this two requirements:     

* All the constraints are equations. This restriction ensures that we have a fixed amount of resources and it is easier to manipulate and analysis our LP, it allows us to use algebraic techniques to solve it.       
* The right hand side and all the variables are non negative. The right hand side represents the resources available, This restriction ensures that the feasible region is closed and bounded, and it ensures that we are not dealing with negative resources which is impossible in the real-world.    

To standardize our LP :

* converting (<) inequalities into equations : we add a non negative slack variable to the left hand side, which represents the unused amount of resources
* converting (>) inequalities into equations : we substrate a non negative surplus variable, which represents how much we exceeds the limits.    

Considering the example I previously mentioned, the standard form for the LP would be:

![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20&plus;%20x_3%20=%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20&plus;%20x_4%20=%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2,%20x_3,%20x_4%20%5Cgeq%200)

The fundamental idea of the simplex method is to improve the feasible solution at each iteration until we reach the optimal one. summarized as the following algorithm

1. Start with an initial feasible solution.
2. Check if the current solution is optimizing my function. If it is, stop and return the solution.
3. If it is not optimal, find a neighboring feasible solution that improves the objective function.
4. Repeat steps 2-3 until the optimal solution is found.

What does that mean Geometrically ? 

The fundamental theorem of linear programming provides us with an important insight : if our set of feasible solutions is a convex set, we can assume that the optimal solution is one of the vertices of the feasible polytope.   

This property allows us to iterate efficiently a dramatically reduced number of solutions. Using it we can improve our previous algorithm : 

1. Choose an initial feasible solution, which corresponds to a vertex of the feasible region.
2. Check if the current solution is optimizing my function. If it is, stop and return the solution.
3. If not, examine the neighboring vertices to find the one that improves the objective function the most.
4. Move to that neighboring vertex and continue the process from step 2 until we reach the optimal solution.

A simplex according to [Wikipedia](https://en.wikipedia.org/wiki/Simplex) :

> A generalization of the notion of triangle or tetrahedron. The simplex is so-named because it represents the simplest possible polytope in any given space.

Hence where the name "Simplex" comes from, as it refers to the fact that we are essentially moving from vertex to vertex of a simplex.

#### A linear Algebraic Approach of the Algorithm

The feasible solution set of a linear program can be defined Algebraically as a linear combination of basis vectors. These basis vectors are selected in such a way that they span the solution set. To obtain these basis vectors we start by writing our linear system in the form of matrices. 

Given our previous example,  We define A as the Matrix that represents the coefficients of our constraints 

![](https://latex.codecogs.com/svg.image?%5Cinline%20A%20=%20%5Cbegin%7Bpmatrix%7D%201%20&%200%20&%201%20&%200%20%5C%5C%201%20&%201%20&%200%20&%201%20%5C%5C%5Cend%7Bpmatrix%7D)

Since the feasible solution set is defined by 2 constraints, it is natural to define the basis with 2 vectors. Therefore,  we can then generate 6 sub-matrices from A.

![](/uploads/equation.svg)

For this sub-matrices to be a basis of our LP, it means that it spans the feasible solution set, in a another word, it satisfy the following : 

![](https://latex.codecogs.com/svg.image?\inline&space;Bx=b)

Hence, we must calculate the determinant of each sub-matrices and chose the ones that are invertible.

By finding a basis for a feasible solution, we are essentially identifying the set of basic variables that correspond to a particular corner point of the feasible region. This translate into moving from one basic feasible solution to another, which does improve our function.

After reducing the feasible set, the final step is to calculate the reduced cost function related to each basis. If the function is positive, we still have resources that can be used, indicating our solution is not optimal. If it is negative, we have used all our resources, and we found the basis of our LP. Congratulation! the solution calculated using this basis is a  BFS



In conclusion, the simplex method is a powerful algorithm, although it has some limitations, it remains one of the most widely used methods in the field of Optimization. Understanding its core principles is essential for anyone who wants to solve real-world problems efficiently and effectively