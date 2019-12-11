# Eye-gaze-controlled-keyboard
1 INTRODUCTION
1.1 BACKGROUND
Various advances in eye-gaze tracking and estimation over the past few years had led to the development and deployment of promising eye-gaze estimation techniques and applications for human-computer interaction. Historically, research on gaze tracking dates back to the early 19th century, starting with confined eye-tracking techniques. An Eye-controlled virtual keyboard might be an effective alternative input mechanism for users with disabilities who cannot use a conventional keyboard. Although various hardware keyboards are available with disability-friendly dual keyboard options, the on-screen keyboard provides a handy utility which can act as a substitute while working at different stations or on a different platform, for example, laptops, mobiles which is limited on screen size.  The system is created to allow users to interact with a computer exclusively only just by moving their eyes. The system prompts the user to make eye – gaze movements and eye blinks to navigate the virtual keyboard.
1.2 STATEMENT
Over twenty million individuals suffer from stroke annually and because of loss of motor and/or speech skills, they face heaps of difficulties in human activity effectively. Augmentative and alternative communication (AAC) based methods and technologies have been designed to provide new effective means of communication to assist these people. In general, AAC systems embody an outsized set of gestural, alphabetical, and iconic communications. This space of analysis is growing vastly to satisfy the wants of severe speech and motor-impaired people, such as aphasia and tetraplegia patients. An AAC system will be divided into 2 distinct components: input device(s) and communication package
1.3 MOTIVATION
The majority of the studies centered on systems performance (increasing text entry rate and reducing error rate) while not considering multimodality (i.e. the inclusion of several input devices). Moreover, their area unit restricted studies associated with gaze-based virtual keyboards. In addition, the validations of most of the proposed systems are limited to healthy users. The neurodegenerative malady slowly puts the nerves that is employed to trigger the striated muscle movement out of operating order. Whenever this happens, the muscles begin to weaken from a lack of use and eventually stop working altogether. Even involuntary movements like breathing cease. Keeping this in mind the aim of the work is thus to optimize gaze-control virtual keyboard that takes into consideration each the gaze characteristics and therefore uses the language script.
1.4 CHALLENGES
For the use of eye gaze tracking we setup cameras are mounted on a  the front camera is used to track user gaze to activate functions such as locking/unlocking phones, interactive displays, dimming backlights or suspending sensors. Within each of these use cases there exists a wide range of system configurations, operating conditions and varying quality of imaging and optical components. Furthermore, the variations in eye-movement and biological aspects of individuals lead to challenges in achieving consistent and repeatable performance from gaze tracking methods. Thus, despite several decades of development in eye gaze research, performance evaluation and comparison of different gaze estimation techniques across different platforms is a still a difficult task. 



    1 PLANNING AND REQUIREMENTS SPECIFICATION
        1.1 SYSTEM PLANNING
           System planning is the first phase of the development life cycle in which total information needs are identified, analyzed prioritized and arranged. Goals and expectations of the new system are created in this phase. Two major activities involved in system planning are 
       1. Identifying the system development project, 
           2. Planning the system development project. 
           There are two approaches in identifying the system development project namely top-down approach and bottom-up approach. The top – down approach is carried out the complex module is divided into submodules. 
           
The app will be built in 2 main parts.
1) Eye detection: detection of the eyes, their movements and perhaps the blinking.
2) Virtual keyboard: a keyboard on the screen where the user would select the letters by just using our eyes.
The second activity is planning the system development project where scope and constraints, benefits, development time and costs, and problems or opportunity are identified.




2.2 REQUIREMENTS
2.2.1 USER REQUIREMENTS
    • User must be able to control the left and right partition of the keyboards.
    • An error message must be thrown if there are multiple faces detected at the same time.
    • An eye -  care lighting condition (Less blue light ) emiting screen must be used 
    • A fully eye controlled system without any physical interferences must be established.

2.2.2 NON-FUNCTIONAL REQUIREMENTS
    • The blink detection shall be detected every time the estimation technique is satisfied. 
    • Only one can able to control the keyboard, multiple gestures should be found and averted. 
    • Reliability of the blinks detections shall be established.
    • The system should perform under certain lighting conditions.
    • An option to opt the left and the right side of the keyboard should be made available all the time. 



2.3 SYSTEM REQUIREMENTS
2.3.1 HARDWARE REQUIREMENTS
HARDWARE
SIZE
Graphics Card
OpenGL graphics card with at least 256 MB of on-board memory.
RAM
4 GB (8GB Recommended)
Free Hard Disk Space
10 GB or more

Web Camera 


					Table 1 Hardware Requirements

2.3.2 SOFTWARE REQUIREMENTS
    • Operating System (Windows 10 / Ubuntu 18.4)
    • Anaconda Environment
    • Python 3.6 
    • Shape detector packages




