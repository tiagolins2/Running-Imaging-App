# Running-Imaging-App
Steps for Controlling Autonomous Tracking System

[1. Connecting to the Image Capturing Board](#1-connecting-to-the-image-capturing-board)

[2. Running Imaging Planner](#2-running-imaging-planner)

[3.	Schedule runs with crontab](#3-schedule-runs-with-crontab)

[4.	Run the image capturing calibration](#4-run-the-image-capturing-calibration)

# 1 Connecting to the Image Capturing Board

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

h)	Once you are done filling out your information, click on Save Plan. As an option, you can also test your plan now by pressing “Run Now” button (*see video below), allowing you to see the results in the app window.

https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/62d48762-8757-47f0-880b-7e52647a5fb5

i)	Once done, you can now close the app.
The next step is to schedule when your plates should be imaged.



# 3 Schedule runs with crontab

https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/2b2375e7-f732-4141-a80f-3a50a3766ef8

a)	In order to set the a pre-defined date to run the code automatically, we must run crontab code from the Raspberry Pi Terminal. Raspberry Pi Terminal can be opened using the icon on the task bar.

 ![tutorial_12](https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/ffb12c62-4d8b-4e80-976d-2fe056bbd285)


b)	On the terminal, write “crontab -l” and press enter to view any scheduled task for the Raspberry Pi. Note that any line starting with “#” is commented out, which means it is inactive. In the image below, all lines are commented out, hence, there is no active scheduled task for this RPi system.
 
<img width="600" alt="tutorial_13" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/97da4518-d725-48b4-9d03-8ad545745af6">

c)	In order to edit this crontab tasks, write “crontab -e” command on the Pi Terminal. Once you hit enter, you’ll see the crontab becomes editable. 
 
 <img width="600" alt="tutorial_14" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/9c8ae484-1fc2-4172-86ad-c1105c01e722">


d)	Delete the hashtag “#” in front of the final line of code so as to make it an active task. The active codes becomes white so once you delete the hashtag at the beginning of the line, the line will turn from blue to white. Once you made any change on the crontab, you should press Ctrl+X to save and exit. After pressing Ctrl+X, it’ll ask you to save it. Press Y to save. Then, it’ll ask you where to save the crontab. Do not change the directory or file name and press Enter.
  
  <img width="332" alt="tutorial_15" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/fb252343-410d-44ca-9dd0-4e9f9c107670">

  
e)	Note that this code is set to run at 16:00 every day once you delete the hashtag. You can set the time by changing 00 and 18 in the code. If you want more than one arbitrary operations, you can simply copy and paste this line of code, and enter another time. If you want to periodically run any command/code/script, there are other available codes you can find over the net (https://crontab.guru/). 
f)	Once you made your changes in crontab and save and exit using Ctrl+X, you will return to Pi Terminal. To double check your scheduled tasks, you can run crontab -l command to see your changed crontab.
 

![tutorial_16](https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/9435f056-ffc2-44dd-be38-973c775432a9)


# 4 Run the image capturing calibration



https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/50a5f119-324b-46e8-a272-439973160cda


a)	To ensure that there is proper alignment between the cameras and the stages, and to also reduce tilting in the images, you can run the calibration app. Open the file named “DuckPlate_imaging_calibrate.py”

 <img width="600" alt="tutorial_17" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/934964b6-7ee8-4f9d-90d7-d1925b55dfe8">


b)	Once open, click the green Run button

 <img width="600" alt="tutorial_18" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/3320e3bc-4ec0-47a1-9bc8-f43f19b3470b">

c)	This will open the small window app. First, press capture image to view how the cameras are capturing the stage above it.

 <img width="250" alt="tutorial_19" src="https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/dc3fab4a-aa4e-42d0-8f52-903a83c44c13">


d)	After about 30 seconds, the window will be automatically updated with the photos that have been just taken, as shown below.
 

![tutorial_20](https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/507d6a74-00b2-43a5-8ae5-f75b1d9ee9b7)







