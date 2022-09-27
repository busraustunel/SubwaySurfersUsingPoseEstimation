# **<center><font style="color:rgb(100,109,254)">Playing Subway Surfers Game using Pose Detection</font> </center>**

<img src='https://drive.google.com/uc?export=download&id=1Msiu4noiq5NKViqXX8TE-6sei6ycS1Xx'>

<img src='https://drive.google.com/uc?export=download&id=1bREfnsfCWjVyMRjXM0kI0V33kRQ7f_dY'>

## **<font style="color:rgb(134,19,348)"> Outline </font>**

- **_`Step 1:`_ Perform Pose Detection**

- **_`Step 2:`_ Control Starting Mechanism**

- **_`Step 3:`_ Control Horizontal Movements**

- **_`Step 4:`_ Control Vertical Movements**

- **_`Step 5:`_ Control Keyboard and Mouse with PyautoGUI**

- **_`Step 6:`_ Build the Final Application**

## **<font style="color:rgb(134,19,348)">Step 1: Perform Pose Detection</font>**

To implement the game control mechanisms, we will need the current pose info of the person controlling the game, as our intention is to control the character with the movement of the person in the frame. We want the game's character to move left, right, jump and crouch with the identical movements of the person.

So we will create function **`detectPose()`** that will take an image as input and perform pose detection on the person in the image using the mediapipe's pose detection solution to get **thirty-three 3D landmarks** on the body and the function will display the results or return them depending upon the passed arguments.

<img src="https://drive.google.com/uc?export=download&id=1CDO0KiXZEOuWc7xLEm7EFLLQf2hydCoI">

This function is quite similar to the one we had created in the previous post. The only difference is that we are not plotting the pose landmarks in 3D and we are passing a few more optional arguments to the function **`mp.solutions.drawing_utils.draw_landmarks()`** to specify the drawing style.

You probably do not want to lose control of the game's character whenever some other person comes into the frame (and starts controlling the character), so that annoying scenario is already taken care of, as the solution we are using only detects the landmarks of the most prominent person in the image.

So you do not need to worry about losing control as long as you are the most prominent person in the frame as it will automatically ignore the people in the background.
