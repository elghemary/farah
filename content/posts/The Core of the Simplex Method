---
title: The Core of the Simplex Method
subtitle: The Geometrical Intuition Behind an Optimization Algorithm
category:
  - Mathematics
author: El Ghemary Farah
date: 2023-04-05T15:24:59.781Z
featureImage: /uploads/1.jpg
---

Imagine you're a computer Scientist tasked to optimize a real-life problem. You know that the best way to find the optimal solution is to use the simplex method. As a mathemathics undergraduate, this is how I first encountered the simplex method, and I was stressed out and overwhelmed by the sheer amount of complicated calculations involved. It didn't make any sense, and I found it difficult to use it for solving real-life Problems.
However, everything changed when I started visualizing the calculations in terms of vectors and planes that everything click into place. In this Article, I want to share my understading of the simplex method, and show how to think about it in an ituitive way. Whether you're a fellow math student or a math enthousiast looking to deeping your understanding of optimization.

>"Linear Programming is a generalization of Linear Algebra. It is capable of handling a variety of problems, ranging from ﬁnding schedules for airlines or movies in a theater to distributing oil from reﬁneries to markets. The reason for this great versatility is the ease at which constraints can be incorporated into the model" by Steven J. Miller (2007) An Introduction to Linear Programming."

Many real-life problems can be formulated as linear porgrams, hence LPs are a mathematical modeling technique in which the objective is to maximize or minimize a certain output. For example, maximizing the profit of a certai company or minimizing the cost and the time of producing a certain product.

let's take an example of a linear program and build our explanation on it :

![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20%5Cleq%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20%5Cleq%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2%20%5Cgeq%200)

To make sure that our model is indeed a linear program, it should verify this three conditions: 
	*All variables are continuous
	*The objective and constraints are linear 
	*there is single objective maximize or minimise not both 

Now, as you might already know the simplex method comes as an answer for the limitations of the graphical method. Instead of solving Linear Programs (LPs) of 2 variables, With this method we are able to solve LPs of n variables. However, before tackling the intuitive idea of this method, I'd like to take a look at the [Wikipedia](https://en.wikipedia.org/wiki/Simplex) definition of a "Simplex" 
>a simplex is a generalization of the notion of triangle or tetrahedron. The simplex is so-named because it represents the simplest possible polytope in any given space."

Keep it in mind, it will make sence in the end of this article
**Optimization Jargon:**
It is important ot make sure that we're not confusing the basic Technical terms:
*Convex Set :* a set where any two point of the subset, the line segment joining them is in the subset 

*Feasible Solution :* the solutions satisfying all the constraints 

*Infeasible solution :* the solutions that do not satisfies one or more constraints

*Optimal Solution :* the best feasible solution

*Extreme Point :* the vertex or the corner of the feasible solution

**Standardizing an LP**
the Simplex method requires a standard LP to work properly, which means ackuiring this two requirements: 
	1. all the constraints are equations.
	*this restriction ensures that we have a fixed amount of resources and it is easier to manipulate and analyse our LP, it allows us to use algebraic techniques to solve it
	2. The righ hand side and all the variables are non negative.
	*The right hand side represents the resources available, This restriction ensures that the feasible region is closed and bounded, and it ensures that we are not dealing with negative resources which is impossible in the real-world

To standardize our LP :

converting (=<) inequalities into equations : we add a non negative slack variable to the left hand side, which represents the unused amount of resources

converting (>=) inequalities into equations : we substrate a non negative surplus variable, which represents how much we exceeds the limits.
For our previous example it is gonna be 
Example 
![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20&plus;%20x_3%20=%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20&plus;%20x_4%20=%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2,%20x_3,%20x_4%20%5Cgeq%200)

Now here is a graph of our standarized LP

Now the fundemental idea of the simplex method algorith is to improve the solution at each iteration, which means we have already the fesible region which represents our solutions
	Take on solution
	is the next solution optimizing my function 
	if no
		take the next solution 
		repeat the 2
	if yes
		congratulations you found the optimal solution 
