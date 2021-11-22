# edge-ml: embedded-first machine learning

Welcome to the _edge-ml_ wiki. Here you can find all the information you need to get started with your first project using _edge-ml_ today.

_edge-ml_ helps developers build models faster and more robustly with an open-source toolchain for embedded machine learning. With a few simple steps _edge-ml_ lets you record data, label samples, train models and deploy validated embedded machine learning directly on the edge. _edge-ml_ requires minimal initilization and supports upload in real-time as well as in bulk from the edge. Models are generated using AutoML therefore requiring minimal user configuration. The models are optimized for resource-constrained embedded chips based on hardware-aware neural network training.

If you are using _edge-ml_ and would like to cite it in your research please use:
```
@misc{edge-ml, 
  title={edge-ml.org - End-To-End Embedded Machine Learning}, 
  url={edge-ml.org}, 
  author={Tobias Röddiger and Tobias King and and Till Riedel and Michael Beigl}
}
```

## Overview
The docs give you a quick intro into edge-ml.
- **[Before you start](#Before-you-start)**
    - [How is edge-ml organized?](#How-is-edge-ml-organized)
    - [Register](#Register)
- **[Creating your first edge-ml model](#Creating-your-first-edge-ml-model)**
  - [Create project](#Create-project)
  - [Connect device](#Connect-device)
  - [Record datasets](#Record-datasets)
  - [Add Labels](#Add-Labels)
  - [Train edge-ml model](#Train-edge-ml-model)
  - [Deploy and use](#Deploy-and-use)
- **[How to contribute](#How-to-contribute)**
  - [Submit an issue](#Submit-an-issue-or-feature)
  - [Join the development](#Join-the-development)
- **[Advanced](#Advanced)**
  - [Projects](#Projects)
    - [Settings]()
    - [Adding team members]()
    - [Enable Device API]()
  - [Datasets]()
    - [CSV Upload / Download]()
    - [Arduino, Android, node.js Libraries]()
  - Account
    - [Settings]()
    - [2-Factor-Authentication]()

## Before you start
### How is edge-ml organized?
In general, edge-ml is organized on a per project. After creating a project, you can link a device to your project, upload datasets, define class labelings, and create as well as deploy edge machine learning models. If you are working together with others you can also add them to your project.

### Registration
Before you can use edge-ml, you have to register. Please do so [here](https://app.edge-ml.org)

## Creating your first edge-ml model
### Create project
After registering (see [Registration](#Registration)) login to your edge-ml account. Then create your first project by clicking on the "+ Add Project" button in the left main navigation bar. Here you can set a project name. Then click "Save" to create your first project. You have now create your first project with edge-ml.

### Connect device
Out of the box, edge-ml currently supports connecting to the following Arduinos:
- [Nicla Sense ME](https://www.bosch-sensortec.com/software-tools/tools/arduino-nicla-sense-me/) (directly from your browser over BLE)
- [Arduino Nano 33 BLE](https://store.arduino.cc/products/arduino-nano-33-ble) (directly from your browser over BLE)
- [ESP32](https://www.espressif.com/en/products/socs/esp32) (over WiFi using the dedicated edge-ml Arduino library)

edge-ml also supports [Android](https://github.com/edge-ml/java) and [node.js](https://github.com/edge-ml/node).

In this tutorial, we will focus on the **Nicla Sense ME** and **Arduino Nano 33 BLE** which already have sensors pre-installed and require minimal setup.

**Before you start please first install the edge-ml firmware on your Nicla Sense ME or Arduino Nano 33 BLE following the tutorials here:**
- [How to install the edge-ml Firmware on your Nicla Sense ME?](https://github.com/edge-ml/nicla-sense-me-fw)
- [How to install the edge-ml Firmware on your Arduino Nano 33 BLE?](https://github.com/edge-ml/nano-33-ble-fw)


Then, navigate to the project that you have created earlier on edge-ml. 
Within in your project navigate to the tab "Datasets" which will give you the possibility to connect to a new device using Bluetooth Low Energy by clicking the "+ Upload from BLE" button. Once your device is found, select it from the list of devices and click "Connect".
The device then shows up in your list of connected devices with the possibility to enable different sensors. 
You can now activate the sensors that you would like to record by selecting them from the list shown on your screen.
In this example, we will activate the accelerometer and gyroscope.

_Please note_: If edge-ml tells you that WebBLE is not available, follow the instructions to activate the experimental feature in your browser. Currently, WebBLE is **only available** on Chrome, Chrome Android, and Microsoft Edge. 
Also, make sure that your computer supports Bluetooth Low Energy.
Otherwise, connecting to the Nicla Sense ME will not be possible. 

### Record dataset
Now that you have connected to your device and configured the sensors according to your requirements, the next step is to record the first dataset.
To do so, click the "Record" button next to your connected device. You will start see data coming in which will be automatically pushed to the edge-ml cloud. Once you click "Stop", edge-ml will redirect you to the dataset you have just recorded. If you want to record another dataset, just go back to your device and click "Record" again.

In this example, we collect two datasets. The first dataset containes multiple repetitions of a 'Shake' gesture. The second dataset contains multiple repetitions of a 'Bump' gesture. We leave small breaks between the gesture repetitions to classify 'No Gesture' later.

### Add labels
Now that you have collected your training data, you have to add labels to it so that they can be processed in the model training generation step later. Please navigate to "Labelings" in the top navigation bar in your project. Then click "+ Add Labeling Set" to add a new set of labels. You can now enter the name of the labeling set (e.g., in our case "Gesture Labels"). Then click on "+ Add Label" to add your desired labels. In our example scenario we are adding the labels based on the data we recorded earlier by adding 'Shake', 'Bump', and 'No Gesture'. The colors for the labels are generate automatically for you and you can easily change them by entering a different color HEX code.

### Train edge-ml model
Training a model inside edge-ml is currently in closed beta. However, if you would like to train a model using the edge-ml device API in Python and sklearn you can follow the steps in the jupyter notebook [here](https://github.com/edge-ml/python)

### Deploy and use
_Coming soon._


## How to contribute
edge-ml is open-source and we love to see others contribute. Our dedicated team of researchers and developers constantly works on making edge-ml the best end-to-end embedded machine learning framework for everyone.

### Submit an issue or feature
Did you experience a bug? 🐛 Do you have a feature request? Please [join the discussion](https://github.com/edge-ml/edge-ml/discussions) and make yourself heard.

### Join the development
If you are interested in contributing a feature to our code base please have a look at our [Kanban board](https://github.com/orgs/edge-ml/projects/1) and make yourself noticed by joining planned features and issues. Also, feel free to create a pull request if you have found a bug and fixed it!

## Advanced
### Projects
#### Settings
#### Adding team members
#### Enable Device API

### Datasets
#### CSV Upload / Download
##### Upload
##### Download

#### Arduino, Android, node.js Libraries
Please follow the readmes of the repositories to learn how to use our Arduino, Android and node.js libraries:
- [Arduino](https://github.com/edge-ml/arduino/blob/master/README.md)
- [Android](https://github.com/edge-ml/android)
- [node.js](https://github.com/edge-ml/node)


### Account
#### Settings
#### 2-Factor-Authentication
