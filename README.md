# Fitness-ai
# Inspiration
The journey to creating FitForm began with a personal challenge. As a fitness enthusiast who often worked out at home, I struggled with maintaining proper form and tracking my progress accurately. The pandemic had shifted many workout routines from gyms to living rooms, and I noticed a gap in accessible technology that could provide real-time feedback without expensive equipment or personal trainers. Traditional fitness tracking apps required manual input or wearable devices, but I envisioned something more intuitive - a system that could "see" and understand exercises just as a personal trainer would. This sparked the idea to leverage computer vision and AI to create an accessible fitness companion for anyone with a webcam.

# What it does
Welcome to Fitness AI – an intelligent posture recognition app built right in the browser. The first part of this project is all about creating a smooth and user-friendly interface. On the left side of the screen, we have the User Profile Panel, where users can enter personal details such as weight, height, age, and gender. These values help in personalizing workout calculations, especially calorie burn. Below the profile section, users can save their profile, start or end a workout, or reset exercise counters at any time. On the right, there’s a live video feed from the webcam, and above it, a canvas that will be used to draw pose detection results. Just below the video, there’s a real-time stat display that updates the number of push-ups, dumbbell curls, calories burned, and time elapsed. Finally, at the bottom of the page, the Workout History Table automatically logs each workout session, helping users track their progress over time.

# MediaPipe Setup and Initialization

The second part focuses on the core logic, where the AI and computer vision come into play. When the page loads, a class called FitnessAI is initialized. This class handles everything – from setting up the webcam to managing exercise detection and user interactions. Using MediaPipe Pose, we bring in real-time human pose estimation. The webcam feed is processed frame-by-frame, and the pose detection model identifies key body landmarks like shoulders, elbows, wrists, hips, and knees. These are essential for understanding how the user is moving. The app overlays these landmarks on the canvas, creating a real-time skeletal view on top of the video. At the same time, the app listens for button clicks — when a user starts the workout, it activates the camera and begins tracking motion. This part ensures the video feed is live, accurate, and responsive to the user’s posture in real time.

# Exercise Detection and Real-time Tracking

Finally, in the third part, we dive into real-time exercise detection and tracking. The app uses angles between joints to understand user movements. For example, when doing push-ups, it calculates the angle between the shoulder, elbow, and wrist to determine whether the arms are bent or extended. It also checks the angle between the shoulder and hip to confirm proper form. A full push-up is counted only when the user goes from a "down" position to an "up" position with correct alignment. The same logic applies to dumbbell curls, but here the app confirms the user is standing and then tracks arm motion based on elbow angle. Calories are calculated using MET values — taking into account the user's weight and the number of reps performed. All this happens in real time. And when the workout ends, the session is logged with details like time, reps, and calories. The user can then see their progress in the history table, making this a complete in-browser fitness tracking experience — powered by AI, and accessible to anyone with a webcam.

# How we built it
FitForm was built as a web application to ensure accessibility across devices without requiring installation. The technology stack includes:

Front-End: HTML5, CSS3, and vanilla JavaScript to create a responsive and intuitive interface. Computer Vision: MediaPipe's Pose library for real-time body landmark detection and tracking. Data Processing: Custom JavaScript algorithms to analyze body positions and determine exercise states. Data Storage: Browser's localStorage API to save user profiles and workout history.

The system works by identifying key body landmarks (shoulders, elbows, wrists, hips) and calculating the angles between them. These angles are then compared against predetermined thresholds to detect specific exercise states. For example, a push-up is counted when the system detects a transition from a "down" position (arms bent) to an "up" position (arms extended). The calorie calculation algorithm uses metabolic equivalents (METs) to estimate energy expenditure based on exercise type, user weight, and duration.

# Challenges we ran into and ## Accomplishments that we're proud of
Camera Access and Initialization One of the most significant challenges was reliable camera initialization across different browsers and devices. Many users experienced the error "Failed to acquire camera feed" when first using the application. Solution: I implemented a robust camera initialization process that:

Verifies MediaPipe libraries are fully loaded before camera access Includes explicit browser permission checks and error handling Uses async/await patterns for proper sequence control Provides clear user feedback for permission issues

Accuracy in Exercise Detection Initially, the system struggled to differentiate between actual exercises and casual movements, leading to false counters. Solution: I refined the detection algorithms by:

Analyzing body positioning to ensure proper exercise form (e.g., checking if the body is parallel to the ground for push-ups) Implementing stage detection that requires complete motion cycles Adding threshold adjustments to account for different body types and movement styles

Browser Compatibility MediaPipe's functionality varied significantly across browsers, with certain features working in Chrome but failing in Safari or Firefox. Solution: I standardized the code to use the most widely supported features and added browser detection to provide appropriate guidance to users. The application now focuses on optimizing for Chrome while providing fallback options for other browsers. User Experience During Workouts Early testers found it challenging to maintain visibility of the screen while performing exercises, particularly floor-based movements like push-ups. Solution: I redesigned the UI to provide large, clear visual feedback and audio cues to confirm repetitions. The counter displays were enlarged and positioned prominently to be visible from various workout positions.

# What we learned
Building FitForm expanded my knowledge in several key areas:

Computer Vision Applications: I gained hands-on experience with MediaPipe's pose estimation library, learning how to track human body landmarks in real-time. Exercise Biomechanics: Researching the proper form for exercises like push-ups and dumbbell curls taught me about the specific angles and positions that define correct movement patterns. Front-End Development: Creating an intuitive user interface that displayed real-time feedback required me to improve my HTML, CSS, and JavaScript skills. Data Persistence: Implementing workout history tracking with localStorage taught me about client-side data storage options. Real-Time Processing: Managing continuous video input while simultaneously analyzing posture and updating the UI presented interesting challenges in performance optimization.

# What's next for Fitness Ai
Fitness ai is continuously evolving. Planned enhancements include:

Support for additional exercise types (squats, lunges, planks) Machine learning improvements to adapt to individual movement patterns Workout routine creation and scheduling Social features for friendly competition Integration with other fitness platforms and wearables

By combining computer vision with accessible web technology, FitForm aims to democratize access to quality fitness feedback and tracking, making proper form and progress monitoring available to everyone with a camera-equipped device.

# Built With
html5
javascript
opencv
python
