# DesktopActivity Eye Tracking Dataset

This repository contains the introduction to the ***DesktopActivity Eye Tracking dataset*** collected for the **ACM SenSys 2020** paper: *"GazeGraph: Graph-based Few-Shot Cognitive Context Sensingfrom Human Visual Behavior"* by [Guohao Lan](https://guohao.netlify.app/), [Bailey Heit](https://www.linkedin.com/in/bailey-heit-b35a23152/), [Tim Scargill](https://sites.duke.edu/timscargill/), and [Maria Gorlatova](https://maria.gorlatova.com/). 

For questions on this repository or the related paper, please contact **Guohao Lan** via *guohao [DOT] lan [AT] duke [DOT] edu*

## **Outline**:

* [Dataset Information](#1)
* [Dataset Download](#2)
* [Citation](#3)
* [Acknowledgments](#4)

## 1. <span id="1">Dataset Information</span>

### 1.1 Data collection setup
The dataset is collected from **eight** subjects (*four female and four male, aged between 24 and 35; all subjects are fluent in English, with Spanish (1), English (2), and Chinese (5) as their first language*) using the [Pupil Core](https://pupil-labs.com/products/core/) eye tracker. During data collection, the subjects wear the eye tracker and sit in front of the computer screen (a 34-inch display) at a distance of approximately 50cm. We conduct the manufacturer's default on-screen five-points calibration for each of the subjects. Note that we have done only one calibration per subject, and the subjects can move their heads and upper bodies freely during the experiment. 

#### Example of data collection setup: 
<p align="center">
     <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/pupilDevice.png" width = "700" height = "200" hspace="0"/>
</p>
<p align="center">
Figure 1: (a) Close-up of the Pupil Core head-mounted eye tracker used in the data collection; (b) example of a subject wearing the eye tracking; (c) field of view of the subject, captured by the front scene camera, with the detected gaze point overlaid.
</p>

### 1.2 Activities
We focus on application of **sedentary activity recognition** using eye trackers. Tracking sedentary activities has several benefits. First, sedentary activities, such as reading and watching videos, occupy a dominant amount of time in people's daily lives. A recent report indicates that 25\% of Americans are sedentary for more than eight hours a day. Unfortunately, a sedentary lifestyle is associated with poor health, including an increased risk of heart disease and type 2 diabetes. Thus, proactively monitoring the daily sedentary activities can provide more fine-grained information about people's lifestyles. Second, it enhances the context-awareness of existing systems. For instance, by detecting whether a user is playing video games or reading articles, the environment (e.g., smart home) or mobile AR/VR systems can be augmented to provide better user experience and more immersive user-environment interaction. 

We consider six different **desktop activities** that are commonly performed in daily life:

- **Browse**: subjects browse public news websites or blogs. The websites visited by the subjects are different: three subjects gravitated toward visiting websites written in English while the other five subjects visited websites written mainly in Chinese. 

- **Play**: subjects are asked to play simple online games. We consider two different games: one requiring the subjects to look ahead horizontally ([Classic Super Mario](https://www.classicgames.me/super-mario-bros.html)), while the other requiring the subjects to look in all directions to navigate the game character ([Agario](https://agar.io/#ffa)). The instructions of the games are given to the subjects before playing. 

- **Read**: subjects read digital content displayed on a computer screen. Three reading materials in English are prepared: a Wikipedia article, a research paper in a two-column format, a textbook in a single-column format. These materials differ in both text layout and the number of figures embedded. 

- **Search**: we ask subjects to search for answers to a list of predefined questions using a web-based search engine (i.e., Google). For each of the subjects, the questions are randomly ordered to ensure variations (and thus, different visual stimuli). The search history is cleared before every session so that all subjects start from the same baseline. 

- **Watch**: subjects watch a short video played on the screen. We consider two videos with a different number of main characters (one with two main characters and the other with more than three characters); also one video has subtitles shown on the bottom.

- **Write**: subjects are asked to write an essay in English using the Microsoft Word installed on the computer.

The subjects are asked to perform each of the six activities for five minutes. They can choose one of the stimuli prepared for the Read, Watch, and Play. The gazes is recorded at a 30Hz sampling rate. 

#### Example of data collection process:
The videos below show how the data collection process was performed. The videos were recorded by the scene camera of the eye tracker when a subject was performing the six activities. Each of the six videos corresponds to one of the six activities. In each of the videos, the estimated gazes (i.e., the green circle) and the images of the pupils are overlaid with the user's field-of-view in real-time. 

<p align="center">
     <table>
          <tr>
               <td> <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/browse.gif" alt="Drawing" style="width: 250px;"/> 
                    <p align="center">(a) Browsing the Internet</p>
               </td>
               <td> <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/play.gif" alt="Drawing" style="width: 250px;"/> 
                    <p align="center">(b) Playing video games</p>
               </td>
          </tr>
          <tr>
               <td> <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/read.gif" alt="Drawing" style="width: 250px;"/> 
                    <p align="center">(c) Reading articles</p>
               </td>
               <td> <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/search.gif" alt="Drawing" style="width: 250px;"/> 
                    <p align="center">(d) Searching the Internet</p>
               </td>
          </tr>
          <tr>
               <td> <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/watch.gif" alt="Drawing" style="width: 250px;"/> 
                    <p align="center">(e) Watching videos</p>
               </td>
               <td> <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/write.gif" alt="Drawing" style="width: 250px;"/> 
                    <p align="center">(f) Writing essays</p>
               </td>
          </tr>
     </table>
</p>

#### Example of the collected gazes: 
<p align="center">
     <img src="https://github.com/GazeGraphResource/GazeGraph/blob/master/rawGazeGraphExample.png" width = "500" height = "350" hspace="70"/>
</p>
<p align="center">
Figure 2: Example of the gazes when a subject is performing different sedentary activities: (a) Browsing the Internet; (b) Playing video games; (c) Reading articles; (d) Searching the Internet; (e) Watching videos; and (f) Writing essays.
</p>


## 2. <span id="2">Download Dataset</span>

The preprocessed dataset can be download [**here**](https://github.com/GazeGraphResource/GazeGraph/blob/master/DesktopActivity.zip). Please find details about the signal preprocessing pipeline in Section 5 of the paper.

#### The structure of the dataset

The dataset follows a hierarchical file structure shown below:
```
DesktopActivity
└───P1
│   │
│   └───P1_BROWSE.csv
│   └───P1_PLAY.csv
│   └───P1_READ.csv
│   └───P1_SEARCH.csv
│   └───P1_WATCH.csv
│   └───P1_WRITE.csv
│   
└───P2
│   │
│   └───P2_BROWSE.csv
│   └───P2_PLAY.csv
│   └───P2_READ.csv
|   ...
...
└───P8
```
There are **eight** sub-folders in the second level, correspond to the eight subjects. In each of the second level folders, there are **six** CSV files, correspond to the six desktop activities. Lastly, each of the CSV files contains the gaze samples (a **9000 x 2** time series) collected from the subject when she/he is performing the activity. The **9000** corresponds to a **5 minutes (300 seconds)** gaze data sampled at **30Hz**, the **2** columns correspond to the **normalized X and Y coordinates of the gaze points**.

## 3. <span id="3">Citation</span>

Please cite the following paper in your publications if the dataset helps your research.

     @inproceedings{Lan20GazeGraph,
      title={{GazeGraph}: Graph-based few-shot cognitive context sensing from human visual behavior},
      author={Lan, Guohao and Heit, Bailey and Scargill, Tim and Gorlatova, Maria},
      booktitle={Proceedings of the 18th ACM Conference on Embedded Networked Sensor Systems (SenSys)},
      year={2020}
    }


## 4. <span id="4">Acknowledgments</span>
We would like to appreciate the help of the eight participants in the data collection. This study was done in the [Intelligent Interactive Internet of Things Lab](https://maria.gorlatova.com/) at [Duke University](https://www.duke.edu/), and was approved by our institution's Institutional Review Board.  

The authors of this dataset are [Guohao Lan](https://guohao.netlify.com/) and [Maria Gorlatova](https://maria.gorlatova.com/). Contact Information of the contributors: 
* guohao.lan AT duke.edu
* maria.gorlatova AT duke.edu

This work is supported by the Lord Foundation of North Carolina and by NSF awards CSR-1903136 and CNS-1908051.

