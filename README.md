# Text-to-Image
A model for synthesizing photo-realistic images given their textual descriptions.  
Related research paper: [StackGAN: Text to Photo-realistic Image Synthesis with Stacked Generative Adversarial Networks](https://arxiv.org/pdf/1612.03242.pdf)

## Model Architecture
Stacked Generative Adversarial Network (StackGAN) is an architecture that aims at generating 256x256 photo-realistic images conditioned on their textual description.  
The complete architecture is composed of 2 GAN models:

### Stage-I GAN
Given the encoded representation of the textual description of the image we want to generate, the Stage-I GAN generates a 64x64 primitive, low-resolution image.

### Stage-II GAN
The Stage-II GAN uses the output of the Stage-I GAN and the textual description as the input to generate a 256x256 dimensional image with photo-realistic details.

![StackGAN Architecture](https://user-images.githubusercontent.com/31109495/94064358-32e02d00-fe07-11ea-8ae0-a53e443f9509.png)

## Dataset
The dataset used is the [CUB dataset](https://drive.google.com/open?id=0B3y_msrWZaXLT1BZdVdycDY5TEE), which contains 200 bird species with 11,788 images.

## References
- [https://arxiv.org/pdf/1612.03242.pdf](https://arxiv.org/pdf/1612.03242.pdf)
- [https://learning.oreilly.com/library/view/generative-adversarial-networks/9781789136678/fe014a9e-b46b-4b94-ade5-5d2c98be4f66.xhtml](https://learning.oreilly.com/library/view/generative-adversarial-networks/9781789136678/fe014a9e-b46b-4b94-ade5-5d2c98be4f66.xhtml)
- [https://medium.com/@mrgarg.rajat/implementing-stackgan-using-keras-a0a1b381125e](https://medium.com/@mrgarg.rajat/implementing-stackgan-using-keras-a0a1b381125e)

