# ABC_Challenge_2025_Parkinson_HCMUT_chillguy
Running Order and File Explanations
1) Query_Acc_train
Purpose: Processes the raw accelerometer data by matching its timestamps with the activity timestamps from the TrainActivities file.
Output: Generates CSV files (one per matched timestamp) that contain rows of accelerometer data for each activity.
Note: The input directory is already set at the start of this notebook—ensure it points to your raw data before running.

2) Labeling_for_Query_Acc_Train
Purpose: Takes the CSV outputs from Query_Acc_train and adds the appropriate labels for each activity.
Output: A refined, labeled dataset ready for model training.

3) Segment Train
Purpose: Trains a segmentation model using the labeled data to split the continuous accelerometer data into meaningful segments corresponding to different activity periods.
Output: A segmentation model and segmented data that can be used for classification.

4) XGBoost
Purpose: Implements an XGBoost classifier using the segmented and labeled data.
Output: A trained XGBoost model with classification metrics (notably, it achieves the highest F1 score among the tested models).
Key Point: Although there are multiple classifiers, XGBoost is the primary model due to its superior performance.

5) MLP / RF / Semisupervised_SelfTraining(RF)_04018
Purpose: These notebooks implement alternative classification models:
MLP: Uses a Multi-Layer Perceptron.
RF: Uses a Random Forest classifier.
Semisupervised_SelfTraining(RF)_04018: Applies a semi-supervised self-training approach with Random Forest.
Output: Each notebook outputs classification results for comparison.
Note: Use these for performance comparison, but XGBoost remains the main model based on its F1 score.

6) Segment_Test

Purpose: Tests the segmentation model on Queried Timestamps data from Test
Output: Evaluation metrics and visualizations that help validate the performance of the segmentation model.

7) Label_for_Test
Purpose: Labels the test data using the outputs from the segmentation and classification models.
Output: A fully labeled test dataset for final evaluation or further processing.
Summary
Initial Setup: Ensure the input directory is correctly set at the start of Query_Acc_train.
Pipeline Flow:
Query_Acc_train → 2. Labeling_for_Query_Acc_Train → 3. Segment Train → 4. XGBoost → 5. (MLP / RF / Semisupervised) → 6. Segment_Test → 7. Label_for_Test
Classification Models: While several classifiers (XGBoost, MLP, RF, and Semi-supervised RF) are used, XGBoost is the key model due to its highest F1 score.
