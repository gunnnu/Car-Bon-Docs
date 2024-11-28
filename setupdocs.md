
# Car-Bon System: Technical Setup Guide

## Prerequisites

Before beginning the installation, ensure you have:

-   Administrator access to the project repository of github
-   Windows operating system
-   Basic understanding of command-line interfaces

## Version Control Setup

1.  Install Git
    -   Download and install from the official website
    -   Configure with your credentials
2.  Clone Project Repository
    
    bash
    
    Copy
    
    `git clone https://github.com/gunnnu/Car-Bon_UI.git`
    
    **Note:** Repository access requires admin invitation

## Windows Subsystem for Linux (WSL) Configuration

1.  Open PowerShell as Administrator
    
    powershell
    
    Copy
    
    `wsl --install`
    
2.  Complete Ubuntu installation and create user account

## Python Environment Preparation

1.  Install Python 3.9+
    
    bash
    
    Copy
    
    `python3 --version`
    
2.  Configure Python System
    
    bash
    
    Copy
    
    `sudo  apt  install python-is-python3 sudo update-alternatives --install /usr/bin/python python $(readlink -f $(which python3))  3`
    
3.  Package Management
    
    bash
    
    Copy
    
    `sudo  apt update sudo  apt  install python3-pip pip install poetry`
    

## AWS SDK Configuration

### AWS Account Setup

1.  Create AWS Account
    -   Visit AWS Console
    -   Sign up or log in to existing account
2.  Generate Access Key
    -   Navigate to IAM > Users
    -   Select or create user
    -   Go to "Security credentials" tab
    -   Create access key
3.  AWS CLI Installation
    
    bash
    
    Copy
    
    `curl  "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" unzip awscliv2.zip sudo ./aws/install`
    
4.  AWS CLI Configuration
    
    bash
    
    Copy
    
    `aws configure`
    
    -   Enter access key and secret access key
    -   Select region: us-east-1
    -   Select output format: json

**Security Recommendations:**

-   Store access keys securely
-   Implement least privilege access
-   Avoid sharing access keys publicly

## API Development Environment

1.  Navigate to Project Directory
    
    bash
    
    Copy
    
    `cd Car-bon_UI/src/Api/`
    
2.  Set Up Virtual Environment
    
    bash
    
    Copy
    
    `poetry shell poetry install`
    
3.  Launch API Server
    
    bash
    
    Copy
    
    `uvicorn app.index:main --reload`
    
4.  Access Documentation
    -   Open [http://localhost:8000/](http://localhost:8000/)

## Frontend Setup

### Node.js Installation

1.  Install Node.js
    
    bash
    
    Copy
    
    `sudo  apt  install nodejs`
    
2.  Verify Version
    
    bash
    
    Copy
    
    `node --version`
    
    **Recommended:** Node 18 or 20

### Frontend Development

1.  Navigate to Frontend Directory
    
    bash
    
    Copy
    
    `cd Car-bon_UI/src/Ui/old/corbon_ui/`
    
2.  Install Dependencies
    
    bash
    
    Copy
    
    `npm  install npm audit fix`
    
3.  Launch Development Server
    
    bash
    
    Copy
    
    `npm run dev`
    
4.  Access Frontend
    -   Open [http://localhost:5173/](http://localhost:5173/)