---
title: "The Core of the Simplex "
subtitle: A Geometrical Intuition
category:
  - About Awake
author: El Ghemary Farah
date: 2023-04-10T06:36:49.269Z
featureImage: /uploads/(0,5).png
---

Imagine you're a computer Scientist tasked to optimize a real-life problem. You know that the best way to find the optimal solution is to use the simplex method. As a mathemathics undergraduate, this is how I first encountered the simplex method, and I was stressed out and overwhelmed by the sheer amount of complicated calculations involved. It didn't make any sense, and I found it difficult to use it for solving real-life Problems. However, everything changed when I started visualizing the calculations in terms of vectors and planes, everything click into place. In this Article, I want to share my understading of the simplex method, and show you how to think about it in an ituitive way. Whether you're a fellow math student or a math enthousiast looking to deeping your understanding of optimization.   

>Linear Programming is a generalization of Linear Algebra. It is capable of handling a variety of problems, ranging from ﬁnding schedules for airlines or movies in a theater to distributing oil from reﬁneries to markets. The reason for this great versatility is the ease at which constraints can be incorporated into the model   
by Steven J. Miller (2007) An Introduction to Linear Programming.   

Many real-life problems can be formulated as linear porgrams, hence LPs are a mathematical modeling technique in which the objective is to maximize or minimize a certain output. For example, maximizing the profit of a certain company or minimizing the cost and the time of producing a certain product.   

let's take an example of a linear program and build our explanation on it :   

![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20%5Cleq%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20%5Cleq%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2%20%5Cgeq%200)

To make sure that our model is indeed a linear program, it should verify this three conditions:   
	* All variables are continuous    
	* The objective and constraints are linear     
	* There is single objective maximize or minimise not both     
	         
Now, as you might already know the simplex method comes as an answer for the limitations of the graphical method. Instead of solving Linear Programs of 2 variables, With this method we are able to solve LPs of n variables. However, before tackling the geometric intuition behind the algorith, I'd like to take a look at the [Wikipedia](https://en.wikipedia.org/wiki/Simplex) definition of a "Simplex":
>a simplex is a generalization of the notion of triangle or tetrahedron. The simplex is so-named because it represents the simplest possible polytope in any given space.

Keep it in mind, it will make sence in the end of this article    
    
**Optimization Jargon:**     
It is important ot make sure that we're not confusing the basic Technical terms:    
*Convex Set :* a set where any two point of the subset, the line segment joining them is in the subset     

*Feasible Solution :* the solutions satisfying all the constraints     
*Infeasible Solution :* the solutions that do not satisfies one or more constraints     
*Optimal Solution :* the best feasible solution    
*Extreme Point :* the vertex or the corner of the feasible solution   
    
**Standardizing an LP**    
The Simplex method requires a standard LP to work properly, which means ackuiring this two requirements:     
* all the constraints are equations. This restriction ensures that we have a fixed amount of resources and it is easier to manipulate and analyse our LP, it allows us to use algebraic techniques to solve it.       
* The righ hand side and all the variables are non negative. The right hand side represents the resources available, This restriction ensures that the feasible region is closed and bounded, and it ensures that we are not dealing with negative resources which is impossible in the real-world.    

**To standardize our LP :**

* converting (=<) inequalities into equations : we add a non negative slack variable to the left hand side, which represents the unused amount of resources

* converting (>=) inequalities into equations : we substrate a non negative surplus variable, which represents how much we exceeds the limits.    

For our previous example it is going to be     
     
