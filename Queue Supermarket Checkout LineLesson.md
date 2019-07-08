# CASE STUDY: SIMULATING A SUPERMARKET CHECKOUT LINE
In this case study, you develop a program to simulate supermarket checkout stations. To keep the program simple, some important factors found in a realistic supermarket situation have been omitted; you’re asked to add them back as part of the exercises.

## Request
Write a program that allows the user to predict the behavior of a supermarket checkout line under various conditions.

## Analysis
For the sake of simplicity, the following restrictions are imposed:

Image There is just one checkout line, staffed by one cashier.

Image Each customer has the same number of items to check out and requires the same processing time.

Image The probability that a new customer will arrive at the checkout does not vary over time.

The inputs to the simulation program are the following:

Image The total time, in abstract minutes, that the simulation is supposed to run.

Image The number of minutes required to serve an individual customer.

Image The probability that a new customer will arrive at the checkout line during the next minute. This probability should be a floating-point number greater than 0 and less than or equal to 1.

The program’s outputs are the total number of customers processed, the number of customers left in the line when the time runs out, and the average waiting time for a customer. Table 8.3 summarizes the inputs and outputs.

![image](https://user-images.githubusercontent.com/19671036/60821590-764e6d00-a169-11e9-81f2-bec57d30d374.png)

The User InterfaceThe following user interface for the system has been proposed:

```
Welcome the Market Simulator

Enter the total running time: 60
Enter the average time per customer: 3
Enter the probability of a new arrival: 0.25
TOTALS FOR THE CASHIER
Number of customers served: 16
Number of customers left in queue: 1
Average time customers spend
Waiting to be served: 2.38
```
# Classes and Responsibilities
As far as classes and their overall responsibilities are concerned, the system is divided into a main function and several model classes. The main function is responsible for interacting with the user, validating the three input values, and communicating with the model. The design and implementation of this function require no comment, and the function’s code is not presented. The classes in the model are listed in the following table:

![image](https://user-images.githubusercontent.com/19671036/60821694-ab5abf80-a169-11e9-8b20-69ad082d8d6b.png)

The relationships among these classes are shown in

![image](https://user-images.githubusercontent.com/19671036/60821748-c3324380-a169-11e9-9ae0-c6567faa23ed.png)

The overall design of the system is reflected in the collaboration diagram shown

![image](https://user-images.githubusercontent.com/19671036/60821795-da713100-a169-11e9-8890-832b61536858.png)

You can now design and implement each class in turn.

Because the checkout situation has been restricted, the design of the class MarketModel is fairly simple. The constructor does the following:

1. Saves the inputs—probability of new arrival, length of simulation, and average time per customer.

2. Creates the single cashier.

The only other method needed is runSimulation. This method runs the abstract clock that drives the checkout process. On each tick of the clock, the method does three things:

1. Asks the Customer class to generate a new customer, which it may or may not do, depending on the probability of a new arrival and the output of a random number generator.

2. If a new customer is generated, sends the new customer to the cashier.

3. Tells the cashier to provide a unit of service to the current customer.

When the simulation ends, the runSimulation method returns the cashier’s results to the view. Here is the pseudocode for the method:

![image](https://user-images.githubusercontent.com/19671036/60822072-61bea480-a16a-11e9-87d7-c40652812d54.png)

Note that the pseudocode algorithm asks the Customer class for an instance of itself. Because it is only probable that a customer will arrive at any given minute, occasionally a customer will not be generated. Rather than code the logic for making this choice at this level, you can bury it in a class method in the Customer class. From the model, the Customer class method generateCustomer receives the probability of a new customer arriving, the current time, and the average time needed per customer. The method uses this information to determine whether to create a customer and, if it does, how to initialize the customer. The method returns either the new Customer object or the value None. The syntax of running a class method is just like that of an instance method, except that the name to the left of the dot is the class’s name.

Here is a complete listing of the class MarketModel:

![image](https://user-images.githubusercontent.com/19671036/60822161-81ee6380-a16a-11e9-9c1a-e3916a1458d8.png)

A cashier is responsible for serving a queue of customers. During this process, the cashier tallies the customers served and the minutes they spend waiting in line. At the end of the simulation, the class’s __str__ method returns these totals as well as the number of customers remaining in the queue. The class has the following instance variables:

![image](https://user-images.githubusercontent.com/19671036/60822205-9af71480-a16a-11e9-81ee-2c9fdf14820d.png)

The last variable holds the customer currently being processed.

To allow the market model to send a new customer to a cashier, the class implements the method addCustomer. This method expects a customer as a parameter and adds the customer to the cashier’s queue.

The method serveCustomers handles the cashier’s activity during one clock tick. The method expects the current time as a parameter and responds in one of several different ways, as listed in

![image](https://user-images.githubusercontent.com/19671036/60822289-c8dc5900-a16a-11e9-8d48-4cde826a2154.png)

Here is pseudocode for the method serveCustomers:

![image](https://user-images.githubusercontent.com/19671036/60822331-df82b000-a16a-11e9-8d60-7912fffb9070.png)

Here is the code for the Cashier class:

![image](https://user-images.githubusercontent.com/19671036/60822431-0b9e3100-a16b-11e9-86cc-c45a0db22de3.png)
![image](https://user-images.githubusercontent.com/19671036/60822462-1c4ea700-a16b-11e9-9b12-dd51c09e2adc.png)

The Customer class maintains a customer’s arrival time and the amount of service needed. The constructor initializes these with data provided by the market model. The instance methods include the following:

Image arrivalTime()—Returns the time at which the customer arrived at a cashier’s queue.

Image amountOfServiceNeeded()—Returns the number of service units left.

Image serve()—Decrements the number of service units by one.

The remaining method, generateCustomer, is a class method. It expects as arguments the probability of a new customer arriving, the current time, and the number of service units per customer. The method returns a new instance of Customer with the given time and service units, provided the probability is greater than or equal to a random number between 0 and 1. Otherwise, the method returns None, indicating that no customer was generated. The syntax for defining a class method in Python is the following:

![image](https://user-images.githubusercontent.com/19671036/60822548-46a06480-a16b-11e9-85d2-9eb491e7c5cc.png)

Here is the code for the Customer class:

![image](https://user-images.githubusercontent.com/19671036/60822595-5ddf5200-a16b-11e9-9e65-0f74ea6e6774.png)




