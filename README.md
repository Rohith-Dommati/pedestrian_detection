# pedestrian_detection
This is a machine learning in edge applications project where we detect pedestrians in day and night times.
# IILUSTRATION OF THE PROJECT

<a href="https://github.com/Rohith-Dommati/pedestrian_detection/assets/101145734/46e992be-8bd8-47d5-b3fa-09de3754c667"><a/>

 Here is an example of the working model of the project where it detects the pedistrians as person with respect to its probabilities.
 We can also perform this using night vision camera under no light conditions


# Getting started (In Windows)

## Required Dependencies

* Edge Impulse CLI
* Arduino CLI (for any arduino devices)

### TO install the required dependencies check these links below

[Installing Edge Impulse CLI](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-installation#installation-windows)

[Installing Arduino CLI](https://arduino.github.io/arduino-cli/0.32/installation/#latest-release)


# connecting Nicla Vision to Edge Impulse (Windows)

1.Download the [latest edge impulse firmware](https://cdn.edgeimpulse.com/firmware/arduino-nicla-vision.zip) and extract the zip file.

2. Connect Arduino Nicla Vision to your PC with a micro-USB cable and press the reset button twice to enter the bootloader indicated by flashing green LED on Nicla Vision.

3. Open the file named `flash_windows.bat` from the unziped files, and let the flash script run, once it is finished blue LED should turn on in your Arduino Nicla Vision.

4. Then run this command on a new cmd prompt `edge-impulse-daemon` and log in to your edge impulse account. Then select the project you want Arduino Nicla Vision to connect. `edge-impulse-daemon --clean` can be run if you want to re-login to edge impulse or select a different project to connect your Nicla Vision.

5. Open your edge impulse project in your browser, you should be able to see Arduino Nicla vision in your Devices tab.

![image](https://github.com/Rohith-Dommati/pedestrian_detection/assets/101145734/271e1a7d-58ff-434c-a8b1-2f5085ffe97d)


# Collecting Data

For gathering data, which comprises of labeled images, one can either upload images onto Edge Impulse directly or collect data from Arduino Nicla Vision. Here, the steps for collecting data from Nicla Vision will be outlined, as uploading data is a straighforward process.

1. Go to the Data acquisition tab, select Nicla Vision from the 'Device dropdown menu' and camera from the 'Sensor dropdown menu'. Once you select the camera you should see a live feed of the camera.

2. Type the class name in the Label box, and get the object in the frame of the camera. Click on 'Start sampling' to capture an image, it will automatically be uploaded to your project with the label you mentioned before.

Video Demonstration of collecting data: [Data Collection in Edge Impulse](https://www.youtube.com/embed/dY3OSiJyne0?start=240)

# Building Machine Learning Model
This section will detail the steps involved in designing the machine learning architecture which will be utilized for training on the collected data. One may either construct and train their own custom model or opt to use pre-trained models provided by Edge Impulse, which can be utilized for transfer learning and fitting our dataset. The subsequent steps are tailored towards transfer learning.

1. Go to the 'Create impulse' tab under 'Impulse design' and select input image width and height in the 'Image data' block.

   ![image](https://github.com/Rohith-Dommati/pedestrian_detection/assets/101145734/55986220-c22a-4c84-92d4-55e77eba6772)


2. Add an image block by clicking on the 'Add a processing block' and selecting Image.

3. Then add a Object detection(Images) by clicking on the 'Add a learning block' and selecting Object detection(Images). Then click on 'Save Impulse'

   ![image](https://github.com/Rohith-Dommati/pedestrian_detection/assets/101145734/1f659f39-63c1-400d-9708-42fbc93f5923)


4. Next, go the 'Image' tab under 'Impulse design', select the Color depth as RGB or Grayscalse and click on 'Save parameters' and then click 'Generate features'.
   
5. Finally, go to the 'Object detection' tab under 'Impulse design' and select appropriate parameters and click on 'Start training' to train our machine learning model.

   ![image](https://github.com/Rohith-Dommati/pedestrian_detection/assets/101145734/70c952c0-9c46-4f0d-9905-9ce81a88e6ad)

   
6. Wait for the model to complete the training and then move to the next section.
   
Video Demonstration of Building Model: [Build Model](https://www.youtube.com/embed/dY3OSiJyne0?start=529)

7. Go to Retrian model tab and train the model agin.

# Deploy the model
Deploying the trained weights to our device is a simple process in Edge Impulse, which can be done in just three easy steps. Once the model is trained and finalized, follow the steps below to deploy it to the device.

1. Go to the 'Deployment' tab and scroll down to the 'Build firmware' section.

2. Next, choose 'Arduino Nicla Vision' as the device and scroll down to click on the 'Build' button. Wait for the process to complete, and upon completion, your browser will automatically download a zipped file with required firmware for Nicla Vision.
3. Finally, enter the bootloader mode of the Arduino Nicla Vision by pressing the reset button twice. Afterward, unzip the downloaded file and open the `flash_windows.bat` file. Let it finish.

### Now you can run the live classification in the microcontroller

