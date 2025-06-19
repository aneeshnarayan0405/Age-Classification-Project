# YonderWonder Internship Assessment: Q&A Responses

## Write-Up
Initially, I explored a classification model to assign age groups in decades (e.g., 20s, 30s). However, with a limited dataset and very few samples in some classes, the model failed to generalize. I realized that predicting actual age values as a regression task was more appropriate. I redesigned the model using a pretrained ResNet18 and achieved significantly better results. The hardest part was balancing the dataset and ensuring enough validation examples, which I addressed using stratified splitting.

---

## Assessment Questions & Answers

### a. What model architecture did you choose and why?
- I used **ResNet18** pretrained on ImageNet.
- It provides a strong feature extractor and is computationally efficient.
- I replaced the final layer with a small regression head to predict a single age value.
- Chosen due to its proven performance on small datasets via transfer learning.

### b. What was its classification accuracy?
- The task was treated as **regression** (predicting continuous age).
- Instead of accuracy, I reported:
  - **MAE** (Mean Absolute Error): *36.03 years*
  - **RMSE** (Root Mean Squared Error): *37.18 years*
- I also binned the predicted/true ages into decades and produced a **confusion matrix** to visualize performance.

### c. What worked well and what didn’t?
**Worked well:**
- Transfer learning with ResNet18
- Regression instead of classification
- Data augmentation and stratified split
- Visualizations and metric reporting

**Did not work well:**
- Class-based prediction (classification)
- Using CNNs from scratch (overfitting)
- Imbalanced data leading to biased predictions

### d. How can you improve upon the results you got?
- Increase training epochs and add early stopping
- Use more diverse or balanced datasets
- Apply stronger augmentation (CutMix, MixUp)
- Try ensemble models or ResNet50/EfficientNet
- Use Huber loss or MAE instead of MSE

### e. If you now want to use the dataset above to train a model to make a person older or younger, what would you change?
- Reframe it as **image-to-image translation**
- Use GANs like **StarGAN** or **Age-cGAN**
- Train model to take input image + target age and output modified face
- Add identity loss to preserve facial structure
- Use aligned and age-labeled datasets (like UTKFace or CACD)

---

## Bonus: Feedback on YonderWonder App
I explored https://app.yonderwonder.ai and found the digital aging effect impressive and intuitive.

**Suggestions:**
- Add an age slider (e.g., +/- years)
- Display before/after side-by-side
- Support profile and side-angle faces
- Allow batch processing of images
- Offer download with age overlay

The core idea is great and exciting for creative or medical applications!
