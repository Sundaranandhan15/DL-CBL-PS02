# DL-CBL-PS02
PS-02: Rice Leaf Disease Identification Using Deep Learning
Project Overview
Rice is a major food crop, and leaf diseases can reduce crop health and yield if they are not identified early. This project develops an image-classification model that predicts the disease category from a rice leaf image.

The project uses transfer learning with MobileNetV2, a convolutional neural network (CNN) pretrained on ImageNet, and adapts it to classify rice leaf images into four disease categories.
Problem Statement
Develop a deep learning model that identifies rice leaf diseases from images to support early disease recognition. Since some diseases may have visually similar symptoms, the notebook evaluates the model using class-wise precision, recall, F1-score, a confusion matrix, and overall test accuracy.
Disease Classes
The notebook uses these four classes:
- Bacterialblight
- Blast
- Brownspot
- Tungro
Methodology
1. Dataset preparation – Extract the dataset archive and organize images into class-specific folders.
2. Dataset inspection – Check class folders and image counts; visualize the class distribution and representative samples.
3. Train/validation/test split – Split the data using stratification to preserve class proportions.
4. Image preprocessing – Resize images to 224 × 224 pixels and prepare batches using TensorFlow data pipelines.
5. Data augmentation – Apply random horizontal flips, rotations, zoom, and contrast adjustments to training images.
6. Transfer learning – Use ImageNet-pretrained MobileNetV2 as a frozen feature extractor.
7. Classification head – Apply global average pooling, dropout, and a softmax output layer for the four classes.
8. Model training – Train with the Adam optimizer and sparse categorical cross-entropy. Use model checkpointing, early stopping, and learning-rate reduction callbacks.
9. Evaluation – Evaluate the best saved model on the test set and generate classification metrics and a confusion matrix.
10. Prediction – Run inference on an individual rice leaf image and display the predicted class and confidence score.
Model Architecture
- Base model: MobileNetV2 (include_top=False, ImageNet weights)
- Input size: 224 × 224 × 3
- Augmentation: RandomFlip, RandomRotation, RandomZoom, RandomContrast
- Pooling: GlobalAveragePooling2D
- Regularization: Dropout (0.30)
- Output layer: Dense layer with 4 units and softmax activation
- Optimizer: Adam (learning_rate=0.001)
- Loss function: Sparse categorical cross-entropy
- Training limit: Up to 10 epochs, with callbacks to help control overfitting and learning rate
Technologies Used
- Python
- TensorFlow / Keras
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Pillow (PIL)
- Scikit-learn
- Jupyter Notebook / Google Colab
Repository Contents
File	Description
RA2311026050228_PS02.ipynb	Notebook containing dataset preparation, model training, evaluation, and prediction


The dataset and trained model are not necessarily included in this repository. Check the notebook's dataset paths and provide the dataset separately before running it.
How to Run
Option 1: Google Colab
1. Upload RA2311026050228_PS02.ipynb to Google Colab.
2. Upload or mount the rice leaf disease dataset archive expected by the notebook.
3. Check the archive and extracted-folder paths in the notebook. Update them if your file structure differs.
4. Run the notebook cells in order, from imports and data extraction through training, evaluation, and prediction.
5. Review the test metrics and generated plots.
Option 2: Run Locally
1. Install Python and Jupyter Notebook, then install the required packages:
   pip install tensorflow numpy pandas matplotlib seaborn scikit-learn pillow py7zr
2. Download or place the dataset in the expected folder structure.
3. Update any Google Colab-specific paths such as /content/... to match your local directories.
4. Open the notebook and run the cells in order.
Note: Training performance and runtime depend on the dataset, hardware, TensorFlow version, and configuration. A GPU is recommended for faster training.
Evaluation
The notebook calculates and visualizes:
- Test loss and test accuracy
- Per-class precision, recall, and F1-score
- Macro-F1 and weighted-F1 scores
- Confusion matrix
- Training and validation accuracy/loss curves
- Predicted class and confidence for an individual image
Results: Add the final test accuracy and class-wise recall after running the notebook. Results are intentionally not stated here because they should be taken from the actual notebook execution.
Output Artifacts
The notebook saves the following artifacts in the rice_disease_results directory:
- rice_leaf_disease_mobilenetv2.keras — trained model
- classification_report.csv — classification metrics
- confusion_matrix.csv — confusion matrix values
- class_mapping.json — mapping between class names and numeric labels
Limitations
- Predictions depend on the quality, variety, and representativeness of the training dataset.
- Performance on controlled dataset images may differ from performance on real field images.
- The model's prediction should be treated as a decision-support result, not a substitute for expert agricultural diagnosis.
- The model should be tested on diverse field conditions before practical deployment.
Future Improvements
- Evaluate on rice leaf images captured under different lighting and field conditions.
- Add more samples and investigate class imbalance.
- Fine-tune selected MobileNetV2 layers and compare performance with other CNN architectures.
- Test robustness against blur, background variation, and image-quality changes.
- Build a simple web or mobile interface for image upload and prediction.
Author
Name: Sundaranandhan R J
Register Number: RA2311026050228
Problem Statement: PS-02 — Rice Leaf Disease Identification
Academic project notebook for rice leaf disease classification using deep learning and transfer learning.