3 SYSTEM DESIGN
 The Eye – Blink can be detected using three approaches:
An eye is blinking whenever:
    1. The eyelid is closed
    2. We can’t see the eyeball any more
    3. Bottom and upper eyelashes connect together
                                Fig. 1 : General Architecture of Face detection








                                                Fig. 1.1 Gaze detection 

4 IMPLEMENTATION 
The goal of such app is to write without using the hands. Such applications are really important for people affected by quadriplegia who completely lost the control of their limbs.
The architecture of the app
The app will be split up and  built in 2 main parts, they are
Eye detection: detection of the eyes, their movement and perhaps their blinking.
Virtual keyboard: a keyboard on the screen where we’re going to select the letters by just using our eyes.



Using the face landmarks detection approach we can find 68 specific landmarks of the face. To each point there is a specific index assigned.
The goal is to detect the two eyes both seperately.
Left eye points: (36, 37, 38, 39, 40, 41)
Right eye points: (42, 43, 44, 45, 46, 47)








                                             

                                                   Fig 2 : Face Landmark points

Once we know the exact position of the eyes is detected it is easier to start working with them, A-line one crossing the eye horizontally and one crossing the eye vertically is drawn so that the blink can be detected.








                                                   Fig 3 : Eye Sample illustration
Now the most important task is to detect whenever the user blinks. The Eye – Blink can be detected using three approaches:
An eye is blinking whenever:
    • The eyelid is closed
    • The eyeball can no more be able to be seen 
    • Bottom and upper eyelashes connect together
And also we need to take into account that all these actions must happen for a short amount of time (approximately a blink of an eye takes 0.3 to 0.4 seconds) otherwise it means that the eye is just closed. As we already drew a vertical and horizontal line crossing the eye. 
This is how the lines look like when the eye is open.




					                                             Fig 4: Open Eye


This is when the eye is closed.



					                                                     Fig. 5 : Closed Eye

One can clearly see that the size of the horizontal line is almost identical in the closed eye and in the open eye while the vertical line is much longer in the open eye in comparison with the closed eye.
The vertical line almost disappears in the closed eye.
The horizontal line is taken as the point of reference, and from this, the ratio in comparison with the vertical line can be calculated. If the ratio goes below a certain number we will consider the eye to be closed, otherwise the eye is open.
The ratio number later is used to detect and we can finally define when the eye is blinking or not. In this case, the ratio number 5.7 is found to be the most reliable threshold value. The process used is to see a keyboard on the screen, light up each key every second or so and when the key we’re interested in is on, we simply close our eyes.
Since the keyboard has 26 letters of the alphabet, plus space and the backspace key will also be needed, just to run through all the keys lighting up each for one second, it will take half a minute each time.
Thus to avoid such a time delay we divide the keyboard into two parts. If the user looks on the left side only the left part of the keyboard will be activated, while if the user looks on the right side only the letters on the right part of the keyboard will light up. The letters in the left and the right side of the keyboard are illustrated below.



								
		           Fig. 6 : Keyboard keys after dividing into two parts

To detect the gaze we need first to understand how the eye appears when it’s looking in different directions, more specifically to detect if the eyes are looking to the left, the right or the center.

			            Fig. 7 : Eye – sclera representation
By looking at the image above, it’s that the sclera (white part of the eye) fills the right part of the eye when the eye is looking at the left, the vice-versa happens when it’s looking to the right and when it’s looking to the center the white is well balanced between left and right. Using this aspect, white part of the eye (sclera) is detected, the idea is to split the eye into two parts and to find out in which of the two parts there is more sclera visible.








						    Fig.8 : Eye gaze detection (White pixel count)
We divide the white pixels of the left part and right part thus we get the gaze ratio. With the gaze ratio, we could conclude where a specific eye is currently looking.
Normally both the eyes look in the same direction, so detecting the gaze of a single eye cannot give us accurate output, hence to be more precise we detect the gaze of both eyes and use both values to detect the gaze ratio. Predominantly if the gaze ratio is smaller than 1 when looking to the right side and greater than 1.7 when the eyes are looking to the left side.
The keyboard is divided into two parts, and before pressing each letter we need to select the part.
The left side contains the letters: Q, W, E, R, T, A, S, D, F, G, Z, X, C, V.
The right side contains the letters: Y, U, I, O, P, H, J, K, L, V, B, N, M, and space bar.
Once the user runs the script we see three different windows containing respectively: the keyboard, a whiteboard and the capture from the webcam.

1) Choose the keyboard’s side:
The webcam is controlling the position of the user’s eyes, so if one wants to select the left side the user needs to look on the left for around a second, for the opposite side the user needs to look on the right.






				                                  
                                                                       
                                                    Fig . 9 : Virtual Keyboard

