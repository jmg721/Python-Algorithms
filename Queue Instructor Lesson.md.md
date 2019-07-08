# CASE STUDY: SIMULATING A SUPERMARKET CHECKOUT LINEIn this case study, you develop a program to simulate supermarket checkout stations. 

To keep the program simple, some important factors found in a realistic supermarket situation have been omitted; 
you’re asked to add them back as part of the exercises.
RequestWrite a program that allows the user to predict the behavior of a supermarket checkout line under various conditions.
Analysis
For the sake of simplicity, 
the following restrictions are imposed: There is just one checkout line, staffed by one cashier. 
Each customer has the same number of items to check out and requires the same processing time. 
The probability that a new customer will arrive at the checkout does not vary over time.
The inputs to the simulation program are the following: The total time, in abstract minutes, 
that the simulation is supposed to run. The number of minutes required to serve an individual customer. 
The probability that a new customer will arrive at the checkout line during the next minute. 
This probability should be a floating-point number greater than 0 and less than or equal to 1.
The program’s outputs are the total number of customers processed, the number of customers left in the line when the time runs out, 
and the average waiting time for a customer. 

This summarizes the inputs and outputs.
