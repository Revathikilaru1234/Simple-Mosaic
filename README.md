📌 Overview

This project demonstrates an image mosaic generation technique using Python and OpenCV. A smaller image is repeatedly blended over a larger image to create a mosaic effect. This approach highlights concepts of image manipulation, blending, and pattern generation, making it suitable for multimedia and computer vision coursework.

🛠️ Features

Loads and processes both a small and a large image.

Divides the large image into patches and replaces them with the smaller image.

Implements blending (cv2.addWeighted) to create a visually appealing mosaic.

Produces both:

A blended mosaic (where patches are merged with the small image).

A simple mosaic (where patches are directly replaced by the small image).

📂 Project Structure
├── multimedia_project_finalised.ipynb   # Jupyter Notebook with code & outputs
├── README.md                            # Project documentation
└── sample_images/                       # Example images (to be added)

🚀 Installation & Requirements

Make sure you have Python installed along with the following libraries:

pip install opencv-python numpy matplotlib

▶️ Usage

Clone this repository or download the files.

Place your images inside a folder (e.g., sample_images/).

Open the notebook multimedia_project_finalised.ipynb.

Update the paths for your small and large images:

img1_path = 'sample_images/small_image.jpg'   # Small image
img2_path = 'sample_images/large_image.jpg'   # Large image


Run the notebook to generate and visualize mosaics.

📊 Example Code Snippet
import cv2
import numpy as np
import matplotlib.pyplot as plt

def create_mosaic(small_img, big_img):
    h_s, w_s, _ = small_img.shape
    h_b, w_b, _ = big_img.shape

    if h_s > h_b or w_s > w_b:
        raise ValueError("Small image must fit inside big image dimensions.")

    mosaic = big_img.copy()
    simple_mosaic = big_img.copy()

    for i in range(0, h_b - h_s + 1, h_s):
        for j in range(0, w_b - w_s + 1, w_s):
            patch = big_img[i:i+h_s, j:j+w_s]
            if patch.shape == small_img.shape:
                blended_patch = cv2.addWeighted(patch, 0.90, small_img, 0.5, 0)
                mosaic[i:i+h_s, j:j+w_s] = blended_patch
                simple_mosaic[i:i+h_s, j:j+w_s] = small_img

    return mosaic, simple_mosaic

🎯 Learning Outcomes

Practical exposure to image processing using OpenCV.

Understanding of blending operations and pixel manipulation.

Application of multimedia concepts for creative visual output.
