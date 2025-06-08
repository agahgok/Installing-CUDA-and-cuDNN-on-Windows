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

![1_GwAUiXylgvaifuqrZd237A](https://github.com/user-attachments/assets/c797ddac-871d-4d84-baec-bad8055345b1)

In the top row of the NVIDIA-SMI output (on the right side), you’ll see your current GPU driver and the CUDA version it supports.

---

## 🏗️ Install Visual Studio

Before you install CUDA, download **Visual Studio 2022 Community** from  
https://visualstudio.microsoft.com/

When running the installer, select the **“Desktop development with C++”** workload (no other components are required). You can proceed with all the default options.

![1_Fe1X27OnUVjNG8TNR8b0cg](https://github.com/user-attachments/assets/d19cab87-882f-424a-8055-d0ffeaf26df7)

Once the installation finishes, close Visual Studio and move on to the CUDA installation.

## 🚀 Download & Install CUDA Toolkit

1. Open your browser and go to the CUDA Toolkit Archive:  
   https://developer.nvidia.com/cuda-toolkit-archive  

![1_ITtF5ydbL2IYDqO1MLMkQw](https://github.com/user-attachments/assets/9d44bfb8-b722-482d-9c93-49f56c2d29da)

2. From the list of releases, choose the CUDA version that matches your driver’s supported CUDA (e.g. **CUDA 12.4**).  
   *Tip:* Minor patch numbers (e.g. 12.4.x) rarely introduce incompatibilities, so you can safely pick the latest 12.4.x.

3. Select **Windows → x86_64 → exe (local)** and download the installer (~3 GB).

4. Run the `.exe` with all **default options** to complete the CUDA installation.

3. On the download page, select the options that match your system:
   - **Operating System:** Windows  
   - **Architecture:** x86_64  
   - **Installer Type:** exe (local)

![1_3gNxK6z7HAI8ibzPywsGCA](https://github.com/user-attachments/assets/44ae31a9-eb12-468c-8d4f-505d5336d121)

   The `.exe` file is roughly **3 GB** — save it locally before proceeding.

5. After the download completes, double-click the `.exe` file to launch the installer.

   During installation, you don’t need to change any settings—just proceed with all default options until it finishes. You should see screens similar to this:

![1_ZRIRtauaOyKUHwoKwjWfew](https://github.com/user-attachments/assets/b3a18755-f727-4b93-b047-976a0d1d0ff0)

## ⚙️ Set Environment Variables

1. In the Windows search bar, type **"Edit the system environment variables"** and open it:  

2. In the **System Properties** window, click the **“Environment Variables…”** button in the bottom-right corner.

## ⚙️ Set Environment Variables

1. Open **System Properties**:  
   - Press Start and search for **“System Environment Variables”**, then select **“Edit the system environment variables”**.  
   - In the dialog that appears, click **Environment Variables…** in the bottom-right.  
   ![1_SXKEs_Kbm2nKKmXYG7-u1Q](https://github.com/user-attachments/assets/37d0917f-1fff-4005-8f73-dcffe69925e3)


2. In the **System variables** section, find and double-click **Path**.  
   ![1_WmdM5oSbC-W4f2NgahX5Mw](https://github.com/user-attachments/assets/a37fb615-31dc-46d7-a155-c631d8fd45e1)


3. In the **Edit environment variable** window, make sure the following CUDA paths (replace `v12.4` with your installed version) are present. If any are missing, click **New** and add them:

```bash
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\bin
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\libnvvp
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\include
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\lib\x64
```
![1_sgJx9jHR6PKeh4vzk52YhA](https://github.com/user-attachments/assets/30c526c1-2c24-4a4d-a88e-952c7f1c73c7)


4. Click **OK** on all dialogs, then **restart** your PC.

After rebooting, you’re ready to verify that CUDA is installed correctly.


## ✔️ Verify CUDA Installation

After rebooting your PC, open a terminal (PowerShell or CMD) and run:

```bash
nvcc --version
```

You should see output similar to this:

For example:

```bash
nvcc: NVIDIA (R) Cuda compiler driver
Cuda compilation tools, release 12.4, V12.4.131
```

If you see your CUDA version listed, congratulations—CUDA is installed correctly!
