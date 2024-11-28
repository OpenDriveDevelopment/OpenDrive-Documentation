---
title: Decisions
parent: Modules
nav_order: 3
---

# Decisions
{: .no_toc }

### **Decision-Making Module**

The Decision-Making Module is the final stage in the framework's processing pipeline. It leverages the insights provided by the Perception Module to evaluate the driving environment and generate actionable decisions. This module is essential for translating sensor data and perception insights into specific recommendations or alerts for safe vehicle operation.

#### **Key Functionalities**
1. **Classification and Alerts:**  
   - Processes the information received from the Perception Module to classify scenarios and emit alerts.  
   - Key alerts include:  
     - **Lane Change Alerts:** Recommendations on whether it is safe to change lanes.  
     - **Object Detection Alerts:** Warnings about objects in the vehicle's path.  
     - **Free Space Alerts:** Notifications about drivable areas around the vehicle.  
     - **Traffic Sign Alerts:** Instructions derived from traffic signs, such as stopping or adjusting speed.

2. **Action Recommendations:**  
   - Determines basic driving actions, such as:  
     - **Brake:** Alerts when it is necessary to slow down or stop.  
     - **Advance:** Signals when it is safe to move forward.  
     - **Lane Change:** Indicates when it is possible to change lanes.

3. **Structured Metadata Output:**  
   - Instead of providing multimedia outputs like images or videos, the module generates textual metadata.  
   - This metadata is structured, clear, and concise, offering critical details about the driving environment for further use.  

#### **Output Example**
The module produces results in textual format, such as:

```json
{
    "lane_change_safe": true,
    "object_in_path": "Pedestrian",
    "free_space": "Left and Forward",
    "traffic_sign_detected": "Stop Sign",
    "recommended_action": "Brake"
}
```
