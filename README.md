Dogs vs. Cats Classification - Model Report
----------------------------------------------------------------------------------------------------------
1. Model Architecture
The model is based on MobileNetV2, a lightweight CNN designed for efficient image classification.

Model Layers & Design:
- Base Model: MobileNetV2 (pretrained on ImageNet, frozen during training)
- Custom Layers Added:
  - 3 Convolutional Layers (ReLU activation)
  - Global Average Pooling Layer (Reduces dimensionality)
  - Dense Layer (128 units, ReLU)
  - Dropout (50%) (Prevents overfitting)
  - Output Layer (Sigmoid activation) for binary classification (cat/dog)

Model Summary:
Input Shape: (160, 160, 3)  
Base Model: MobileNetV2 (Pretrained on ImageNet)  
Custom Layers: Conv2D(32, 64, 128)  → Dense(128) → Dropout(50%) → Sigmoid  
Loss Function: Binary Crossentropy  
Optimizer: Adam  
-------------------------------------------------------------------------------------------------------------------------------------
2. Preprocessing Steps
The dataset consists of 8,000 training images (4,000 cats + 4,000 dogs) and 2,000 test images (1,000 cats + 1,000 dogs).

Steps Used for Preprocessing:
- Image Rescaling: Normalized pixel values to range [0,1] (rescale=1/255)
- Data Augmentation (Training Only):
  - Rotation (20°), Zoom (20%), Width & Height Shift (20%)
  - Horizontal Flip (to improve model generalization)
- Resized Images to 160x160 Pixels (to reduce computation time)
- Binary Labels Assigned (0 = Cat, 1 = Dog)
-----------------------------------------------------------------------------------------------------------------------------
3. Model Performance
- Training Accuracy: 96.86%
- Validation Accuracy: 94.22%
- Final Test Loss: 0.1411
