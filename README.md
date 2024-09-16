# Text-to-Image Synthesis with StackGAN

This repository implements a model for synthesizing photo-realistic images from textual descriptions using the **Stacked Generative Adversarial Networks (StackGAN)**.

## Overview

StackGAN is a two-stage generative adversarial network that synthesizes images conditioned on textual descriptions. It uses:
1. **Stage-I GAN**: Generates low-resolution images (64x64).
2. **Stage-II GAN**: Refines and generates high-resolution images (256x256).

**Research Paper**: [StackGAN: Text to Photo-realistic Image Synthesis with Stacked Generative Adversarial Networks](https://arxiv.org/pdf/1612.03242.pdf)

---

## Model Architecture

### Stage-I GAN:
- **Input**: Encoded textual description.
- **Output**: 64x64 low-resolution image.
- **Goal**: Generate basic shapes and colors corresponding to the text.

### Stage-II GAN:
- **Input**: Low-resolution image from Stage-I and encoded text.
- **Output**: 256x256 high-resolution image.
- **Goal**: Refine the image by adding realistic details.

**Architecture Diagram**:
![StackGAN Architecture](https://user-images.githubusercontent.com/31109495/94064358-32e02d00-fe07-11ea-8ae0-a53e443f9509.png)

---

## Key Features

- **Two-Stage GAN**: Progressive image generation, improving quality and stability.
- **Text-to-Image**: Generates images based on text descriptions.
- **Scalability**: Can be adapted for larger images and various datasets.

---

## Installation

To install the necessary packages and set up the environment, follow these steps:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-username/StackGAN.git
    cd StackGAN
    ```

2. **Install required dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Download the dataset**:
    Download the [CUB dataset](https://drive.google.com/open?id=0B3y_msrWZaXLT1BZdVdycDY5TEE) and place it in the `data/` directory.

4. **Run the model**:
    ```bash
    python train.py
    ```

---

## Dataset

This project uses the [CUB dataset](http://www.vision.caltech.edu/visipedia/CUB-200.html) which contains 11,788 images across 200 bird species. The dataset also includes textual descriptions for each image.

### Data Preprocessing

- **Image Resizing**: Images are resized to 256x256.
    ```python
    from PIL import Image
    img = Image.open('image_path').resize((256, 256))
    ```

- **Text Encoding**: Text descriptions are converted into vector representations using embeddings like Word2Vec or GloVe.
    ```python
    from gensim.models import Word2Vec
    model = Word2Vec(sentences, vector_size=100, window=5, min_count=1, workers=4)
    text_vector = model.wv['word']
    ```

---

## Training the Model

1. **Stage-I Training**:
    Train the Stage-I GAN to generate 64x64 images:
    ```bash
    python train_stage_1.py
    ```

2. **Stage-II Training**:
    Use the output of Stage-I to train Stage-II GAN for 256x256 image generation:
    ```bash
    python train_stage_2.py
    ```

Training time may vary based on dataset size and hardware.

### Hyperparameters:

- **Learning rate**:
    ```python
    learning_rate = 0.0002
    ```

- **Batch size**:
    ```python
    batch_size = 64
    ```

---

## Results

After training, the model generates high-resolution images based on unseen text inputs.

### Example Outputs:

- **Input Text**: "A small bird with bright yellow feathers."
- **Stage-I Output**: A 64x64 image with basic shapes and colors.
- **Stage-II Output**: A 256x256 refined image with realistic textures and details.

---

## Usage

Generate new images using the trained model:
```bash
python generate.py --description "Your image description here"
