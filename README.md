# Vehicle Counting and Tracking System

This project implements a vehicle counting and tracking system using YOLOv5 for object detection and a simple tracking algorithm. The system counts and tracks vehicles in a given video feed and provides the count of vehicles in predefined regions.

## Prerequisites

- Python 3.x
- OpenCV (`pip install opencv-python`)
- PyTorch (`pip install torch`)
- YOLOv5 (`pip install yolov5` or `torch.hub.load('ultralytics/yolov5', 'yolov5s', pretrained=True)`)

## Implementation Details

- **YOLOv5 Object Detection**: The script initializes YOLOv5 for vehicle detection. YOLOv5 is a state-of-the-art real-time object detection system that provides accurate and efficient vehicle detection.

- **Regions of Interest (ROI)**: Two regions of interest (ROI) are defined in the video feed: a green region and a red region. These regions are predefined and used for counting vehicles separately based on their presence within each ROI.

- **Vehicle Counting**: Vehicles detected within each ROI are counted separately. The script keeps track of the count of vehicles within the green and red regions, providing real-time updates.

- **Vehicle Tracking**: Vehicle tracking is implemented using a simple centroid tracking algorithm. The algorithm tracks vehicles across frames by associating detected vehicle centroids with existing tracked vehicles based on proximity.

- **Unique IDs**: Detected vehicles are assigned unique IDs for tracking. These IDs are used to maintain the identity of vehicles across frames and enable accurate counting and tracking.

- **Customization**: Users can adjust the coordinates of the predefined regions of interest (`area1` and `area2`) according to specific requirements. Additionally, the tracking algorithm can be further optimized or replaced with more advanced techniques for better performance based on the project's needs.

## Code Structure

The main script (`vehicle_counter.ipynb`) follows the following structure:

1. **Imports**: Import necessary libraries including OpenCV (`cv2`), PyTorch (`torch`), and the tracking module (`tracker`).

2. **Global Variables**: Define global variables such as `count` and `count2` for storing the ID of a person, and initialize the YOLOv5 model.

3. **ROI Definition**: Define the regions of interest (`area1` and `area2`) where vehicle counting and tracking will be performed.

4. **Main Loop**: Enter the main loop for processing the video feed frame by frame.

    a. **Read Frame**: Read a frame from the video feed.
    
    b. **Preprocessing**: Resize the frame to a specified size and draw the predefined regions of interest (ROIs) on the frame.
    
    c. **Object Detection**: Use the YOLOv5 model to detect vehicles in the frame and extract their bounding box coordinates.
    
    d. **Tracking**: Update the tracker with the detected vehicle bounding boxes to track vehicles across frames and assign unique IDs.
    
    e. **Counting**: Count the number of vehicles within each ROI and update the count accordingly.
    
    f. **Visualization**: Draw bounding boxes, IDs, and count information on the frame for visualization.
    
    g. **Display**: Display the processed frame with vehicle detection, tracking, and counting.
    
    h. **Exit Condition**: Check for the key press 'Esc' to exit the loop and terminate the program.

5. **Cleanup**: Release the video capture object and close all OpenCV windows.


