# Running-Imaging-App
Steps for Controlling Autonomous Tracking System

[1. Connecting to the Image Capturing Board](#1.-connecting-to-the-image-capturing-board)

[2. Running Imaging Planner](#2-running-imaging-planner)

**3.	Schedule experiment with crontab**

**4.	Run the image capturing calibration (optional)****


# 1. Connecting to the Image Capturing Board

a)	Download and Install UtorVPN, Cisco (if you do not have it already installed in your computer)
Here is the link for UtorVPN. Depending on your device, select the proper operating system, install The Cisco AnyConnect Client with the proper settings.
https://onesearch.library.utoronto.ca/ic-faq-categories/utorvpn

b)	Open VPN and connect via your UTORid and password.
An example run on Windows:
 <img width="600" alt="tutorial_1" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/83c48453-0061-484b-80c2-ea8df4c9ac1c">


c)	Windows->Remote Desktop Connection
In order to connect the Raspberry Pi of the imaging system, you need to run the Remote Desktop Connection.
Press windows button and write “remote” in the search bar.

 <img width="600" alt="tutorial_2" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/b60ee5e0-7236-495c-8e60-7bb408d6ba57">


Enter the IP address of the RPi, and click connect.
IP: 142.150.215.184

 <img width="600" alt="tutorial_3" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/5659bffd-ef47-4689-9089-02cc254de2fb">


d)	Login Raspberry Pi using the User ID and password
a.	User: pi
b.	Password: 190190
 
<img width="600" alt="tutorial_4" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/120bcf88-e3e6-4788-9310-0a2a46e852e8">


# 2 Running Imaging Planner

https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/4f2ed26d-fde3-4bf7-8e2d-387af65591ad

a)	First, open DuckPlate_imaging.py

 <img width="200" alt="tutorial_5" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/71af5177-86b0-4146-adad-f1d461fe1e96">

b)	This will open the code. Click the run button 
 
<img width="600" alt="tutorial_6" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/0e7ef8ab-8368-441d-87f6-26077a0e4b3c">

c)	The following window will show up. Define each field using the dropdown options:
Number of photos: How many repeat photos of the same area you want
Number of rows: How many rows on the stage to be covered (Please check to make sure the way for the linear stage to move is clear!)
Mode: Photo or video. For now I have only enabled photo to work
Press Okay once done 

 <img width="300" alt="tutorial_7" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/4a1763c8-f713-49cc-8989-27a8d6ce806a">


d)	Once you press Okay, a new window will appear. Before you name them, first define a start time and end time for the image capturing.
 
Click on *Update start time*

 <img width="404" alt="tutorial_8" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/59cfab83-1129-4dcf-83b6-6d1a3dc2aaf9">

e)	Next, click on Update end time

 <img width="600" alt="tutorial_9" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/84b4c14b-b4e7-4ab3-b021-9bd43a0260bd">

f)	You will be asked to enter how many days you want to run your experiment for (i.e. 5 days)

<img width="600" alt="tutorial_10" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/2b5a7434-11df-43fc-bdcf-128f6a36b684">

 
g)	You can then name each area/pair of plates, and change the dates according to your experiment design. Here I named them as numbers going from 1 to 20.

 <img width="600" alt="tutorial_11" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/20c3c93a-5fca-4cba-b218-5375021784ed">

h)	Once you are done filling out your information, click on Save Plan. As an option, you can also test your plan now by pressing “Run Now” button, allowing you to see the results in the app window.

i)	Once done, you can now close the app.
The next step is to schedule when your plates should be imaged.







