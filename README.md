# YOLOv8 Custom Gwanganri Detection

This repository contains a custom implementation of the YOLOv8 object detection model tailored for the Gwanganri area. The primary focus is to detect specific objects relevant to the region using the YOLOv8 architecture.

## Project Structure

- **dataset/**: Contains the dataset used for training and validation.
- **models/**: Holds the architecture and weights for the YOLOv8 model.
- **notebooks/**: Jupyter notebooks that provide detailed analysis and execution steps.
- **scripts/**: Python scripts for training, validation, and inference.

## Getting Started

To get started with this project, follow the steps below:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/youchulJ/YOLOv8_Custom_Gwanganri_Detection.git
   cd YOLOv8_Custom_Gwanganri_Detection
   ```

2. **Install Dependencies:**
   Use the requirements.txt file to install the necessary packages:
   ```bash
   pip install -r requirements.txt
   ```

3. **Prepare the Dataset:**
   Make sure the dataset is properly formatted and placed in the **dataset/** directory.

4. **Model Training:**
   Execute the training script located in the **scripts/** directory:
   ```bash
   python scripts/train.py
   ```

5. **Evaluation:**
   After training, run the evaluation script:
   ```bash
   python scripts/evaluate.py
   ```

6. **Inference:**
   Use the inference script to test the model:
   ```bash
   python scripts/infer.py
   ```

## Notebooks

The **notebooks/** folder contains Jupyter notebooks that explain the analysis process and model evaluation. Use the following order for execution:

1. **Data Exploration Notebook** – Explore and visualize the dataset.
2. **Model Training Notebook** – Document the training process and parameters.
3. **Evaluation Notebook** – Show evaluation metrics and results.
4. **Inference Notebook** – Demonstrate how to run inference on new data.

## Contributing

If you'd like to contribute, please fork the repository and submit a pull request. We appreciate any contributions and feedback!

## License

This project is licensed under the MIT License. See the LICENSE file for more details.