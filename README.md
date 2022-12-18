# AI-Workout-Trainer
Finding a discrete definition for fitness is impossible. According to the dictionary, fitness means: “the quality or state of being fit. Fitness doesn’t have to mean that you’re an ultra-marathoner or that you can perform one push-up or one hundred. Fitness can mean different things to different people. In the fast paced world that we are living in, physical fitness is falling behind. The project aims to solve this issue through a web based fitness application. Most of the existing fitness app that are currently being used, only allows the users to track their walking, running and in a few cases cycling activities. The project however, focuses on a wide range of physical activities. It is capable of monitoring a user’s exercise routine and predicting the intensity of the workout done by them. 

2.	INTRODUCTION:
                         Our proposal expands on the existing fitness Apps to motivate users to perform diverse physical workouts to achieve fitness goals and rewards coins, which they can redeem in an in-app store for free products or discounts. This 

development is part of a broader trend of self-tracking (the ‘quantified self’), whose effects are discussed in an increasing number of publications in the humanities and social sciences. The main concentration of this proposal is to calculate the user’s activity intensity. The web application provides a demo video that helps the user with the workouts. By leveraging the latest machine learning technology, we replace the traditional learning approach in which users simply follow an exercise video with a more enjoyable interactive experience in which users get feedback on their body movements in real-time. These features would help even the elderly to practice exercises more effectively and reduce the risk of injury.

3.	APPROACH AND DESIGN:

To gain maximum benefit out of a workout routine, it is necessary to maintain the correct postures and make the right movements. By using the proposed solution, users can determine if they are performing the moves correctly using AI to track their movements. 

4.	OVERALL DESCRIPTION OF APPROACH:

1.	The user needs to follow a demo video and imitate the movements, so the product will play videos.
2.	To provide valuable real-time feedback to the users, body movements will be captured with the front-facing camera.
3.	The user also needs to specify their details like age as the scoring system used is age-based.
4.	The user needs to complete a calibration step for each exercise. This step identifies the points to be monitored using the Openpose framework. This calibration needs to be done before starting any new exercise set.
5.	For different workout exercises, specific points of focus are chosen. The intensity of the workout is calculated using the speed of movement of these points.

4.1	  ARCHITECTURE DIAGRAM:

 

5. OPENPOSE ARCHITECTURE: 

       OpenPose is the first real-time multi-person system to jointly detect human body, hand, facial, and foot key-points (in total 135 key-points) on single images. 

5.1 Openpose Architecture diagram
 

•	In first step the image is passed through baseline CNN network to extract the feature maps of the input In the paper. In this paper the authors used first 10 layers of VGG-19 network.
•	The feature map is then process in a multi-stage CNN pipeline to generate the Part Confidence Maps and Part Affinity Field
•	Part Confidence Maps:
•	Part Affinity Field
•	In the last step, the Confidence Maps and Part Affinity Fields  that are generated above are processed by a greedy bipartite matching algorithm to obtain the poses for each person in the image.

5.2	BODY MOVEMENT RECOGNITION USING OPENPOSE:

•	Shown below is an example of body-weight squat and pose estimation using Openpose. We defined one squat repetition round as 6 s; thus, one set of the exercise will be 60 s. In every repetition round, first, the exerciser is told to look straight ahead, put their arms parallel to the ground, make sure their knees are not inward; then “sit back” in 3 s, not round the back and bend the knees; at last, lift in the rest 3 s, instead of standing up immediately. Accordingly, every repetition was to be evaluated according to three indices: knee width, hip position, and rhythm. 
                  
             5.2.1- Pose detection for squats  
5.3  VERIFICATION OF MOVEMENTS USING ML AND AI: 

 It is important for the app to recognize key body movements. To do this, we transformed the body movement recognition problem into a typical machine learning classification problem. Below is a sample of how we defined the key.

5.3.1- ML for pose recognition

We trained a traditional deep neural network to classify user body movements and  to recognize correct movements for each exercise. When a user chooses to do a particular workout routine, his/her movements are compared against the pre-existing model. A rep is considered valid only if it matches the predefined movements.

5.5 INTENSITY CALCULATION:

To determine the intensity of each lap of a particular workout routine, we have designed the following algorithm: 

1. For each exercise we focus on different points identified by the present.
2. For example, for squats, the points of focus would be the hip and the ankle. As the user does the exercise, we calculate the distance moved by the hip about the ankle as a function of time. 
3. The intensity is calculated by determining the speed of motion calculated by taking the distance moved by these points by the time taken to move that distance.
4. This calculation is repeated for each rep of the exercise; hence we can identify the intensity of each movement done by the user.
5. Based on the intensity, the user is given a score for each rep.
6. At the end of the set, coins are allotted based on the total score.

5.4  SCORING SYSTEM:

1. Firstly, for each exercise an optimal intensity is identified. 
2. This optimal intensity is the average intensity achievable by a person belonging to a particular age group. 
3. A lower bound of the intensity is identified for each exercise, a rep is considered valid if it crosses the lower bound.
4. Different optimal intensities are chosen for users of different age groups.
5. There are three intensity ranges categorized as low, moderate, and vigorous. A variable for the total score and a variable for the Current rep score is maintained. The points are assigned for the current lap score based on the intensity range it falls in. 
6. Additionally, when a user crosses the optimal intensity set for his/her age group a bonus score is added.
7. The bonus score is calculated using the formula:
        Bonus score= 2 x (Current rep intensity-Optimal intensity) 

6	SUGGESTED TECHNOLOGY:

•	OpenPose is a Real-time multiple-person and human's jointly key points detection library
•	Mediapipe
•	Python

7	ADDITIONAL DETAILS:

•	After installing the app, the user can log in by providing their details. Also, the user will be allowed to enter their age, gender, weight, height and difficulty level, and the type of workout. 
•	Based upon the user’s fitness goals, the app suggests a personalized workout routine with sets of exercises. 
•	The ML framework makes sure that the user executes the exercises in a correct manner, by checking postures for each rep. Hence, we reduce the chances of injury.
•	A different optimal intensity is selected for different age groups because the same workout could be more or less intense based on a person’s age. 
