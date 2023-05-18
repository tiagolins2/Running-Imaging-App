# Running-Imaging-App
Steps for Controlling Autonomous Tracking System

[1. Connecting to the Image Capturing Board](#1-connecting-to-the-image-capturing-board)

[2. Running Imaging Planner](#2-running-imaging-planner)

[3.	Schedule runs with crontab](#3-schedule-runs-with-crontab)

[4.	Run the image capturing calibration](#4-run-the-image-capturing-calibration)

[5. Storing files into Symbiont Server](#5-storing-files-into-symbiont-server)


  
# 1 Connecting to the Image Capturing Board

a)	Download and Install UtorVPN, Cisco (if you do not have it already installed in your computer)
Here is the link for UtorVPN. Depending on your device, select the proper operating system, install The Cisco AnyConnect Client with the proper settings.
https://onesearch.library.utoronto.ca/ic-faq-categories/utorvpn

b)	Open VPN and connect via your UTORid and password.
An example run on Windows:
 <img width="600" alt="tutorial_1" src="images_app/tutorial_1.png">


c)	Windows->Remote Desktop Connection
In order to connect the Raspberry Pi of the imaging system, you need to run the Remote Desktop Connection.
Press windows button and write “remote” in the search bar.

 <img width="600" alt="tutorial_2" src="images_app/tutorial_2.png">


Enter the IP address of the RPi, and click connect.
IP: ---------------

<img width="350" alt="tutorial_3-2" src="images_app/tutorial_3-2.png">



d)	Login Raspberry Pi using the User ID and password

a.	User: -----
b.	Password: --------
 


<img width="450" alt="tutorial_4-2" src="images_app/tutorial_4-2.png">





# 2 Running Imaging Planner



https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/afac327b-5777-40b3-84b5-72d762619946



![running app](images_app/videos-app/running imaging app - how to do calibration.mp4)

a)	First, open DuckPlate_imaging.py

 <img width="200" alt="tutorial_5" src="images_app/tutorial_5.png">

b)	This will open the code. Click the run button 
  
<img width="600" alt="tutorial_6" src="images_app/tutorial_6.png">

c)	The following window will show up. Define each field using the dropdown options:
Number of photos: How many repeat photos of the same area you want
Number of rows: How many rows on the stage to be covered (Please check to make sure the way for the linear stage to move is clear!)
Mode: Photo or video. For now I have only enabled photo to work
Press Okay once done 

 <img width="300" alt="tutorial_7" src="images_app/tutorial_7.png">


d)	Once you press Okay, a new window will appear. Before you name them, first define a start time and end time for the image capturing.
 
Click on *Update start time*

 <img width="404" alt="tutorial_8" src="images_app/tutorial_8.png">

e)	Next, click on Update end time

 <img width="600" alt="tutorial_9" src="images_app/tutorial_9.png">

f)	You will be asked to enter how many days you want to run your experiment for (i.e. 5 days)

<img width="600" alt="tutorial_10" src="images_app/tutorial_10.png">

 
g)	You can then name each area/pair of plates, and change the dates according to your experiment design. Here I named them as numbers going from 1 to 20.

 <img width="600" alt="tutorial_11" src="images_app/tutorial_11.png">

h)	Once you are done filling out your information, click on Save Plan. As an option, you can also test your plan now by pressing “Run Now” button (*see video below*) allowing you to see the results in the app window, or running the saved plan to view the output in the board.

https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/62d48762-8757-47f0-880b-7e52647a5fb5

https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/6f33d427-7271-4777-80e9-22f9b66dcb37

i)	Once done, you can now close the app.
The next step is to schedule when your plates should be imaged.




# 3 Schedule runs with crontab

https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/2b2375e7-f732-4141-a80f-3a50a3766ef8

a)	In order to set the a pre-defined date to run the code automatically, we must run crontab code from the Raspberry Pi Terminal. Raspberry Pi Terminal can be opened using the icon on the task bar.

 <img width="600" alt="tutorial_12" src="images_app/tutorial_12.png">


b)	On the terminal, write “crontab -l” and press enter to view any scheduled task for the Raspberry Pi. Note that any line starting with “#” is commented out, which means it is inactive. In the image below, all lines are commented out, hence, there is no active scheduled task for this RPi system.
 
<img width="600" alt="tutorial_13" src="images_app/tutorial_13.png">

c)	In order to edit this crontab tasks, write “crontab -e” command on the Pi Terminal. Once you hit enter, you’ll see the crontab becomes editable. 
 
<img width="600" alt="tutorial_14" src="images_app/tutorial_14.png">


d)	Delete the hashtag “#” in front of the final line of code so as to make it an active task. The active codes becomes white so once you delete the hashtag at the beginning of the line, the line will turn from blue to white. Once you made any change on the crontab, you should press Ctrl+X to save and exit. After pressing Ctrl+X, it’ll ask you to save it. Press Y to save. Then, it’ll ask you where to save the crontab. Do not change the directory or file name and press Enter.
  
  <img width="340" alt="tutorial_15" src="images_app/tutorial_15.png">

  
e)	Note that this code is set to run at 16:00 every day once you delete the hashtag. You can set the time by changing 00 and 18 in the code. If you want more than one arbitrary operations, you can simply copy and paste this line of code, and enter another time. If you want to periodically run any command/code/script, there are other available codes you can find over the net (https://crontab.guru/). 
f)	Once you made your changes in crontab and save and exit using Ctrl+X, you will return to Pi Terminal. To double check your scheduled tasks, you can run crontab -l command to see your changed crontab.
 

<img width="600" alt="tutorial_16" src="images_app/tutorial_16.png">







# 4 Run the image capturing calibration

https://github.com/tiagolins2/Running-Imaging-App/assets/95873122/50a5f119-324b-46e8-a272-439973160cda


a)	To ensure that there is proper alignment between the cameras and the stages, and to also reduce tilting in the images, you can run the calibration app. Open the file named “DuckPlate_imaging_calibrate.py”

 <img width="600" alt="tutorial_17" src="images_app/tutorial_17.png">


b)	Once open, click the green Run button

 <img width="600" alt="tutorial_18" src="images_app/tutorial_18.png">

c)	This will open the small window app. First, press capture image to view how the cameras are capturing the stage above it.

 <img width="250" alt="tutorial_19" src="images_app/tutorial_19.png">


d)	After about 30 seconds, the window will be automatically updated with the photos that have been just taken, as shown below.
 

 <img width="550" alt="tutorial_20" src="images_app/tutorial_20.png">




# 5 Storing files into Symbiont Server

You can also store files saved in the board into the server under your account.  
To do this, you can open the command prompt in the raspberry Pi, and write "expect autom2.exp" (see below) 

 <img width="600" alt="tutorial_21" src="images_app/tutorial_21.png"> 

It will ask you for your user name in Symbiont, a folder name where you want to store all the files (i.e. "test1"), and your password (which won't show up as you type). This will then create the folder in your account and save all the images (from cameras A to D) into the folder.




