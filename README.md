# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

# 🛣️ Finding Lane Lines on the Road  
**Udacity Self-Driving Car Nanodegree – Project 1**  
_By Antoine Neidecker_

---

## 📌 Overview

This is my implementation of the **Finding Lane Lines** project from Udacity’s Self-Driving Car Nanodegree. In this project, I built a basic computer vision pipeline using **Python** and **OpenCV** to detect lane lines in road images.

The goal was to simulate a core function of a self-driving car: understanding lane boundaries using visual input, just as a human would.

---

## 🔧 What I Built

Using OpenCV, I created a step-by-step image processing pipeline that includes:

- Converting images to **grayscale**
- Applying **Gaussian blur** to reduce noise
- Using the **Canny edge detector** to find edges
- Defining and applying a **region of interest mask**
- Detecting straight lines using the **Hough Transform**
- Overlaying detected lane lines on the original image

The result is a working lane-detection system for still road images.

---

## 🖼️ Sample Output

You can find input and output examples in:

- `test_images/` – original test images  
- `test_images_output/` – processed images with lane lines drawn

Each output image shows the detected lines overlaid on the original image.

---

## 🧪 How to Run It

1. **Set up the Environment**  
   Install and activate the Udacity CarND Term1 Starter Kit:

   ```bash
   conda activate carnd-term1
