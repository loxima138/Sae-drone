# Sae-drone

This project was proposed by my school, the IUT of Tarbes in France as I was in the GEII course.
The goal was for us to learn how to control a DJI Tello drone. To help us through, we had a project specification document.

## Overview

The drone is controlled via Python using the `djitellopy` library. The main feature is autonomous color tracking: an OpenCV pipeline detects a target color in the camera feed, and a proportional controller adjusts the drone's movements in real time to follow it.

## Features

- Real-time color detection using OpenCV (HSV masking)
- Proportional control loop for smooth tracking
- State machine architecture for flight management (takeoff, tracking, landing, emergency stop)
- Live video feed processing

## Project Structure

Each part of the porject holds the name of the step in the project specification document

## Requirements

- Python 3.x
- `djitellopy`
- `opencv-python`
- `numpy`

Install dependencies:
```bash
pip install djitellopy opencv-python numpy
```

## Usage

1. Power on the Tello drone and connect to its Wi-Fi network
2. Run the main script:
```bash
python main.py
```

## How it works

The camera feed is processed frame by frame. Each frame is converted to HSV colorspace and masked to isolate the target color. The centroid of the detected region is compared to the frame center, and the error signal drives a proportional controller that sends velocity commands to the drone.
