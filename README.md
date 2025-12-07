Face Recognition System (MediaPipe + LBPH)

This project builds a full face-recognition workflow using MediaPipe Face Mesh for detection and OpenCV’s LBPH algorithm for identifying people based on facial features.

What It Does

👁️ Face Detection powered by MediaPipe Face Mesh

🧠 Face Recognition using OpenCV’s LBPH classifier

📷 Simple Image Collection via webcam

🏗️ Model Training from your captured face data

⚡ Live Recognition using your webcam feed

Folder Layout
face_recognition_mediapipe_lbph/
├── capture.py              # Grab face images from webcam
├── train.py                # Build the LBPH recognition model
├── predict.py              # Run real-time face recognition
├── dataset/                # Collected images go here
│   ├── Princesse/
│   └── Benitha/
├── models/
│   ├── lbph_model.xml      # Saved LBPH model
│   └── label_map.json      # Name-to-ID mapping
└── README.md

Setup

Install the needed libraries:

pip install opencv-python mediapipe opencv-contrib-python


You need:

opencv-python for camera/image handling

mediapipe for facial landmark detection

opencv-contrib-python because LBPH lives in the contrib modules

How to Use It
1. Collect Training Images

Run:

python capture.py


Then:

Type your name

Look at the camera while images are captured

Press Q to stop

Images will be stored in dataset/<your_name>/.

2. Train the LBPH Model

After gathering data for each person:

python train.py


The training script:

Reads all dataset folders

Converts images to grayscale

Assigns numeric labels

Trains the LBPH recognizer

Saves the model and label map inside models/

3. Run the Recognition Script
python predict.py


You’ll see:

A bounding box around every detected face

The predicted name

The LBPH confidence value

Press Q to close the window.

Behind the Scenes
capture.py

Uses MediaPipe to find face landmarks

Calculates the face bounding box

Crops the face area and saves it as a training image

train.py

Reads all images in dataset/

Converts everything to grayscale

Builds label indexes

Trains an LBPH model

Outputs lbph_model.xml + label_map.json

predict.py

Live detection using MediaPipe

Extracts face crops

Feeds them to the LBPH recognizer

Shows identification results on the webcam feed

Typical Workflow

Capture images for each person

Train the LBPH model

Run Prediction in real time

You can repeat the capture+train steps anytime you want to add more people.

Extra Tips

Make sure lighting is decent while capturing

Capture multiple angles for better results

More training images = more consistent predictions

LBPH is a classic, fast method that works great without deep learning