2) Press a key
Let’s supposed that we chose the Right side. Now we will see the keys contained on the right side. To press a key we need to wait that the key lights up, and then we blink our eyes. We keep them closed until we hear a sound. That sound means that the key has been pressed.






				
                                           
                                          Fig. 10 Right – Side of the keyboard

3) Repeat step 1 and 2 to press a new key.
Each time we press a key, we need to repeat the step 1 and 2.Each time the key is pressed, it is added to the white board. For example the word “Hello” is typed below.










5 RESULTS AND DISCUSSION
 The performance of the eye-gaze controlled Virtual Keyboard may be affected considerably with patient teams, especially, stroke patients. Keeping these issues in mind, an optimized gaze-controlled virtual keyboard has been designed wherein inputs can be provided using a portable non-invasive eye-tracker with or without a single input switch. This system may additionally facilitate patients to enhance the loss of motor skills by the addition of alternative doable input modalities (e.g. motor imagery) wherein search and target selection of items can be achieved by gaze and motor imagery, respectively.

6 CONCLUSION AND FUTURE WORK
The majority of the studies targeted upon systems performance (increasing text entry rate and reducing error rate) while not considering multimodality (i.e. the inclusion of several input devices). Moreover, there square measure restricted studies associated with gaze-based virtual keyboards. In addition, the validations of most of the proposed systems are limited to healthy users. The solution given for the chosen problem statement which is a lack of able communication tools for people affected by quadriplegia, who completely lost the control of their limbs or amyotrophic lateral sclerosis (ALS) also referred to as motor neuron disease in some countries, is the eye – gaze controlled keyboard. A recent study provided a viable usage of eye-gaze indices (i.e., eye fixation, smooth pursuit, and blinking) for the assessment of pathological states in stroke patients. Therefore, a doable extension of the projected system could also be used for assessment functions to assist patients to see their current status. The cost involved in the existing communication tools such as Speech – generating device which late scientist Stephen Hawking used is high.This proposed application is simple, robust and effective. It can be also be integrated with a Word predicting system that enables prediction of words that the user tries to generate with its past communication. Also, ACAT – Assistive Contextually Aware Toolkit can be integrated, this creates shortcuts for skype calls, read emails, etc. This could also pave the way to replacing traditional input devices that interact with the computer and optimizing the computing speed.

REFERENCES:
1) C. Kumar, R. Menges, and S. Staab, “Eye-controlled interfaces for multimedia interaction,” IEEE MultiMedia, vol. 23, no. 4, pp. 6–13, Oct 2016
2) C. Schaefer, R. Menges, K. Schmidt, M. Kuich, and T. Walber, “Schau genau! an eye tracking game with a purpose,” in Applications for Gaze in Games, 2014
3)  X. Zhang, H. Kulkarni, and M. R. Morris, “Smartphone-based gaze gesture communication for people with motor disabilities,” in CHI 2017 Proc. ACM, 2017
4)  C. Dickie, R. Vertegaal, C. Sohn, and D. Cheng, “Eyelook: using attention to facilitate mobile media consumption,” in 18th UIST Proc. ACM, 2005
4)  C. Holland and O. Komogortsev, “Eye tracking on unmodified common tablets: challenges and solutions,” in Proc. of the Symposium on Eye Tracking Research and Applications. ACM, 2012.
5)  V. Vaitukaitis and A. Bulling, “Eye gesture recognition on portable devices,” in Ubicomp 2012 Proc. ACM, 2012.
6)  D. Kim, O. Hilliges, S. Izadi, A. D. Butler, J. Chen, I. Oikonomidis, and P. Olivier, “Digits: freehand 3d interactions anywhere using a wrist-worn gloveless sensor,” in 25th UIST Proc. ACM, 2012
[7]  N. Van Huan and H. Kim, “A novel circle detection method for iris segmentation,” in CISP 2008 Proc., vol. 3. IEEE, 2008
[8]  D. W. Hansen and Q. Ji, “In the eye of the beholder: A survey of models for eyes and gaze,” IEEE Trans. Pattern Anal. Mach. Intell., vol. 32, no. 3, pp. 478–500, Mar. 2010.
[9]  L. R. Young and C. Sheena, “Methods and designs: Survey of eye move ment recording methods,”Behavior Res. Methods Inst.,no.5,pp.397–429,1975
[10] E. Guestrin and M. Eizenman, “General theory of remote gaze estimationusing the pupil center and corneal reflections,” IEEE Trans. Biomed. Eng., ol. 53, no. 6, pp. 1124–1133, Jun. 2006














APPENDIX
SCREENSHOT
















