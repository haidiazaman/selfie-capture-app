# Python demo app for Gojek Hackathon

<div style="display: flex; gap: 10px;">
    <img src="https://github.com/haidiazaman/secure-face-capture-python-app/blob/main/imgs/left_eye_blocked.jpg" alt="Left eye blocked" width="250"/>
    <img src="https://github.com/haidiazaman/secure-face-capture-python-app/blob/main/imgs/right_eye_blocked.jpg" alt="Right eye blocked" width="250"/>
    <img src="https://github.com/haidiazaman/secure-face-capture-python-app/blob/main/imgs/mouth_blocked.jpg" alt="Mouth blocked" width="250"/>
</div>

View the demo using this link: https://drive.google.com/drive/folders/1P73Dhn_2g_7a7kMbua8SP0smXhi9BuKV?usp=sharing

# Background / Objective
This app was developed during a 1 day company hackathon during my internship in Gojek / Goto Financial. The purpose of this app is to ensure that users are able to take a good quality selfie. Companies around the world have a selfie-capture as part of their onboarding process, face verification process, etc. Most of these selfie capture processes do not include checks to ensure certain potential issues like users wearing a mask, portion of face blocked, etc. This leads to issues like inappropriate images for usage in other models further down the pipeline, waste of storage resources of invalid images etc. As such, I trained 2 separate models, an eye blink model and a mouth block identification model to be able to detect if these regions of the face is blocked. This will then indicate to the user to retake their selfie and inform them of the error (which part of the face is blocked).

# Method 
The eye blink model has three classes, it is able to detect open, close and block eye. The mouth block model has 2 classes (block / no block). In this 1 day MVP, only a demo of the blocking capability is shown. Both the eye and mouth models are used only to detect block or no block.

# Future work 
A mouth blink model can be trained, similar to the eye blink model for liveness procedure. The eye and mouth blink models can be enhanced in robustness through ongoing training that incorporates new strategies employed by attackers attempting to overcome its defenses. When this has passed, the app will take a few seconds to ensure that the face is not blocked. This is done via several other models that will check for any face blocking items across this parts of the face. The interesting part here is that the app will be able to tell the user which part of the face is blocked. This is an improvement over current face quality models which may include a "Block" label which only tells you that the face is blocked without specifying which part. This may be frustrating for users who may repeatedly be rejected without knowing the exact reason. This frustration multiplied by thousands of users could potentially lead to thousands of dollars lost by the company as users give up and decide not to onboard onto the companies' app. After this entire process, the selfie is taken. This project can be taken further by deploying on Android (will need to learn Android development).

# Motivation
This is the codebase for my project to summarise my learnings and work done during my internship in GoTo Financial (Gojek) as a KYC Data Scientist, from Sep - Dec '23. I led the liveness team's efforts in developing an eye blink model that was an essential part of our demo app submitted for Level 1 ISO Liveness Face Anti-spoofing application. Throughout this project, I navigated the entire data science lifecycle — from mining data in production to crafting scripts for model training. Data cleaning involved a combination of manual methods and soft labels, where a separate model was trained to make predictions on this noisy data to ‘soft’ label them, if confidence scores exceeded a set threshold. During this 1 day Gojek hackathon I developed a Python app that is able to detect face blocking items by training specific face region models. I was pleasantly surprised at being able to develop the necessary models and the Python app all in 1 day. 

# Potential flaws
The app is not flawless. The liveness check is a simple eye blink model. After the eye blink has passed, a fraudster could potentially just swap out a printed face to do the face checking before the selfie is taken. This is obviously an issue. The ideal way is to maybe maintain another model checking the liveness score of the selfie throughout the entire selfie-capture process in other to identify any face swaps in real-time, but this is beyond the scope of this project (or i might try this in the future). This can also be done without the use of a liveness check model. Instead a pixel similarity check can be deployed in the app logic, that checks the average similarity of the frames to be above a certain threshold.
