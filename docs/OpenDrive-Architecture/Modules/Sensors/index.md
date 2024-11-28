---
title: Sensors
parent: Modules
nav_order: 1
---

# Sensors
{: .no_toc }

### **Sensors Module**

The Sensors Module is a foundational component of the framework, designed to abstract the functionality of different types of sensors that a self-driving system might use, such as cameras, LIDARs, radars, and proximity sensors.

#### **Key Features**
- **Abstraction Layer:** The `Sensor` class provides a common interface for all sensors through the use of an abstract base class (ABC). This ensures consistency and ease of integration for different sensor types.
- **Extensibility:** While the current implementation focuses on camera sensors, the design allows developers to extend the module to integrate other sensor types in the future.

#### **Core Functionalities**
1. **Lifecycle Management:**  
   - Each sensor has a unique ID (`sensor_id`) generated using `uuid.uuid4()`.  
   - A state property (`state`) tracks the sensor's status, starting with "Created."

2. **Abstract Methods:**  
   - `start_sensing()`: Defines the logic for initiating data collection by the sensor.  
   - `stop_sensing()`: Specifies how to halt data collection.  
   These methods must be implemented by any concrete sensor class derived from `Sensor`.

3. **Streaming and Control:**  
   - `start_data_streaming()` and `stop_data_streaming()`: Manage the transmission of sensor data.  
   - `enable_sensor()` and `disable_sensor()`: Enable or disable the sensor programmatically.

#### **Future Vision**
While cameras are the primary focus now, the module's abstract and modular design encourages future contributions to support other sensor types. This approach ensures that the framework remains adaptable as new sensor technologies emerge.

#### **Usage Example**
Developers can create a new sensor class by inheriting from `Sensor` and implementing the required abstract methods. For instance, a camera sensor might look like this:

```python
class CameraSensor(Sensor):
    def start_sensing(self):
        print("Camera sensing started.")

    def stop_sensing(self):
        print("Camera sensing stopped.")

