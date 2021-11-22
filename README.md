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
- **[Advanced](#Advanced)**
  - [Projects](#Projects)
    - [Settings]()
    - [Adding team members]()
    - [Enable Device API]()
  - [Datasets](#Datasets)
    - [Labelings and Labels](#Labelings-and-Labels)
    - [CSV Header Format](#CSV-Header-Format)
    - [Example Dataset](#Example-Dataset)
    - [CSV Upload / Download]()
    - [Arduino, Android, node.js Libraries]()
  - [Account](#Account)
    - [Settings]()
    - [2-Factor-Authentication]()
- **[How to contribute](#How-to-contribute)**
  - [Submit an issue](#Submit-an-issue-or-feature)
  - [Join the development](#Join-the-development)
    - [Prerequisites](#Prerequisites)
    - [Starting edge-ml](#Starting-edge-ml)
    - [Troubleshooting](#Troubleshooting)

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
- [How to install the edge-ml Firmware on your Nicla Sense ME?](https://github.com/edge-ml/nicla-sense-me-fw#nicla-sense-me-fw)
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
Training a model inside edge-ml is currently in closed beta. However, if you would like to train a model using the edge-ml device API in Python and sklearn you can follow the steps in the jupyter notebook [here](https://github.com/edge-ml/python/blob/main/notebook.ipynb). *Please Note:* You have to enable the device API in the settings of your project on edge-ml to retreive an API key for your project that you then use in the Python library.

### Deploy and use
_Coming soon._

## Advanced
### Projects
#### Settings
#### Adding team members
#### Enable Device API

### Datasets

#### Labelings and Labels
Datasets can be labelled to mark features e.g. for machine learning. We use following terminology:
* "labelings" are basically groups of "labels"; a dataset cannot be labelled with labelings directly, but with individual labels of a labeling
* multiple labelings (label groups), each containing multiple labels, can be created or imported
* labels of a labeling (aka the label group) must each have a unique name
* one specific label must not overlap in a dataset; this is prevented by edge-ml, but custom datasets need to comply
* different labels, even from the same labeling (label group), are allowed to overlap though


Importing and exporting datasets is possibles via CSV (comma separated values) files. 
The first record/line in the CSV file is the header containing a list of field names. 
Before reading on, [make yourself familiar what labelings/labels are in edge-ml](#Labelings-and-Labels) and how they are used.

#### CSV Header Format
We use the following (header )format, with which you have to comply with, if you want to import custom datasets:
* 'time', used for UNIX timestamps
* all sensors used, in the following format: "sensor\__sensorName_[_sensorUnit_], for each value that a specific sensor captured at a specific point in time; e.g. sensor_accX[m/s²] for acceleration in the x-direction.
* all labelings and labels used in the following format: label_labelingName_labelName; e.g. label_labeling1_label11, label_labeling1_label12,..., label_labeling2_label21, label_labeling2_label22


Some things to keep in mind:
* Labels of a labeling with the same name must not overlap. Edge-ml ensures this when creating/editing label(ing)s, but custom datasets must conform to this. Overlapping is forbidden, because it cannot be recreated when uploading and downloading the same dataset again.
* Different labels of a labeling are allowed to overlap though.
* To label a time stamp, simply add any string between the commas, expect the empty string. We simply use 'x' when downloading a dataset.

#### Example Dataset
Consider following scenario: We took sensor data of acceleration sensors in three dimensions on the 5th August 2021 on four points in time. The unit for acceleration is m/s². We have labeling1 with labels label1, label2 and labeling2 with labels label3, label4. 
The CSV file looks like this:

```
time,sensor_accX[m/s²],sensor_accY[m/s²],sensor_accZ[m/s²],label_labeling1_label1,label_labeling1_label2,label_labeling2_label3,label_labeling2_label4
1628168415000,2,2,2,x,,x,
1628168416000,4,2,4,x,,,
1628168417000,8,3,8,,x,,x
1628168418000,16,4,16,,x,,
```

#### CSV Upload / Download
##### Upload
Datasets can be uploaded as CSV files if they comply with our [CSV format](#CSV-Header-Format). Simply click on "+ Add Project" in the navbar on the left side, and the choose "Upload CSV Files"
##### Download
Datasets can be downloaded as CSV file. Select your project and dataset in the navbar on the left side, and click "View" to open a dataset. Then simply click "Download as CSV" in the "Management" section on the right. Everything you need to know about the CSV file is explained [here](#CSV-Header-Format).

#### Arduino, Android, node.js Libraries
Please follow the readmes of the repositories to learn how to use our Arduino, Android and node.js libraries:
- [Arduino](https://github.com/edge-ml/arduino/blob/master/README.md)
- [Android](https://github.com/edge-ml/android)
- [node.js](https://github.com/edge-ml/node)


### Account
#### Settings
#### 2-Factor-Authentication

## How to contribute
edge-ml is open-source and we love to see others contribute. Our dedicated team of researchers and developers constantly works on making edge-ml the best end-to-end embedded machine learning framework for everyone.

### Submit an issue or feature
Did you experience a bug? 🐛 Do you have a feature request? Please [join the discussion](https://github.com/edge-ml/edge-ml/discussions) and make yourself heard.

### Join the development
If you are interested in contributing a feature to our code base please have a look at our [Kanban board](https://github.com/orgs/edge-ml/projects/1) and make yourself noticed by joining planned features and issues. Also, feel free to create a pull request if you have found a bug and fixed it!

#### Prerequisites
* docker, nodejs (> v10) and npm must be installed. It is recommended to have nodemon installed as well.
* Windows does not support the nodejs debug options. You must run edge-ml on Windows Subsystem for Linux or WSL 2. WSL 2 however does not support React hot reload though, so you might be better off using a VM. 
* We discourage the use of Windows. It is supported, but it can be tricky to get everything to work, especially if you use the Windows Subsystem for Linux or WSL 2 alongside with Docker Desktop for Windows.

#### Installation
* do `git clone --recurse-submodules https://github.com/edge-ml/edge-ml.git`
* make sure docker (desktop) is running
* cd into the edge-ml folder and compose & start the mongo database with `docker-compose up -d mongo`
* cd into ./authentication and do npm install
* cd into ./backend and do npm install
* cd into ./frontend and do npm install

#### Starting edge-ml
(if you don't want automatic server refreshs when you modify the code, you can substitute "nodemon" with "node")

* make sure docker (desktop) is running, do `docker-compose up -d mongo` to start the database
* cd into ./authentication and do nodemon server.js 
* cd into ./backend and do nodemon server.js 
* cd into ./frontend and do npm start (or yarn start)

The order is important, the authentication part and the backend need to run before the frontend is started.
You should now get a message similar to this one: 

`Something is already running on port 3000. Probably:`
  `/path/to/nodejs server.js (pid 8753)`
  `in /path/to/edge-ml/backend`

`Would you like to run the app on another port instead? (Y/n)`

* type Y and hit enter. A browser window should open. If not, open one yourself with URL localhost:3001

Every time you run edge-ml, you need to go through these steps again. You can put these commands in a bash script for convenience.
 
Now you should be good to go. Any change in the source code will automatically refresh the server and frontend when nodemon is used.
If you use Visual Studio Code, debugging React code is easy, click [here](https://code.visualstudio.com/docs/nodejs/reactjs-tutorial#_debugging-react) for a guide.


#### Troubleshooting
* Windows does not support the nodejs debug options. You must run edge-ml on Windows Subsystem for Linux or WSL 2. If you get an error message similar to this one: `Error: Cannot find module 'C:\Workspace\edge-ml\authentication\$NODE_DEBUG_OPTION'` this is the reason.
* if you use Windows Subsystem for Linux or WSL 2 and cannot access localhost:3001, try http://127.0.0.1:3001 instead of localhost, or restart the Subsystem and try again.
