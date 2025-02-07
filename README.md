# Generative Adversarial Network (GAN) that generates synthetic MNIST images.
![image](generated_images/epoch_40.png)

## GAN Project Components

1. **Model Architecture**:
   - **Generator**: Takes random noise as input and produces an image in MNIST format.
   - **Discriminator**: Classifies images as real or fake.

2. **Training Process**:
   - Trains the generator and discriminator in alternating steps:
     - **Generator** aims to fool the discriminator by producing realistic images.
     - **Discriminator** learns to differentiate between real and generated images.
   - Uses Binary Cross-Entropy loss and the Adam optimizer.

3. **Image Generation**:
   - Saves generated images every 10 epochs to visualize progress.
   - **End of training**: Logs and saved images help evaluate GAN performance.

## Core Math Behind GANs (Simplified)

### 1. **What’s the Goal of a GAN?**
- A GAN has two parts: a **Generator** and a **Discriminator**.
- **Generator**: Creates fake data (e.g., images).
- **Discriminator**: Judges whether the data is real or fake.
- **Goal**: The generator wants to fool the discriminator, and the discriminator wants to tell the difference.

This is like a forger (Generator) trying to make fake paintings and an art critic (Discriminator) deciding whether a painting is real or fake.

### 2. **The Key Math Behind GANs**

#### A. **Probability**
- The discriminator outputs a **probability**: how likely the input is **real**.
  - If it's real, the output is close to 1.
  - If it's fake, the output is close to 0.

#### B. **Loss Function (How GANs Learn)**
- GANs optimize a function that measures how well the generator and discriminator are doing. The two loss functions are:

1. **Discriminator’s Loss**:
   - It tries to maximize how well it classifies:
     - **Real data as real**.
     - **Fake data as fake**.
   - Mathematically:
     ```math
     L_D = -E[\log(D(x))] - E[\log(1 - D(G(z)))]
     ```
     - `D(x)`: Probability the discriminator assigns to real data.
     - `D(G(z))`: Probability it assigns to fake data.

2. **Generator’s Loss**:
   - The generator tries to **fool the discriminator**, meaning it wants `D(G(z))` to be close to 1 (fake data being classified as real).
   - Mathematically:
     ```math
     L_G = -E[\log(D(G(z)))]
     ```

#### C. **Gradient Descent**
- Both the generator and discriminator use **gradient descent** to update their weights. This means:
  - They compute how much the loss changes when their weights change slightly.
  - They adjust the weights to minimize (for the generator) or maximize (for the discriminator) their loss.

### 3. **How They Compete**
- GAN training is like a **game**:
  - The generator improves until it can create data that looks so real, the discriminator gets tricked.
  - The discriminator improves to better spot fake data.
- Mathematically, this is a **min-max optimization problem**:
  ```math
  \min_G \max_D V(D, G) = E[\log(D(x))] + E[\log(1 - D(G(z)))]
  ```

### 4. **Noise and Latent Space**
- The generator starts with **random noise** as input (a bunch of numbers, usually from a normal distribution).
- This noise is transformed step by step into something meaningful (e.g., an image).
- The **latent space** is this space of random inputs that the generator learns to map to realistic outputs.

### 5. **Training GANs is Hard**
- The generator and discriminator must stay balanced:
  - If the discriminator is too strong, the generator can’t learn.
  - If the generator is too strong, the discriminator becomes useless.
- This is called the **vanishing gradient problem**, which makes GAN training tricky.

### 6. **Summary of Steps**
1. Feed real data and fake data to the discriminator.
2. Calculate the discriminator's loss.
3. Update the discriminator’s weights.
4. Feed noise into the generator to create fake data.
5. Calculate the generator's loss based on how well it fools the discriminator.
6. Update the generator's weights.
7. Repeat until the generator creates realistic data.
