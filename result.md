Result:

# 1. Problem Definition:

## States: 
Any valid placement of die on puzzle board is a state, die can have any orientation and location on puzzle where there is no obstacles but it can never have 6 as face-up value.
So given a puzzle of m rows and n columns with k obstacles there are total (m*n) – k valid locations where a die can be placed. Further a die can have all four orientation but since 6 can never be face-up value of die, we can have total (6-1)*4 i.e. 20 orientation per location.
Hence the total state space will be  20*((m*n)-k).

## Initial State:
In Initial state our die is laying on location marked with S in the puzzle with initial configuration that it has 2 on north, 3 on east, 5 on south and 4 on west.

## Actions:
Given die can be roll to any of the direction i.e. east, west, north and south given that rolling to that direction would not make the die fall outside the puzzle board, the resultant location does not have any obstacle and after performing the roll 6 is not facing up.

## Transition Model:
Whenever we can perform a valid roll as defined in action we make a transition from one state to another where the new orientation and location of die is current state.

##Goal Test:
The Die is on a location G on puzzle and 1 is facing up on die.

Path Cost:
Estimated Total Cost to destination through current position n is given by
f(n)= g(n)+h(n)	
where
g(n)-  path cost to position n from initial state
h(n)-  estimated cost to goal state from position n

Each valid move has the same cost so we can assume the path cost as constant.


2. Heuristics:

We have used three heuristics to estimate the cost to the destination.

1: Manhattan Distance: 
Manhattan or block distance between two position on the puzzle is given by 

cur(xc,yc): row and column  of current state
goal(xg,yg): row and column  of goal state

h(n)=|xc-xg |  + |yc-yg|

This heuristic is admissible:
	
Manhattan distance will never overestimate the cost to destination
h(n)<=Actual cost to goal from state n 
