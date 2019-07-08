# CASE STUDY: AN EMERGENCY ROOM SCHEDULER
As anyone who has been to a busy hospital emergency room knows, people must wait for service. Although everyone might appear to be waiting in the same place, they are actually in separate groups and scheduled according to the seriousness of their condition. This case study develops a program that performs this scheduling with a priority queue.

Request
Write a program that allows a supervisor to schedule treatments for patients coming into a hospital’s emergency room. Assume that, because some patients are in more critical condition than others, patients are not treated on a strictly first-come, first-served basis, but are assigned a priority when admitted. Patients with a high priority receive attention before those with a lower priority.

Analysis
Patients come into the emergency room in one of three conditions. In order of priority, the conditions are ranked as follows:

1. Critical

2. Serious

3. Fair

When the user selects the Schedule option, the program allows the user to enter a patient’s name and condition, and the patient is placed in line for treatment according to the severity of his condition. When the user selects the Treat Next Patient option, the program removes and displays the patient first in line with the most serious condition. When the user selects the Treat All Patients option, the program removes and displays all patients in order from patient to serve first to patient to serve last.

Each command button produces an appropriate message in the output area. This Table lists the interface’s responses to the commands.

![image](https://user-images.githubusercontent.com/19671036/60823986-68e7b180-a16e-11e9-97d9-a82d5fdb2a58.png)

Here is an interaction with the terminal-based interface:

![image](https://user-images.githubusercontent.com/19671036/60824044-874dad00-a16e-11e9-8f64-dc7a9ee87dc2.png)

Classes
The application consists of a view class, called ERView, and a set of model classes. The view class interacts with the user and runs methods with the model. The class ERModel maintains a priority queue of patients. The class Patient represents patients, and the class Condition represents the three possible conditions. The relationships among the classes are shown in the next Figure

![image](https://user-images.githubusercontent.com/19671036/60824111-a2b8b800-a16e-11e9-87ec-6c4e46fe1baf.png)

Design and Implementation
The Patient and Condition classes maintain a patient’s name and condition. You can compare (according to their conditions) and view them as strings. Here is the code for these two classes:

![image](https://user-images.githubusercontent.com/19671036/60824173-bebc5980-a16e-11e9-9ff1-b18918d06fcc.png)

The class ERView uses a typical menu-driven loop. You structure the code using several helper methods. Here is a complete listing:

![image](https://user-images.githubusercontent.com/19671036/60824226-d85da100-a16e-11e9-97ee-3b7f7ced417b.png)
![image](https://user-images.githubusercontent.com/19671036/60824277-ef9c8e80-a16e-11e9-8637-e48eb791f5fb.png)
![image](https://user-images.githubusercontent.com/19671036/60824335-0a6f0300-a16f-11e9-93ad-f57022329773.png)

The class ERModel uses a priority queue to schedule the patients. Its implementation is left as a programming project for you.

# STUDENT PERFORMANCE LAB
Complete the emergency room scheduler application as described in the case study.
