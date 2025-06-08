![1__IbvD3wE1ZcWvNHszZ1FOg](https://github.com/user-attachments/assets/98d735f8-5213-4c23-b9fd-2d006197824f)

## Introduction

Hello everyone,

In this guide, I’ll show you how to install and test NVIDIA’s CUDA Toolkit and cuDNN on your Windows machine.

First, let’s briefly explain what these technologies are:

**CUDA** (Compute Unified Device Architecture) is a parallel computing platform and programming model developed by NVIDIA that lets you harness the massive parallel processing power of your GPU for general-purpose computing. With CUDA, compute-intensive applications—from scientific simulations to AI workloads—can achieve major speedups.

**cuDNN** (CUDA Deep Neural Network Library) is a GPU-accelerated library of highly tuned routines for deep learning. Developed by NVIDIA, cuDNN optimizes the training and inference of neural networks and integrates seamlessly with popular frameworks like TensorFlow and PyTorch, squeezing out maximum performance from your GPU.

When used together, CUDA and cuDNN deliver substantial performance boosts for AI and deep learning projects—helping researchers and engineers iterate faster and deploy more powerful models.

> **Prerequisite:** You’ll need an NVIDIA GPU with the correct drivers installed. In the next section we’ll verify your driver’s CUDA compatibility.

![1_d0BRi1sS3W-FyKskEV5h8g](https://github.com/user-attachments/assets/16be27d0-a300-43b9-bbb2-c76222da8470)


![1_a9-Z4oYrPiRTntEaHj5gZQ](https://github.com/user-attachments/assets/07cd489e-5726-4921-a2e4-cb23ab080a28)


🔍 Check NVIDIA Driver & CUDA Compatibility

Open a terminal (PowerShell or CMD) and run:

```bash
nvidia-smi
```

You should see output similar to this:

The “CUDA Version” column shows which CUDA release your current NVIDIA driver supports. Use this information to pick the matching CUDA Toolkit installer in the next step.
