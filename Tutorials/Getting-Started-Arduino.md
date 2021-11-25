# Getting Started - Arduino

### Introduction
This tutorial is intended for everyone that is interested in using edge-ml with Arduino for the first time.

In this tutorial we will show you:
- [How to install the Arduino IDE?](#Install-Arduino-IDE)
- [How to add the required support files for your Nicla Sense ME or Arduino Nano 33 BLE Sense to the Arduino IDE?](#Add-Board-Support-Files)
- [How to flash the edge-ml firmware on your Nicla Sense ME or Arduino Nano 33 BLE Sense?](#Flash-edge-ml-Firmware)
- [How to collect data with edge-ml and your Arduino board?](#Collect-data)
- [How to label data with edge-ml and your Arduino board?](#Label-Data)
- [How to train a classifier from edge-ml data in a Jupyter Notebook?](#Train-Classifier)

### Install Arduino IDE
To install the Arduino Desktop IDE follow the specific instructions for your platform here:
- [Windows](https://www.arduino.cc/en/Guide/Windows)
- [MacOS](https://www.arduino.cc/en/Guide/macOS)
- [Linux](https://www.arduino.cc/en/Guide/Linux)

### Add Board Support Files
To add the required support files for your Arduino follow the steps here:
- [Arduino Nicla Sense ME](https://docs.arduino.cc/software/ide-v1/tutorials/getting-started/cores/arduino-mbed_nicla)
- [Arduino Nano 33 BLE Sense](https://docs.arduino.cc/software/ide-v1/tutorials/getting-started/cores/arduino-mbed_nano)

### Flash edge-ml Firmware
Install edge-ml in your Arduino IDE and flash it onto your Arduino following the steps [here](https://github.com/edge-ml/EdgeML-Arduino#how-to-install).

### Collect Data
_Please note_: Before you can use edge-ml you have to enable WebBLE in your Browser. Currently, WebBLE is **only available** on Chrome (head to `chrome://flags/#enable-experimental-web-platform-features` in your browser bar and set the Experimental Web Platform Features enabled) and Microsoft Edge. 
Also, make sure that your computer supports Bluetooth Low Energy.
Otherwise, connecting to your Arduino board will not be possible. 

To collect data, head over to [edge-ml.org](https://app.edge-ml.org) and register an account. Then create a new project in the left navigation bar by clicking "+ Add Project". Give your project a name and save it. Open the project and select "Datasets". Now you can connect to your Arduino by clicking "Connect to Bluetooth Device".

<img src="https://user-images.githubusercontent.com/11386075/143427884-2b283110-4342-438d-8e6c-59256ced91a0.png" alt="alt text" width="700">

Click on "Connect device". This will scan for available devices. Once your device has been found, connect to it.

<img src="https://user-images.githubusercontent.com/11386075/143428977-3adc1ba8-773f-4b60-86c2-99f3a49762a8.png" alt="alt text" width="700">


Now that you are connected, you can select the desired sensors, give your dataset a name and hit "Start recording" to collect data. When you are finished collecting data you can click "Stop recording".

<img src="https://user-images.githubusercontent.com/11386075/143428686-bbba3d3e-54ee-4da0-b308-3bf70fd598b9.png" alt="alt text" width="700">

You can view the recorded dataset by heading back to datasets and clicking "View".

<img src="https://user-images.githubusercontent.com/11386075/143429468-a18d32ec-0757-4f55-a487-f677c5e1c364.png" alt="alt text" width="700">




### Label Data
Now that you have collected your training data, you have to add labels to it so that they can be processed in the model training generation step later. Please navigate to "Labelings" in the navigation bar in your project. Then, lick "+ Add Labeling Set" to add a new set of labels 

<img src="https://user-images.githubusercontent.com/11386075/143431041-0a83ec45-0724-4888-b89a-38c41d20cd51.png" alt="alt text" width="700">


You can now enter the name of the labeling set. Then click on "+ Add Label" to add your desired labels.
The colors for the labels are generate automatically for you and you can easily change them by entering a different color HEX code.

<img src="https://user-images.githubusercontent.com/11386075/143431092-2291b034-6131-4e4b-8aa8-ec21409c9b4d.png" alt="alt text" width="400">

To add a label go back to your datasets and then view the dataset that you would like to label. Click the lock in the bottom left corner to enable the labeling feature. Then add the labels as you desire.


![ezgif-2-440acf966c1b](https://user-images.githubusercontent.com/11386075/143432545-f75fd209-71e5-42f0-9334-7bd870a4ece7.gif)





### Train Classifier
Now that you have collected some data and labeled different acitivities, please follow the steps in [this Google Colab Notebook](https://colab.research.google.com/drive/1JeKOSQvd5xayBETpWO-uPHtiKgKmGjUv?usp=sharing) to train a classifier.
You will have to perform small changes to adapt the notebook to your specific dataset (sensors used) and labels.
Please find the detailed instructions directly inside the notebook.

# Questions
If you have any questions please reach out to Tobias Roeddiger *[lastname]*@teco.edu

If you are experiencing problems with edge-ml please file a bug [here](https://github.com/edge-ml/edge-ml/issues).