![](https://latex.codecogs.com/svg.image?%7Bmax%7D%5C%20z%20=%20x_1%20&plus;%202x_2%20%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%7D%20s.t%5C%20%5C%20%5C%20%5C%20%20x_1%20&plus;%20x_3%20=%203,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1%20&plus;%20x_2%20&plus;%20x_4%20=%205,%5C%5C%7B%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%5C%20%7Dx_1,x_2,%20x_3,%20x_4%20%5Cgeq%200)


Now the fundemental idea of the simplex method algorithm is to improve the solution at each iteration, which means we have already the fesible region which represents our solutions    
	Take a solution    
	is the next solution optimizing my function      
	if no     
		take the next solution      
		repeat the 2    
	if yes     
		congratulations you found the optimal solution      

Now how can this scheme be transelated into a geometrical Interpretation    
Now thanks to the fundemenatl theorem of linear programming, if our set of solutions is a convex set, we can assume that the optimal solution in a vertex of the feasible polytope.     


let's improve our previous scheme :    
	choose the initial solution, which means the initial vertex    
	Check the neighboring vertex    
		if the nearest vertex increases the objective function    
			move to it   
			keep moving from vertex to vertex    
		if the all the neighboring vertices deacreses our function or do not cange it at all    
			stop the algorithm, cogratulations you found th eoptimal solution     

Let's Apply this to the previous example of our LP

1. Let's choose the origin as the initial vertex (0,0)

  ![](https://latex.codecogs.com/svg.image?x_1%20=%20x_2%20=%200) ![](https://latex.codecogs.com/svg.image?x_3&space;=&space;3,&space;x_4&space;=&space;5&space;and&space;z&space;=&space;0)      
  ![alt text](https://github.com/elghemary/farah/assets/uploads/(0.0).png?raw=true)

2. Choose a neighbor :

   from the graph we can see the moving from the origin to the vertex in ![](https://latex.codecogs.com/svg.image?x_2) will increase our objective function faster than the vertex in ![](https://latex.codecogs.com/svg.image?x_1)

   so we choose ![](https://latex.codecogs.com/svg.image?x_1) as the basic
3. Choose the one that gets to zero first

   If we increases ![](https://latex.codecogs.com/svg.image?x_2) then ![](https://latex.codecogs.com/svg.image?x_4) decreases to

   so ![](https://latex.codecogs.com/svg.image?x_4) is the non-basic
4. (0,5) is our current vertex:

   ![](https://latex.codecogs.com/svg.image?x_3%20=%203%20-%20x_1%20=%203)

   ![](https://latex.codecogs.com/svg.image?x_4%20=%205%20-%20x_1%20-%20x_2%20=%205%20-%200%20-%205%20=%200)

   ![](https://latex.codecogs.com/svg.image?z%20=%2010)
5. Choose a neighbor:

   whatever vertex we choose from the neighbors, our f decreases, so that means the algorithm stops and (0,5) is our solution
   ![alt text](https://github.com/elghemary/farah/assets/uploads/(0.5).png?raw=true)


Pretty simple isn't it ? but you might think okay that's great but I'm still confused on how this is related to the tedious calculations of the method ?

First of all let's clear something about the difference between The tableau method and the algebraic form of the algorithm, well surprisingly It is the same thing, same algorithm and same calculations, even if it seems like two totally different methods. The Tableau method is in fact just a condensed form of the algebraic method.

In the rest of this article I'll cover the algebraic method, as it's more important and carry out the mathematical interpretation of the calculations. this part a solid understanding of linear algebra and especially the geometrical intuition behind it's concept. I highly recommend "The Essence of Algebra" playlist of the famous you-tuber 3b1b.

**The algebraic simplex method**

Our LP consists of two parts

1. the objective function
2. our constraints that makes a linear system

We can think of this linear system geometrically as a matrix A transforming a vector x to a vector b,

each columns of the matrix A tells us where the vectors of the basis lands in the output

A is a non square, 2x4 matrix which means A is a transformation from a higher dimension to a lower one.

We know that the output is some linear combination of the columns of the matrix,

along with with x1, x2 >0 , sum .. it is a convex combination

So we are asked to find the convex combination of the columns of A that equals to b ( which geometrically is a convex set ) and satisfy our objective function !

Let's back to our linear system in matrix form, to solve it A should be invertible e.g detA != 0 then x = A^-1.b

If you pay enough attention you'll observe that this is impossible, A is a non suquare matrix, and the det is defined for square matrices only. Geometrically this intuition is impossible, as we said before A is transformation of 4D space to 2D space, the invertible transformation ...

the mathematical procedure is to calculate nCn base ..

The way I like to think about this is since the invertible transformation to a higher dimension is impossible, and the output vector is 2D, we'll look for a matrix that transform a 2d vector to our b vector by dividing our matrix A to a smaller square matrix supposed to be the new basis,

we'll end up with 6 matrices

At the end of this process we end up with a number of vectors less or equal to nCn

Let's back to our initial goal : optimize our objective function, so this results are all solutions to our LP, but we are looking for the optimum one, for this reason e introduce the reduced coast function, which calculate the possible amount that the objective function can be improved, then it is logical that whenever this function is negative that means that there is no way to improve this function, we find the basic optimal solution

now do u remember the Wikipedia definition of a simplex that I mentioned before, the simplex method consists to fix a basis vectors, that are a convex combination and makes a convex polygon,

looking if the solution is a vertex of the vertex

if not we change one vector of the basis without affecting the other edges of the polygon

**Python Code**

Here is a python code that solve an LP problem using the simplex method
