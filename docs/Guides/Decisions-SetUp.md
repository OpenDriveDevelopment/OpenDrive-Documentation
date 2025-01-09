---
title: Decisions Setup
parent: Guides
nav_order: 4
---

# Decisions Setup
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# **Decisions Module Configuration**

The Decisions module processes data from computer vision models to suggest decisions for the current driving situation. This guide explains how to configure the Decisions module using the **`start_data_reception`** method.

---

### **Step 1: Understand the `start_data_reception` Method**

The `start_data_reception` method defines how data is received from models, processed, and delivered as output.

```python
def start_data_reception(models_to_receive, topic="output_topic_objects1", output_mode="console", function_mode="four_cameras", kafka_topic="processed_data_output"):
```

**Core Parameters**:
- **`models_to_received`**: Specifies the number of unique models expected to provide data.
- **`topic` (optional)**: The Kafka topic from which data is received.
- **`output_mode` (optional)**: Determines how the output data is delivered: `['console', 'document', 'kafka']`.
- **`function_mode` (optional)**: Defines how the data is processed to make suggested decisions: `['four_cameras', 'custom']`.
- **`kafka_topic` (optional)**: The Kafka topic where the output is published if **`kafka`** is selected as **`output_mode`**.

---

### **Step 2: Define start_data_reception method**

Below is an example of how to define the **`start_data_reception`** method:

```py
from OpenDrive.modules.decision_making.pipeline_definition.consumer import start_data_reception

def main():
    start_data_reception(
        models_to_received = 5, 
        topic = "output_topic_objects1", 
        output_mode = "console", 
        function_mode = "four_cameras", 
        kafka_topic = "processed_data_output"
    )
```

* `models_to_received`: Specifies that 5 models are expected to provide data
* `topic`: Indicates that the Kafka topic for receiving data is **`output_topic_objects1`**.
* `output_mode`: Specifies that the output will be printed to the console.
* `function_mode`: Indicates that the processing mode is the standard configuration for four cameras.
* `kafka_topic`:  Although unused in this case, the Kafka topic for publishing the output is set to **`processed_data_output`**.

### **Step 3: You are done**

This is one of the simplest modules to use. Once configured, it will automatically receive and process data as defined—no further steps are required.

## Complete Example

Here is a complete example demonstrating how to use the module:

```py
from OpenDrive.modules.decision_making.pipeline_definition.consumer import start_data_reception

def main():
    # Initialize the data reception
    start_data_reception(
        models_to_received = 5, 
        topic = "output_topic_objects1", 
        output_mode = "console", 
        function_mode = "four_cameras", 
        kafka_topic = "processed_data_output"
    )
    
if __name__ == '__main__':
    main()
```
