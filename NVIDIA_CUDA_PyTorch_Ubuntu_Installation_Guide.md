# Comprehensive Guide to Installing NVIDIA CUDA and PyTorch with CUDA Support on Ubuntu Headless Systems

1. **Upgrade Your Ubuntu System**:
   Start by updating and upgrading your Ubuntu system to ensure all software is up-to-date.

   ```
   sudo apt update
   sudo apt upgrade
   ```

2. **List the Recommended NVIDIA Drivers**:
   Install `ubuntu-drivers-common` and then use the `ubuntu-drivers` command to list the recommended NVIDIA drivers for your system.

   ```
   sudo apt install ubuntu-drivers-common
   sudo ubuntu-drivers devices
   ```

3. **Install the NVIDIA Driver**:
   Install the driver recommended by the `ubuntu-drivers` command. For example:

   ```
   sudo apt install nvidia-driver-535
   ```

4. **Reboot Your System**:
   After installing the driver, reboot your system to ensure proper installation.

   ```
   sudo reboot now
   ```

5. **Check the Driver Installation**:
   Once rebooted, check the installation using the NVIDIA System Management Interface.

   ```
   nvidia-smi
   ```

6. **Install GCC**:
   The GCC compiler is necessary for installing the CUDA toolkit.

   ```
   sudo apt install gcc
   gcc -v  # To verify the installation
   ```

7. **Install the CUDA Toolkit**:
   Download and install the CUDA toolkit from NVIDIA’s official site.

   ```
   wget [CUDA Toolkit Link]
   sudo dpkg -i [Downloaded File]
   sudo apt-get update
   sudo apt-get -y install cuda
   ```

8. **Reboot Your System Again**:
   Reboot your system to load the required modules for CUDA.

   ```
   sudo reboot now
   ```

9. **Environment Setup**:
   Update the environment variables for CUDA.

   ```
   nano ~/.bashrc
   # Add the following lines to the file:
   export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
   export LD_LIBRARY_PATH=/usr/local/cuda-12.2/lib64\
                            ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
   # Save and exit, then reload the file
   . ~/.bashrc
   ```

10. **Test the CUDA Toolkit**:
    Test the installation by executing the CUDA compiler.

    ```
    nvcc -V
    ```

Once CUDA is installed, you can proceed to install PyTorch with CUDA support. PyTorch provides pre-built binaries with CUDA support that can be installed using `pip`. Ensure you have Python and `pip` installed, then follow these steps:

1. **Install PyTorch with CUDA**:
   Visit the [PyTorch official website](https://pytorch.org/get-started/locally/) to find the appropriate `pip` command for your system configuration (which includes CUDA version). It usually looks something like this:

   ```
   pip install torch torchvision torchaudio
   ```

2. **Verify PyTorch and CUDA Installation**:
   Run a Python script or enter a Python interactive shell and execute the following commands to verify the installation:

   ```python
   import torch
   print(torch.__version__)
   print(torch.cuda.is_available())
   ```

This process ensures that both NVIDIA CUDA and PyTorch with CUDA support are installed and configured correctly on your Ubuntu headless system.

For more detailed instructions and potential troubleshooting, refer to NVIDIA's [CUDA Installation Guide for Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html) and the [Cherry Servers guide](https://www.cherryservers.com) for installing CUDA on Ubuntu.
