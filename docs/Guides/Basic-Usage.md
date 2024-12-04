---
title: Basic Usage
parent: Guides
nav_order: 1
---

# Basic Usage
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Basic usage example

## Step 1: Start Kafka Broker
Before you begin, make sure that the Kafka Broker is up and running. To do this, navigate to the folder containing the `docker-compose.yml` file and run the following command in your terminal:

```bash
docker-compose up -d
```

## Step 2: Sensors definition

The first point of access to the framework is the initialization of the sensors. In this step, we will define and initialize the sensors, which will be responsible for collecting data.

### 1. Importing the Required Classes and Functions

The first thing we need to do is import the necessary classes. In this case, we are working with a camera sensor. The `Camera` class, which represents a camera sensor. 

```py
from OpenDrive.modules.sensors_prep.sensors.camera import Camera
```
Next, we import the function `start_sensors_streaming`, which will allow us to begin the sensor data streaming process.

```py
from OpenDrive.modules.sensors_prep.pipeline_definition.sensors_stream_control import start_sensors_streaming
```

### 2. Structuring the Code with the Main Function

It is recommended that the code always be executed using the standard entry point structure with the convention if \_\_name__ == "\_\_main__":. This ensures that the script will only run when it is executed directly and not when imported as a module.

### 3. Defining the Sensors

Once we have imported the necessary classes and functions, we can define the sensors. In this case, we define two camera sensors: cam1 and cam2. Both sensors are initialized with two parameters: port and sensing_speed. The port indicates the sensor's identifier, and the sensing_speed controls how fast the sensor collects data.
```py
def main():
    cam1 = Camera(port = 1, sensing_speed = .3)
    cam1.enable_sensor()

    cam2 = Camera(port = 2, sensing_speed = .3)
    cam2.enable_sensor()
```

### 4. Starting the Sensors' Data Streaming

After defining the sensors, we pass them as a list to the start_sensors_streaming function. In addition to passing the list of sensors, we also define the loglevel parameter. The loglevel can take values between 0 and 1, and it controls the level of log information displayed.
- loglevel=0 will show minimal logs.
- loglevel=1 will display detailed logs.

```py
start_sensors_streaming(
        sensors = [cam2, cam1],
        loglevel= 1  # Set the log level to 1 for detailed logs
    )
```

### 5. Full Code Example

Here’s the complete code for this step:
```py
from OpenDrive.modules.sensors_prep.sensors.camera import Camera
from OpenDrive.modules.sensors_prep.pipeline_definition.sensors_stream_control import start_sensors_streaming

def main():
    # Define and enable the first camera sensor
    cam1 = Camera(port = 1, sensing_speed = .3)
    cam1.enable_sensor()

    # Define and enable the second camera sensor
    cam2 = Camera(port = 2, sensing_speed = .3)
    cam2.enable_sensor()
    
    # Start streaming data from the sensors
    start_sensors_streaming(
        sensors = [cam2, cam1],
        loglevel= 1  # Detailed logging
    )
    
if __name__ == "__main__":
    main()

```

## Step 3: Perception definition

Once the sensors have been defined, the next step is the definition of the perception module. This module will process the data received from the sensors and apply vision models for analysis.

### 1. Importing Required Classes and Functions
For the perception module, we need to import the following:

**`SensorToModelPipeline`**: This class will be used to define the role of each of the previously defined sensors. 

```py
from OpenDrive.modules.sensors_prep.pipeline_definition.sensor_to_model_pipeline import SensorToModelPipeline
```

**`control_perception_streaming`**: This function will be used to start the execution of the perception process by controlling the streaming of data through the defined pipelines.

```py
from OpenDrive.modules.sensors_prep.pipeline_definition.perception_control import control_perception_streaming
```

### 2. Defining the Perception Pipelines

Next, you need to define the perception pipelines in an array. These pipelines will determine the role and functionality of each sensor.

```py
def main():
    pipelines = [
    SensorToModelPipeline(
        input_sensor="sensor_camera_1", 
        sensor_type = "Camera",
        sensor_position = "Front",
        output_decision="output_topic_objects1"
        ),
    SensorToModelPipeline(
        input_sensor="sensor_camera_2",
        sensor_type = "Camera",
        sensor_position = "Custom",
        perceptions = ["signals", "objects"],
        output_decision="output_topic_objects1"
        ),
    ]
```

Here’s a breakdown of the parameters for the SensorToModelPipeline class:

- `input_sensor:` This is the name that identifies the Kafka topic containing the sensor data.
    - Allowed values: String that contains the sensor kafka topic name
- `sensor_type:` Specifies the type of sensor being used
    - Allowed values: "Camera", "Custom"
- `sensor_position:` Specifies the position of the sensor on the vehicle.
    - Allowed values: "Front", "Rear", "LeftSide", "RightSide", "Custom"
- `output_decision:` This is the name that identifies the Kafka topic where the detection results will be sent.
    - Allowed values: String that contains the kafka  output topic name

**Note:** If the sensor_position is set to "Custom", the user will need to define an additional attribute called perceptions. 
- `perceptions:` This attribute refers to the computer vision models that will analyze the sensor data. It accepts an array of strings with the following possible values:

    - Allowed values: "lane", "signals", "objects"

### 3. Starting perceptions process

The **`control_perception_streaming`** function is responsible for starting and controlling the streaming of data through the defined perception pipelines. 

```py
 control_perception_streaming(
        pipelines = pipelines,
        loglevel= 0
    )
```

Here's a breakdown of its parameters:

- `pipelines:` This parameter receives an array of perception pipelines that define how the data from the sensors should be processed. Each pipeline specifies the sensor, the type of perception task (e.g., lane detection, object detection), and where to send the results. In this case, the pipelines variable holds the list of all the pipelines you've defined earlier in the code.

- `loglevel`: This parameter controls the verbosity of the logs during the execution of the perception process. It can take values between 0 and 1:

    - loglevel=0: Minimal logging is displayed (it only indicates if the pipelines are running).
    - loglevel=1: Medium logging (it displays information every time a vision model process something).
    - loglevel=2: Detailed logging (it displays information regarding the vision models process and the kafka data stream).

By calling control_perception_streaming the function will start processing the sensor data according to the defined pipelines and will send the produced information to the decision making module.

### 4. Full Code Example

Here’s the complete code for this step:

```py
from OpenDrive.modules.perception.pipeline_definition.percep_pipeline import SensorToModelPipeline
from OpenDrive.modules.perception.pipeline_definition.perceptions_stream_control import control_perception_streaming

def main():
    pipelines = [
    SensorToModelPipeline(
        input_sensor="sensor_camera_1", 
        sensor_type = "Camera",
        sensor_position = "Front",
        output_decision="output_topic_objects1"
        ),
    SensorToModelPipeline(
        input_sensor="sensor_camera_2",
        sensor_type = "Camera",
        sensor_position = "Front",
        output_decision="output_topic_objects1"
        ),
    ]

    control_perception_streaming(
        pipelines = pipelines,
        loglevel= 1
    )

if __name__ == "__main__":
    main()
```

## Step 4: Decision making definition

In progress ...
