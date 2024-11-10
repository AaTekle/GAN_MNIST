# Generative Adversarial Network (GAN) that generates synthetic MNIST images.
![image]([https://github.com/user-attachments/assets/e991057f-a706-4aa4-8355-00af2d0632d7](https://raw.githubusercontent.com/AaTekle/GAN_MNIST/refs/heads/main/generated_images/epoch_40.png?token=GHSAT0AAAAAACVU7BMFJYOITP75Q3ER2FP4ZZQ7FSQ
))

## Key Components

1. **Environment Setup**:
   - Uses GPU if available.
   - Creates a directory to save generated images.

2. **Data Preparation**:
   - Loads the MNIST dataset, applying normalization to prepare for training.

3. **Model Architecture**:
   - **Generator**: Takes random noise as input and produces an image in MNIST format.
   - **Discriminator**: Classifies images as real or fake.

4. **Training Process**:
   - Trains the generator and discriminator in alternating steps:
     - **Generator** aims to fool the discriminator by producing realistic images.
     - **Discriminator** learns to differentiate between real and generated images.
   - Uses Binary Cross-Entropy loss and the Adam optimizer.

5. **Image Generation**:
   - Saves generated images every 10 epochs to visualize progress.

**End of training**: Logs and saved images help evaluate GAN performance.
