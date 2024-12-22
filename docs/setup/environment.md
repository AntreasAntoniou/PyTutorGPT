# Setting Up Your Python Development Environment

## Overview
We'll be setting up:
1. WSL2 (Windows users only) - Linux environment for Windows
2. Conda - For managing Python versions and environments
3. uv - A fast Python package installer (installed via conda's pip)
4. VS Code - Our code editor
5. Required Python packages

## Step-by-Step Installation

### Windows Users: Setting Up WSL2 First
1. Open PowerShell as Administrator and run:

    wsl --install

2. Restart your computer when prompted

3. After restart, a Ubuntu window will open automatically
   - Create a username and password when prompted
   - Keep these credentials safe - you'll need them!

4. Update Ubuntu:

    sudo apt update && sudo apt upgrade -y

5. Install build essentials:

    sudo apt install build-essential

6. Verify WSL installation:

    wsl --version

7. Install VS Code WSL extension:
   - Open VS Code
   - Install "Remote - WSL" extension
   - Click the green button in the bottom-left corner
   - Select "New WSL Window"

Now proceed with the rest of the setup IN YOUR WSL TERMINAL.

### 1. Installing Conda

#### Windows (via WSL/Ubuntu) and Linux
1. Download Miniconda:

    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

2. Install:

    bash Miniconda3-latest-Linux-x86_64.sh

3. Accept the license and defaults
4. Restart your terminal or run:

    source ~/.bashrc

5. Verify installation:

    conda --version

#### macOS
1. Download Miniconda:
   - Visit: https://docs.conda.io/miniconda/
   - Download the latest macOS installer
2. Install from Terminal:

    bash ~/Downloads/Miniconda3-latest-MacOSX-x86_64.sh

3. Accept the license and defaults
4. Restart your terminal or run:

    source ~/.zshrc

5. Verify installation:

    conda --version

### 2. Creating and Activating Course Environment

    # Create new environment
    conda create -n pylearn python=3.11

    # Activate environment
    conda activate pylearn

    # Verify Python version
    python --version

### 3. Installing uv using conda's pip
With your environment activated:

    # Install uv using conda's pip
    pip install uv

    # Verify installation
    uv --version

### 4. Installing Required Packages
With your environment activated:

    # Install packages using uv
    uv pip install numpy pandas jupyter matplotlib requests

    # Verify installations
    python -c "import numpy; import pandas; import matplotlib; import requests; print('All packages installed successfully!')"

### 5. Installing and Configuring VS Code

#### All Platforms
1. Download VS Code:
   - Visit: https://code.visualstudio.com/
   - Choose your platform's installer

2. Install Required Extensions:
   - Python (Microsoft)
   - Jupyter
   - Python Indent
   - autoDocstring
   - (Windows users) Remote - WSL

3. Configure VS Code:
   - Open Command Palette (Cmd/Ctrl + Shift + P)
   - Type: "Python: Select Interpreter"
   - Choose the `pylearn` environment
   - For Windows: Ensure you're in a WSL window first

## Verification Steps

### 1. Environment Check
Create and run `test_env.py`:

    import sys
    import numpy as np
    import pandas as pd
    import matplotlib.pyplot as plt

    # Print versions
    print(f"Python version: {sys.version}")
    print(f"NumPy version: {np.__version__}")
    print(f"Pandas version: {pd.__version__}")

    # Create test plot
    plt.plot([1, 2, 3], [1, 2, 3])
    plt.title("Test Plot")
    plt.show()

### 2. Jupyter Notebook Check
1. In terminal:

    jupyter notebook

2. Create new notebook
3. Run a test cell:

    print("Jupyter is working!")

## Troubleshooting

### Common Issues

#### WSL Issues (Windows)
1. If WSL install fails:
   - Enable virtualization in BIOS
   - Run Windows Update
   - Try manual installation:

    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

#### Conda Issues
1. Conda not found after installation:
   - Windows/WSL/Linux: `source ~/.bashrc`
   - macOS: `source ~/.zshrc`

2. Environment activation fails:
   - Try: `conda init bash` (or `zsh` for macOS)
   - Restart terminal

#### Package Installation Issues
1. If uv installation fails:
   - Try: `pip install --upgrade pip`
   - Then retry: `pip install uv`

2. If package installation fails:
   - Try traditional pip:

    pip install numpy pandas jupyter matplotlib requests

### Getting Help
- Course Forum: [Link]
- Discord Channel: [Link]
- Office Hours: [Schedule]

## Next Steps
1. Complete all verification steps
2. Try creating and running a Jupyter notebook
3. Read the Python setup guide in Week 1 materials
4. Start with Week 1 content

## Updates
Last updated: 2024-12-21
Python version: 3.11
uv version: latest