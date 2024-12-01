# Binary Segmentation of Liquid in Video
This project focuses on applying binary segmentation techniques to separate liquid from the background in a video. The liquid is analyzed frame by frame using a segmentation algorithm based on color thresholding. The primary objective is to isolate the liquid regions in each frame and create a binary mask that distinguishes the liquid from other elements in the scene.

## Goal
The primary goal of this project is to separate the liquid from the background in the video, enabling further analysis of its properties, such as flow patterns, surface tension, or interaction with other elements.


### Steps Involved:

#### 1. **Input: Liquid Video**
   - The input to the segmentation process is a video containing a liquid. The video is broken down into individual frames for processing.
  
#### 2. **Preprocessing: Frame Extraction**
   - Each frame of the video is extracted and converted into an RGB image. This allows the color-based segmentation to be applied on a per-frame basis.

#### 3. **Segmentation using Color Thresholding**:
   - The function `LiquidMaskv3.m` is used to segment the liquid in each frame. The steps involved in segmentation include:
   
     a) **Color Space Analysis**:
        - The function operates in the RGB color space. Specific threshold values are predefined for each color channel:
          - **Red channel**: Values between 0 and 90.
          - **Green channel**: Values between 0 and 56.
          - **Blue channel**: Values between 0 and 64.
        
     b) **Binary Mask Creation**:
        - A binary mask (`BW`) is created by checking each pixel in the frame. If a pixel’s RGB values fall within the defined thresholds, it is classified as part of the liquid, and the mask value is set to `true` for that pixel. Otherwise, it is classified as background (`false`).
        
     c) **Mask Application**:
        - The binary mask is applied to the original RGB image. Pixels corresponding to the background (where the mask is `false`) are set to zero, effectively blacking out non-liquid regions. The result is an isolated image of the liquid (`maskedRGBImage`), where only the liquid pixels are visible.

#### 4. **Postprocessing**:
   - The segmented liquid mask is applied across all frames, generating a sequence of isolated liquid images. These images can then be analyzed for liquid behavior over time, such as changes in shape, flow patterns, or interaction with external forces.

#### 5. **Output: Segmented Liquid Video**
   - The output of the process is a video where the liquid has been successfully segmented from the background. This binary-segmented video can be used for further analysis or visualization of the liquid's properties.

