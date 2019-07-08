# Checkout Performance Lab Exercises:

In real life, customers do not choose a random cashier when they check out. They typically base their choice on at least the following two factors:

a. The length of a line of customers waiting to check out.

b. The physical proximity of a cashier.

Modify the simulation of the previous project exercise so that it takes account of the first factor.

Modify the simulation of the previous project so that it takes account of both factors listed in that project. You should assume that a customer initially arrives at the checkout line of a random cashier and then chooses a cashier who is no more than two lines away from this spot. This simulation should have at least four cashiers.

The simulator’s interface asks the user to enter the average number of minutes required to process a customer. However, as written, the simulation assigns the same processing time to each customer. In real life, processing times vary around the average. Modify the Customer class’s constructor so that it randomly generates service times between 1 and (average * 2 + 1).
