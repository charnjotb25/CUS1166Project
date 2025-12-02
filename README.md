# Vehicular Cloud Real Time System
### for CUS 1166-Software Engineering
##### By: Aditya V., Andrew O., Benjamin N., Charnjot B., Michael M., Shiva G. (Group 3) <br/> <br/>


### Milestone 1: Requirements Specification 
(taken from: https://docs.google.com/document/d/1neGHutoS9SDQq29_mAlbRED2GrWD_Al43ZQ2OgRHke8/edit?usp=sharing)
* Purpose - Vehicular Cloud Real-Time System (VCRTS) provides the basic services to manage/organize jobs and vehicles at a static vehicular cloud. In this system, Vehicles may arrive and depart with known and unknown schedules. Owners can rent out their vehicles to a Vehicular Cloud (VC) Manager. Clients can submit jobs in order to receive computation services.
* User Requirements:
  - Registration Service
  - Submission Service
  - Computation
  - Job Status
* Functional Requirements:
  - Registration Service 
  - Submission Service
  - Computation
  - Job Status
  - Role of VC Manager
  - Checkpoint Mechanism
  - Tracking the jobs
  - Confirmation Page
* Non-Funcional Requirements
  - Performance
  - Process Model
  - Language and Platform
  - Capacity
  - Data Integrity
  - Reliability <br/> <br/>

### Milestone 2: GUI 
* Created a GUI through a java window using JFrame, Labels and Button objects.
* Main class controls input and output
* Main Frame contains GUI methods and reads user-input of Vehicle Owner information/Client Job information to .txt files for storage and later use

### Milestone 3: Class design
UML Design: https://lucid.app/publicSegments/view/d98c9ae8-ba25-4c3c-83da-9cc8a983cc6e/image.pdf

![image](UML%20Diagram/VCRTS_UML_Diagram.png)

### Milestone 4: Class Implementation
* Added Classes in UML from Milestone 3:
  - Client
  - ClientList
  - Vehicle
  - VehicleOwner
  - VehicleOwnerList
  - Controller
  - VehicularCloud
  - Job
* Classes implemented to complete the following tasks:
  - Client can submit a job to VC and the information will be stored in a file. 
  - Vehicle Owner can register in the system and the information will be stored in a file.
  - VC Controller will be able to compute the completion time for each job.

### Milestone 5: Client/Server Model
* Created server within Controller class
* Added a Task Owner (Client) to authorize Jobs stored.
* Added Vehicler Owner (Client) to authorized Vehicles stored. 
* Messages can be sent between Clients and Servers to authorize or reject information

---
## 🚀 How to Deploy & Run the Project

This guide explains how to fork the project, set up the MySQL database, configure the code, and run both the server and client applications.

---
### 📌 1. Fork & Clone the Repository

1. Go to the GitHub repository page.
2. Click “Fork” to create your own copy.
3. Copy the URL of your forked repository.
4. Open Eclipse or any Git-compatible IDE.
5. Clone the repository into your workspace:
     - File → Import → Git → Clone URI
     - Paste the repository URL
     - Pull all project components

--- 
### 📌 2. Set Up the MySQL Database in MySQL Workbench
Create the Database Schema
  1. Open MySQL Workbench
  2. Click on Localhost
  3. Click Create a New Schema
  4. Name it: VC3
  5. Click Apply → Finish

You should now see the VC3 schema on the left sidebar.

---
#### Create Table 1: `client`
1. Right-click Tables → Create Table
2. Set Table Name: `client`
3. Add the following columns:
   | Column Name | Type        | NN |
   | ----------- | ----------- | -- |
   | name        | VARCHAR(45) | ✔  |
   | Id          | VARCHAR(45) | ✔  |
   | deadline    | VARCHAR(45) | ✔  |

4. Click Apply → Finish

To view rows:
Right-click the `client` table → Select Rows
(Current values will show as `NULL`)

This table stores task owner information.

--- 
#### Create Table 2: `vehicleowner`
1. Right-click Tables → Create Table
2. Set Table Name: `vehicleowner`
3. Add the following columns:
    | Column Name    | Type        | NN |
    | -------------- | ----------- | -- |
    | vehicleOwnerId | VARCHAR(45) | ✔  |
    | model          | VARCHAR(45) | ✔  |
    | licenseNumber  | VARCHAR(45) | ✔  |
    | residencyTime  | VARCHAR(45) | ✔  |

4. Click Apply → Finish

To view rows:
Right-click the `vehicleowner` table → Select Rows

This table stores vehicle owner information.

---
### 📌 3. Enter Your MySQL Password in the Code
After cloning the project:
1. Open Controller.java
2. Open NetworkClient.java
3. Enter your MySQL password in the empty string fields on:
     - Line 159 (Controller.java)
     - Line 187 (Controller.java)
These fields are required for the server to connect to MySQL.

Also review:
- Job Owner Information.txt
- Vehicle Owner Information.txt

These will be used to store client-side input temporarily.

---
### 📌 4. Running the System (Server & Client)
This application consists of:
  - Server side → Controller.java
  - Client side → NetworkClient.java

#### Step 1 — Start the Server
  1. Run Controller.java
  2. The console will display server logs
  3. It will wait for a client connection

#### Step 2 — Start the Client
  1. Run NetworkClient.java
  2. The console will show client options
  3. Type:
       - `yes` — to send data
       - `exit` — to disconnect

---
### 📌 5. Using the GUI Windows
When you type "yes" on the client side:
  1. Two GUI windows will appear
  2. Select the window titled:
       “Welcome to Vehicular Cloud Console”
  3. Choose one of the two main options:
       - owner → vehicle owner entering vehicle data
       - client → task owner submitting a job📌 5. Using the GUI Windows

Once you make a choice:
  1. A form window opens
  2. Fill in the fields
  3. Click Enter

A message dialog will confirm the data was sent to the server.

---
### 📌 6. Server-Side Approval Process

After the data is sent:
1. The server reads data from:
     - `Vehicle Owner Information.txt`
     - `Job Owner Information.txt`
2. A new window titled “Server” will appear
3. The server operator can choose:
     - Accept
     - Reject

If Accepted:
- Data is inserted into the appropriate MySQL table
- Client console displays a success message

If Rejected:
- Client console displays a rejection message
- Data is NOT added to the database

--- 
📌 7. Looping or Ending the Session
After receiving the server response, the client may:
- Type yes → submit another entry
- Type exit → close the connection

The server remains active and can continue accepting new connections or data.





