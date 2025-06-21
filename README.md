![Output](assets/output.jpg)
# Virtual T-Shirt Try-On
This repository provides a framework for a virtual try-on system, specifically focusing on T-shirts. It leverages computer vision and deep learning techniques, including models like SegFormer for image segmentation, to process apparel and enable virtual fitting experiences.

## Features

* T-shirt Processing: Utilizes advanced image segmentation to isolate and prepare T-shirt images for virtual try-on.

* Virtual Try-On: Integrates processed T-shirt images onto human models to visualize how the apparel would look.

* Image Segmentation: Employs models, likely SegFormer, for accurate object (T-shirt and potentially human) recognition and masking.

## Folder Structure

The repository is organized as follows:

.
├── Tryon Human Models/
├── tshirts/
│   └── 1.jpg
├── T-shirt processing.ipynb
├── Virtual TryOn.ipynb
├── final_processed_tshirt.jpg
├── tshirt_cropped.jpg
└── yolov8n-seg.pt  # This file might be present but not actively used for segmentation based on current understanding.

* Tryon Human Models/: This directory is expected to contain images of human models on which the T-shirts will be virtually tried on.

* tshirts/: This directory holds the raw T-shirt images (e.g., 1.jpg) that will be processed.

* T-shirt processing.ipynb: A Jupyter notebook dedicated to the processing of T-shirt images, likely involving segmentation and background removal.

* Virtual TryOn.ipynb: A Jupyter notebook that handles the core virtual try-on logic, integrating the processed T-shirts onto human models, and appears to use transformers for segmentation (e.g., SegFormer).

* final_processed_tshirt.jpg: An example of a processed T-shirt image, ready for try-on.

* tshirt_cropped.jpg: An intermediate output, likely a T-shirt with its outer portion filled with median color after initial processing.

* yolov8n-seg.pt: A pre-trained YOLOv8 segmentation model file. As per your instruction, this model will be ignored in the context of the project's primary segmentation workflow.

## Setup and Installation

To set up this project, follow these steps:

1. Clone the repository:
   git clone <repository_url>
   cd <repository_name>

2. Create a virtual environment (recommended): <br>
   `python -m venv venv` <br>
   `source venv/bin/activate` <br>
    On Windows, use `venv\Scripts\activate`

3. Install dependencies:
   `pip install -r requirements.txt`

## Usage

1. Prepare your data:

   * Place human model images in the Tryon Human Models/ directory.

   * Place T-shirt images (preferably on a clean background) in the tshirts/ directory.

2. Run the T-shirt processing.ipynb notebook:
   This notebook will handle the segmentation and preparation of your T-shirt images. Follow the instructions within the notebook.
   
   **Flow of T-shirt Processing:**
   * **Load Image:** The notebook starts by loading the T-shirt image from the `tshirts/` directory.
   * **Segmentation:** A pre-trained image segmentation model (e.g., SegFormer) is used to detect and create a mask for the T-shirt, separating it from the background.
   * **Background Removal:** The background is removed based on the generated mask, resulting in a T-shirt image with a transparent background.
   * **Fill Outer Portion with Median Color:** The outer portion of the T-shirt might be filled with its median color after initial processing, potentially generating `tshirt_cropped.jpg`.
   * **Save Processed Image:** The final processed T-shirt image, ready for virtual try-on, is saved (e.g., as `final_processed_tshirt.jpg`).

3. Run the Virtual TryOn.ipynb notebook:
   After processing the T-shirts, open this notebook to perform the virtual try-on. The notebook will guide you through selecting human models and T-shirts and visualizing the results.

   **Flow of Virtual Try-On:**
   * **Load Human Model and Processed T-shirt:** The notebook loads a human model image from `Tryon Human Models/` and a processed T-shirt image (e.g., `final_processed_tshirt.jpg`).
   * **Upper Cloth Segmentation:** Segment the upper cloth of from the image. 
   * **T-shirt Alignment and Resizing:** The processed T-shirt image is resized and aligned to fit realistically onto the human model's body. This may involve geometric transformations.
   * **Superimposition:** The T-shirt image is superimposed onto the human model image, taking into account the segmentation masks to ensure a natural overlay.
   * **Result Visualization:** The final image with the virtually tried-on T-shirt is displayed.

## Expected Output

The Virtual TryOn.ipynb notebook is expected to output images or visualizations of T-shirts superimposed realistically onto human models, providing a virtual try-on experience. The T-shirt processing.ipynb will output processed T-shirt images suitable for this purpose.

