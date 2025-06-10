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

## 📥 Download & Install cuDNN

Once CUDA is installed and your environment variables are updated, you’re ready to install cuDNN.

1. Visit the cuDNN Archive:  
   https://developer.nvidia.com/rdp/cudnn-archive  
   ![1_Gs2oFRZLYF6HNM4IE9dPwA](https://github.com/user-attachments/assets/d8d19315-b558-4d64-bd94-610364767247)


2. From the list, choose the cuDNN release that matches your CUDA version (for example, **cuDNN v8.9.7** for CUDA 12.x).

3. Click the cuDNN version you need (for example, **cuDNN v8.9.7** for CUDA 12.x). You’ll be prompted to sign in or register for a free NVIDIA Developer account—complete that to access the download.

4. On the download page, select your OS and package format:
   - **Operating System:** Windows  
   - **Package Format:** ZIP  

   ![1__67SGk0CaSWpcaPfcbvSaw](https://github.com/user-attachments/assets/539c3eeb-f9db-4e7c-abfa-92812e237c76)

5. **Extract & Copy cuDNN Files**

   - Unzip the downloaded cuDNN archive to a temporary folder.  
   - Copy the folders into your CUDA installation (replace `v12.4` with your version):

     | Source Folder      | Destination Path                                                |
     | ------------------ | --------------------------------------------------------------- |
     | `bin\*`            | `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\bin\`  |
     | `include\*`        | `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\include\` |
     | `lib\x64\*`        | `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4\lib\x64\` |

6. **Update Environment Variables**

   1. Open **System Environment Variables**:  
      - Press **Start**, type “System Environment Variables” and select **Edit the system environment variables**.  
      - Click **Environment Variables…**  
      ![1_SXKEs_Kbm2nKKmXYG7-u1Q](https://github.com/user-attachments/assets/160c796e-3d75-4b24-8690-92034f44cc28)


   2. In the **System variables** section, find **Path** and click **Edit**:  
      ![1_WmdM5oSbC-W4f2NgahX5Mw](https://github.com/user-attachments/assets/7485a84f-52e9-464f-b836-d4fba8aaff46)



   3. Make sure these entries exist (add them if missing):

```
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vX.X\bin
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vX.X\libnvvp
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vX.X\lib
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vX.X\include

```

   4. Click **OK** on all dialogs and **restart** your PC.

   5. Ensure **all four** of these paths are listed under **Path**. After you finish editing, the **Edit Environment Variable** window should look similar to this:

   ![1_5wKg2AMqDCpbwlHo4H3Prg](https://github.com/user-attachments/assets/958573d0-6a1b-40f0-b72b-91d5990e9832)

   6. Click **OK** on all dialogs and **restart** your PC.

## ✔️ Verify CUDA & cuDNN Installation

Once your computer restarts, you’re ready to verify that both CUDA and cuDNN were installed correctly.

## 🐍 Python Test Script

To verify both CUDA and cuDNN, save the following code as `code/cudnn_test.py` (or run it in your Jupyter/Colab notebook):

```python
import tensorflow as tf
import numpy as np
import time

def cudnn_performance_test():
    model = tf.keras.models.Sequential([
        tf.keras.layers.Conv2D(32, (3, 3), activation='relu', input_shape=(28, 28, 1)),
        tf.keras.layers.MaxPooling2D((2, 2)),
        tf.keras.layers.Conv2D(64, (3, 3), activation='relu'),
        tf.keras.layers.MaxPooling2D((2, 2)),
        tf.keras.layers.Flatten(),
        tf.keras.layers.Dense(128, activation='relu'),
        tf.keras.layers.Dense(10, activation='softmax')
    ])

    model.compile(optimizer='adam',
                  loss='sparse_categorical_crossentropy',
                  metrics=['accuracy'])

    x_train = np.random.random((10000, 28, 28, 1))
    y_train = np.random.randint(10, size=(10000,))

    start_time = time.time()
    model.fit(x_train, y_train, epochs=10, batch_size=64, verbose=2)
    end_time = time.time()

    training_time = end_time - start_time
    print(f"CuDNN performans testi tamamlandı! Eğitim süresi: {training_time:.2f} saniye")

cudnn_performance_test()
```

Run it with:

```bash
python code/cudnn_test.py
```

You should see output like:

```
cuDNN performance test completed! Training time: 4.76 seconds
```

If the script runs successfully and reports a training time, your CUDA and cuDNN setup is confirmed to be working properly on your Windows machine.
