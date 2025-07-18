PLEASE SEE A MORE RECENT VERSION OF THIS PROJECT AT THIS LINK: https://github.com/Torquoal/VR_Zoomorphic_Robots/tree/main

This Unity project explores different affective expression modalities for a real-life zoomorphic robot using a virtual reality overlay. It contains scenes, GUIs and scripts that allow for systematic evaluation of the interfaces, as well as a prototyping menu where modes can be freely actuated and combined at will.

<b>Click below to watch the video</b>
[![Watch the video](https://img.youtube.com/vi/B5ucAt7Fp0I/maxresdefault.jpg)](https://youtu.be/B5ucAt7Fp0I)

**How to use:**

The virtual robot should be overlaid over a real life equivalent such that touching the robot in VR results in touching the physical robot. This can be achieved either by using the meta quest base recentring function, or using the Calibration scene while running the application is Quest Link and pressing the 1, 2 and 3 keys on the host PC to set the 3 users x,y and z direction from the robot. Inside the Qoobo GameObject is an internal object with the Grabble and Hand Grab Components called QooboTouchDetector which is used to detect when the user touches the robot and trigger a function hosted by ScriptHost, which contains components for all the scripts which can trigger all the functions of the robot. The script which is bound to the QooboTouchDetector changes based on the scene to trigger a different modality. Each modality features a script to control how it presents the 5 different emotions and to pass its current details to the RatingScript which is used to log users responses on the Likert GUI. Tail movements are handled by the QooboManager script.


**Disclaimer**: This code was constructed with a quick and naiive approach to run a study on the modalities by somebody who is a researcher first, designer second and coder third. It is far from a beautiful piece of software engineering. Feel free to continue to implement modalities or emotions by copying what has been done here, but also feel free to code this with an actually nice and extendable set of classes if you wish.

Once in the Base scene you can turn to the right to activate experimental mode or prototyping mode. 

**Experiment Mode**
In the experimenting mode the user can place their hand on the robot to be shown an expression using one modality (e.g., light, or sound, or tail movement). After 7 seconds the expression will stop and three Likert scales will appear. submitting these scales will then alow the user to put their hand on the robot for another expression. After 5 expressions (for 5 emotions), the user can press a button to proceed to the next round, loading as new scene that triggers a different expression modality, and the same process repeats until all 7 modalities are shown. The order is modalities can be specified in the Load Condition component of the ScriptHost object.

**Prototyping Mode**
In the prototyping mode users can open one of 5 menus, one per emotion, to activate or toggle the display modalities for that emotion.

**Modality Implementations**
In terms of how each modality is implement for future development or additions:

_Light_

Implement with a Light Source under the robot, located in the Mood Lights object of the Hierarchy. Different colours can be enabled by toggling different emotion objects on or off. E.g., Angry is set to red. Colours can be edited for current objects or new objects added. Alternatively this could be refactored to change the colour of the lightsource via script.

_Face_

The face is added to the base robot object using an URP decal projector. Swapping facial expressions requires only that the material in the projector is swapped, which can be done by script (see FaceManager) or manually. Face decals  are found in Face Decals folder.

_Speech & Sound_

Speech and Sound works by playing specific files from an AudioSource in the Virtual Environment, under the EmotiveSound object. Setting the touch detector inside Qoobo or any button to trigger <AudioSource>.Play for the appropriate object will then play the sound as needed.

_Tail_

The Tail is a pill-shaped GameObject. There are 5 functions with different movement patterns for each emotion defined the QooboManager script which can be triggered or have their values adjusted as needed.

_Text & Emoji_

Text and Emoji are presented via simple canvases placed over the robot, located within the Qoobo object in the hierarchy. Different text or images can be displayed either by adding scriot support to swap text/materials or by toggling different preset objects present in the hierarchy. Emoji are found in the Materials folder.



