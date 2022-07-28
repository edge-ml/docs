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
  - [Arduino](#Getting-started-with-edge-ml-and-Arduino)
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
We offer support for different platforms. Please follow the tutorials for your platform:
- [Getting started with edge-ml and Arduino](https://github.com/edge-ml/docs/blob/main/Tutorials/Getting-Started-Arduino.md)



## Advanced
### Projects
_Coming soon._
#### Settings
_Coming soon._
#### Adding team members
_Coming soon._
#### Enable Device API
_Coming soon._

### Datasets

#### Labelings and Labels
Datasets can be labeled e.g. for machine learning. We use following terminology:
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
* alternative without docker: install mongodb following the instructions [here](https://www.mongodb.com/docs/manual/administration/install-community/) or for WSL 2 [here](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database#install-mongodb)
* alternative without docker: create a directory for your database with `mkdir mongo`
* cd into ./authentication and do npm install
* cd into ./backend and do npm install
* cd into ./frontend and do npm install


#### Starting edge-ml
(if you don't want automatic server refreshs when you modify the code, you can substitute "nodemon" with "node")

* make sure docker (desktop) is running, do `docker-compose up -d mongo` to start the database
* alternative without docker: cd into ./mongo and do `sudo mongod --dbpath ./`
* cd into ./authentication and do `nodemon server.js`
* cd into ./backend and do `nodemon server.js` 
* cd into ./frontend and do `npm start` (or `yarn start`)

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
