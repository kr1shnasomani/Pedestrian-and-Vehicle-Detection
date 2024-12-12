# Pedestrian & Vehicle Detection
The system leverages DeepLabv3 ResNet-50 to detect and segment pedestrians and vehicles, with color-coded masks for easy visualization. This solution is designed for applications in traffic monitoring, pedestrian safety and smart city solutions. Built using PyTorch, Semantic Segmentation and Computer Vision techniques.

## Execution Guide:

## Overview:
The given code snippets implement image segmentation for detecting pedestrians and vehicles in an image using a **DeepLabv3 model** with a ResNet-50 backbone, pretrained on the COCO dataset. The scripts are divided into three distinct files based on their functionality:

**1. `both.py`**
This script performs **semantic segmentation** on the input image and visualizes all detected classes using a color-coded segmentation mask.

**Key Features:**
- **Model Used:** `DeepLabv3 ResNet-50`.
- **Input Image Preprocessing:**
  - Converts the image to RGB format.
  - Normalizes it using ImageNet mean and standard deviation values.
- **Segmentation Output:**
  - Generates a mask where each pixel is assigned a class ID.
  - Applies a color palette to visualize the segmentation classes.
- **Output:** Saves a segmentation image (`both-resultant-image.png`) where all classes are color-coded.

**2. `pedestrian.py`**
This script focuses on **extracting only pedestrians** (COCO class ID 15, corresponding to "person") from the input image.

**Key Features:**
- **Mask Extraction:** Extracts the mask where class ID = 15 (pedestrian).
- **Output Image:** Creates a binary mask, highlighting pedestrian areas in red (`[255, 0, 0]` in RGB).
- **Output:** Saves the segmented pedestrian image (`pedestrian-resultant-image.png`).

**3. `vehicle.py`**
This script segments **vehicles** (COCO class IDs 2 and 7, corresponding to "car" and "truck").

**Key Features:**
- **Vehicle Mask Creation:** Combines masks for "car" (class ID 2) and "truck" (class ID 7).
- **Output Image:** Creates a binary mask with detected vehicles highlighted in blue (`[0, 0, 255]` in RGB).
- **Output:** Saves the segmented vehicle image (`vehicle-resultant-image.png`).

### **Common Components Across Scripts:**
1. **Model Loading:**
   - All scripts use `torch.hub` to load a pretrained `DeepLabv3` model.
   - The model operates in evaluation mode (`model.eval()`).
2. **Preprocessing Pipeline:**
   - Converts input images to tensors.
   - Normalizes them to match the pretrained model's requirements.
3. **Inference:**
   - Performs a forward pass with the model and extracts segmentation outputs (`output['out'][0]`).
   - Uses the `argmax` function to determine the class ID for each pixel.
4. **Output Path:** The segmented images are saved in a specified output directory.

### **Use Cases and Functionality:**
- **`both.py`**: For general-purpose segmentation and visualization of all classes in an image.
- **`pedestrian.py`**: For applications focusing solely on pedestrian detection (e.g., crowd analysis, pedestrian safety systems).
- **`vehicle.py`**: For applications requiring vehicle detection (e.g., traffic monitoring, autonomous vehicle systems).

These scripts demonstrate a modular approach, where specific objects of interest (pedestrians, vehicles) can be segmented independently or collectively, depending on the application.