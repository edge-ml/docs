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
To collect data, head over to [edge-ml.org](https://app.edge-ml.org) and register an account. Then create a new project in the left navigation bar.
Open the project and select "Datasets". Now you can connect to 

### Label Data

### Train Classifier
Now that you have collected some data and labeled different acitivities, please follow the steps in [this Google Colab Notebook](https://colab.research.google.com/drive/1JeKOSQvd5xayBETpWO-uPHtiKgKmGjUv?usp=sharing) to train a classifier.
You will have to perform small changes to adapt the notebook to your specific dataset (sensors used) and labels.
Please find the detailed instructions directly inside the notebook.

# Questions
If you have any questions please reach out to Tobias Roeddiger *[lastname]*@teco.edu

If you are experiencing problems with edge-ml please file a bug [here](https://github.com/edge-ml/edge-ml/issues).



