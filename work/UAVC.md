---
layout: page
permalink: /work/UAVC/index.html
title: UAVC
---

## Trajectory generation and control architecture of zero-sample aircraft based on GPT-4

### Experimental Objectives
Build a macro-micro instruction generation system based on a large language model to achieve autonomous flight control and path planning for quadcopter vector drones. The goal is to establish a direct mapping from "orders" to robot "behavior" using a language model, avoiding the use of directly assembled instruction sets (which would require collecting machine data and more complex sequences of instructions to train the model's ability to handle environmental changes in a supervised or semi-supervised manner, a mainstream research direction with high costs, not adopted here). We aim to leverage large model inference methods to provide addressing cues for path planning, thereby enhancing the zero-shot generalization capability of the drone system.
<br>

### Feasibility Discussion
Large models possess certain common-sense problem-solving abilities (for example, in simple tasks, they can provide alternative solutions such as "assume a straight path through obstacles and change the path slope radially where it overlaps with obstacles") and strong code generation capabilities (evident in generating machine control statements like PID commands for guiding hardware motion). These capabilities make it possible for large models to serve as "task processing centers" and "task dispatch centers." The recent release of VoxPoser has also enabled language model-guided 3D environmental interactions, offering potential for simple path planning. In the ideal vision, we aim to achieve a series of actions from user language expression to autonomous drone "problem-solving, optimization, and execution."
<br>

### Algorithm Module Design and Differentiation<br>
1. Data Collection and Processing:<br>
    · Utilize monocular RGB-D odometry for environmental perception and SLAM modeling to obtain real-time data about the drone's surroundings.<br>
    · Collect data from various environmental scenarios, including normal flight and the presence of obstacles, for model training and testing (LOG).<br>
    · Open datasets can be directly used for simulation testing.<br>
2. Establish Perception and Understanding Modules:<br>
    · Model the collected environmental data to detect and identify important elements such as obstacles, paths, targets, etc.<br>
    · These perception modules can be used to generate semantic information about the environment, aiding the model in understanding the current situation.<br>
3. Construct an NLP Module:<br>
    · Design and train a language model to understand and generate natural language commands.<br>
    · This module can accept user language input and convert it into "macro/micro-instructions."<br>
4. Integrate Perception and NLP:<br>
    · Integrate the perception and NLP modules to enable the model to understand environmental data and generate corresponding instructions.<br>
    · This can be achieved through deep reinforcement learning methods, allowing the model to learn how to make decisions based on environmental data and user commands.<br>
5. Environmental Interaction and Decision-making:<br>
    · Implement a module that allows the model to make decisions based on environmental data and user instructions, such as planning a path to avoid obstacles.<br>
    · In the face of specific environmental changes, the model should be able to provide solutions and execute the corresponding actions.<br>
6. Model Evaluation and Optimization:<br>
    · Regularly test and evaluate your model to ensure its performance remains stable in various situations.<br>
    · Optimize based on test results, which may involve adjusting model hyperparameters or training strategies.<br>
7. Safety and Robustness:<br>
    · Ensure the model's safety, especially when dealing with different environmental changes, to prevent potential hazards.<br>
    · Implement robust measures to enable the model to handle uncertainties such as noise and sensor errors.<br>

### Experiments and Simulation:<br>
1. Conduct extensive testing and training in a simulation environment to reduce risks on actual drones.<br>
2. Simulation can simulate various environmental scenarios and help validate the model's performance.<br>

### Task Description:<br>
0. The task can be described as follows in terms of logic:<br>
    1. Consider generating an instruction set that includes macro instructions that are simplified and formalized after understanding the original task, as well as actual PID statements for controlling machine functions.
    2. For example, the original instruction might be "Please circle the area." The macro instruction could be transformed into "Scan the environment, move to the nearest wall in a clockwise direction, maintaining a one-meter safety distance from the wall during the circle." Another critical task is micro-instructions, which involve studying and analyzing macro instructions, ultimately translating them into device control. For example, after generating the macro command in the example above, the model would need to output a series of micro commands that specifically analyze the macro instruction's meaning, similar to converting it into "Activate visual odometry for full-scene scanning, determine the position, calculate the next motion anchor point's location, control the machine to move to the nearest wall position, start circling along the wall while maintaining a one-meter distance, and return to the starting point."
    3. The algorithm utilizes VoxPoser principles for path planning, generating a set of task points in 3D space, evaluating risks, and then generating corresponding machine instructions (PID statements). Once the corresponding instruction set is obtained, the hardware system begins execution.

### Experimental Workflow Design and Discussion
1. Hardware Design and Setup<br>
2. Control Algorithm Design: SLAM algorithm design and optimization (testing latency), 3. language model training (command analysis capability and code generation capability, testing latency), VoxPoser algorithm implementation (3D environmental interaction path planning algorithm), hardware control algorithm (communication interfaces), risk assessment algorithm (decision feasibility assessment).<br>
3. Control Chain Testing<br>
4. Simulation Environment Setup and Testing<br>
5. Simulation Experiments<br>
6. Real-world Testing<br>


