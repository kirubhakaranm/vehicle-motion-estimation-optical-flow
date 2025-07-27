# 🌊 Vehicle Segmentation and Motion Direction Estimation using Optical Flow

**Overview**

This project demonstrates a powerful computer vision technique for analyzing traffic flow by detecting moving vehicles and estimating their direction of travel using **Optical Flow**. By analyzing the motion vectors between two consecutive video frames, this system can differentiate moving cars from the static background, segment them, and quantify traffic patterns.

The primary objectives are to:
1.  **Generate a motion mask** that isolates fast-moving objects (vehicles) from the scene.
2.  **Use optical flow vectors** to compute the direction and count of cars moving left and right.

This project showcases an end-to-end pipeline, from initial image loading to final motion analysis, providing a foundation for more advanced applications in intelligent traffic monitoring, vehicle tracking, and real-time transportation analytics.

---
### 💡 Features

* **Motion-Based Detection:** Uses the Farnebäck optical flow algorithm to estimate motion between frames.
* **Dynamic Motion Masking:** Creates a binary mask by thresholding flow magnitude to isolate moving objects.
* **Robust Segmentation:** Employs morphological operations and area filtering to refine the vehicle masks and remove noise.
* **Directional Analysis:** Calculates the mean horizontal flow (`Vx`) for each detected object to determine its direction (left or right).
* **Vehicle Counting:** Quantifies the number of vehicles moving in each direction.
* **Visualization:** Overlays optical flow vectors and bounding boxes on the original frames for clear visual feedback.

---
### 🧱 Pipeline Structure

The project is executed in a single MATLAB script and is broken down into five main steps:

1.  **Load Image Frames:**
    * Two consecutive frames (`Rt9Frame1.png` and `Rt9Frame2.png`) are loaded.
2.  **Initialize & Estimate Optical Flow:**
    * An `opticalFlowFarneback` object is created.
    * The flow field between the two frames is estimated, capturing pixel-wise motion.
3.  **Create Mask of Fast-Moving Regions:**
    * The flow magnitude is thresholded to identify areas with significant motion.
    * The resulting binary mask is cleaned using area filtering and morphological closing to create solid regions for each vehicle.
4.  **Apply Mask & Visualize Detections:**
    * The motion mask is used to segment the cars from the original frame.
    * Bounding boxes are drawn around each detected region for visualization.
5.  **Analyze Velocity & Determine Traffic Direction:**
    * The mean horizontal velocity (`Vx`) is calculated for each segmented region.
    * Vehicles are classified as moving "left" or "right" based on a velocity threshold, and the counts are displayed.

---
### 📂 File Structure

```
📁 vehicle-motion-estimation-optical-flow/
├── 📄 estimate_traffic_flow.mlx       # Main MATLAB script with all code
├── 📄 Rt9Frame1.png                 # Input Frame 1
└── 📄 Rt9Frame2.png                 # Input Frame 2
```

---
### 📊 Input Data Schema

The project uses two sequential image frames as input:

* **`Rt9Frame1.png`**: The first image frame (time `t`).
* **`Rt9Frame2.png`**: The second, subsequent image frame (time `t+1`).

Both inputs are standard `.png` image files.

---
### 🛰️ Data Source & Attribution

The image data used in this project is provided by **MathWorks** for the **Object Tracking and Motion Detection with Computer Vision** course.

---
### 🔧 Requirements

* **MATLAB** (R2022b or newer recommended)
* **Image Processing Toolbox™**
* **Computer Vision Toolbox™**

---
### 🛠️ Setup Instructions

1.  Place the main MATLAB script (`estimate_traffic_flow.m`) and the two input images (`Rt9Frame1.png`, `Rt9Frame2.png`) in the same directory.
2.  Ensure this directory is set as the current folder in MATLAB.

---
### 🚀 Usage

1.  Open the `estimate_traffic_flow.m` script in MATLAB.
2.  Click the **Run** button to execute the script.
3.  Observe the figures that are generated, showcasing each step of the pipeline.
4.  Check the MATLAB Command Window for the final output, which prints the number of cars detected moving left and right.

---
### 👤 Author

**Kirubhakaran Meenakshi Sundaram**

💼 LinkedIn: [https://www.linkedin.com/in/kirubhakaranm/](https://www.linkedin.com/in/kirubhakaranm/)

---
### 📚 Additional Resources

* [Optical Flow Overview](https://www.mathworks.com/discovery/optical-flow.html) - Official MATLAB documentation explaining optical flow concepts.
* [opticalFlowFarneback Object](https://www.mathworks.com/help/vision/ref/opticalflowfarneback.html) - Documentation for the Farnebäck algorithm implementation.
* [regionprops Function Documentation](https://www.mathworks.com/help/images/ref/regionprops.html) - For measuring properties of image regions, including mean intensity.
* [bwareafilt Function Documentation](https://www.mathworks.com/help/images/ref/bwareafilt.html) - For filtering binary images based on object area.
