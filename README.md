# VisionCaptioner

**VisionCaptioner** is an AI-powered image captioning system that combines **Convolutional Neural Networks (CNNs)** and **Transformers** to automatically generate human-like captions for images.  

This project uses **PyTorch** and provides a pipeline for training, checkpointing, and generating captions using the **COCO 2017 dataset**.  
 fully operational at http://127.0.0.1:7860/
---

## Features

- 📤 Load and preprocess COCO 2017 images and captions  
- 📝 Automatically generate captions with a Transformer decoder  
- 🎯 ResNet-50 encoder extracts high-level visual features  
- 💾 Save and load model checkpoints for training or inference  
- 🌍 GPU support for faster training  

---

## Tech Stack

- **Frameworks**: PyTorch, torchvision, transformers  
- **Modeling**: ResNet-50 encoder + Transformer decoder  
- **Dataset**: MS COCO 2017 (images + captions)  
- **Preprocessing**: PIL, torchvision.transforms  
- **Tokenizer**: BERT tokenizer (`bert-base-uncased`)  

---

## Project Workflow

1. **Dataset Preparation**  
   - Load COCO 2017 images and captions using `COCODataset` class.  
   - Preprocess images (`224x224` resize, tensor conversion).  
   - Tokenize captions using BERT tokenizer.  

2. **Model Architecture**  
   - **EncoderCNN**: Pretrained ResNet-50 extracts image features, followed by a linear layer + batch norm.  
   - **DecoderTransformer**: Embedding layer, positional encoding, Transformer decoder layers, output linear layer to predict tokens.  

3. **Training**  
   - Use cross-entropy loss with teacher forcing.  
   - Optimizer: Adam on decoder parameters + encoder’s FC layer.  
   - Checkpoints saved after every epoch.  

4. **Inference / Caption Generation**  
   - Load trained checkpoints.  
   - Preprocess new images and generate captions using `generate_caption()` function.
