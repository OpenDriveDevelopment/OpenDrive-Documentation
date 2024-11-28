---
title: Perception
parent: Modules
nav_order: 2
---

# Perception
{: .no_toc }

The Perception Module is a critical component of the framework, tasked with interpreting data from the Sensors Module to extract meaningful information about the environment. It combines various models and techniques to analyze the sensor data and generate actionable insights.

#### **Key Functionalities**
The Perception Module offers the following capabilities:

1. **Traffic Sign Detection:**  
   Identifies and classifies traffic signs, such as stop signs, speed limits, and warnings, to ensure the vehicle adheres to road regulations.

2. **Lane Detection:**  
   Determines the position and boundaries of lanes on the road, aiding the vehicle in maintaining the correct trajectory.

3. **Object Detection:**  
   Detects and classifies objects in the vehicle's path, such as pedestrians, other vehicles, and obstacles, ensuring safe navigation.

4. **Free Space Detection:**  
   Identifies drivable areas by evaluating zones free of obstacles, aiding in path planning and maneuvering.

#### **Advanced Processing**
While the current focus is on computer vision models, the Perception Module is designed to accommodate a wide variety of processing methods, including:

- **Deep Learning Models (e.g., CNNs):**  
   These models will process and interpret sensor data (e.g., images from cameras, point clouds from LIDARs) to provide a deeper understanding of the environment.
   
- **Multi-Sensor Fusion:**  
   Planned future updates will include models that combine data from different sensor types (e.g., radar, LIDAR, and cameras) to improve accuracy and reliability in perception.

#### **Integration with the Framework**
The Perception Module acts as a bridge between the **Sensors Module** and the **Decision-Making Module**, enabling the vehicle to:
1. Gather real-time data from sensors.
2. Process the data to identify critical elements in the environment.
3. Provide actionable insights to the Decision-Making Module for further processing.

#### **Future Enhancements**
The framework is designed to evolve with advancements in artificial intelligence and sensor technologies. Future updates will include:
- Incorporation of more advanced deep learning architectures.
- Extended support for multi-modal data interpretation, combining visual, spatial, and contextual information.

#### **Usage Example**
1. Data is received from the Sensors Module (e.g., video feeds, LIDAR point clouds).
2. The Perception Module applies relevant models, such as CNNs or fusion algorithms, to interpret the data.
3. The extracted insights (e.g., detected lanes, objects, and free spaces) are sent to the Decision-Making Module for real-time decision-making.

This modular and extensible design ensures that the Perception Module remains a powerful and adaptable tool for developing self-driving systems.
