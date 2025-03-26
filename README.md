# Impulse Response Generator with GANs

*An AI system that generates custom impulse responses from acoustic parameters*

## 📌 Overview

This project uses generative adversarial networks (GANs) to create custom impulse responses (IRs) from acoustic parameters. Using the Boom Library dataset, the system learns to generate realistic acoustic spaces through parameter control.

## 🚀 Key Features

- **Parameter-to-IR Generation**: Transform acoustic parameters into custom impulse responses
- **Boom Library Integration**: Trained on high-quality acoustic samples
- **Parameter Control**: Adjust size, brightness, and decay through text
- **Real-time Capable**: Optimized for low-latency operation
- **Stereo Output**: Generates spatially realistic IRs

## 📂 Project Structure
```
Gen_IR_with_GAN/
 ├── data/ # Boom Library dataset (after processing)
 ├── models/ # Pretrained models
 ├── notebooks/ # Jupyter notebooks for exploration
 ├── scripts/ # Main processing scripts
 │ ├── preprocess.py # Data preparation
 │ ├── train.py # Model training
 │ └── generate.py # Inference pipeline
 └── requirements.txt # Python dependencies
```
 ## 🛠️ Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Polymath1108/Gen_IR_with_GAN.git
   cd Gen_IR_with_GAN
   ```
2. Install dependencies
  ```bash
    pip install -r requirements.txt
  ```
3. Download the Boom Library Impulse Responses and place in data/raw_irs/

## 🔧 Usage
1. Data Preparation 
  Process Boom Library IRs and generate metadata:
  ```bash
    python scripts/preprocess.py \
  --input_dir data/raw_irs \
  --output_dir data/processed
  ```
2.training  
  GAN Model:
  ```bash
    python scripts/train.py gan \
  --data_dir data/processed \
  --output_dir models/gan \
  --epochs 100
  ```
3. Generation
  Create IRs:
  ```bash
  python scripts/generate.py \
--size 0.8 \
--brightness 0.6 \
--decay 3.2 \
--output my_ir.wav
  ```

## 🧠 Model Architecture
IR Genertaion(GAN)
 1. **Generator**: Creates IRs from parameter vectors
   - Input:[size, brightness, decay, density]
   - Output: 44100-sample stereo IR
 2. **Discriminator**: Evaluates realism of generated IRs
 3. **Loss**: Wasserstein loss with gradient penalty

## 📊 Performance Metrics

| Model     | Loss     | Inference Time| VRAM Usage |
| :-------- | :------- | :------------------------- | :----------------|
| `GAN  Generator` | `0.25` | `8ms` |  `1.5GB`|

## 🎛️ Parameter Control
Control IR characteristics through text:

| Parameter | Range     | Description             |
| :-------- | :------- | :-------------------------------- |
| `size`      | `0-1` | Physical space dimensions |
| `Brightness`      | `0-1` | High-frequency content |
| `Decay`      | `0-10` | Reverb tail length (seconds) |
| `Density`      | `0-1	` | Reflection complexity |


## 🙏 Acknowledgments

 - Boom Library for high-quality impulse responses
 - PyTorch team for GAN framework
