# Python Installation and Setup

In this chapter, we will walk you through installing Python using Conda, a popular package management system. We will also cover how to create and manage different Python environments to help you work with multiple projects that require different Python versions or package dependencies.

### Step 1: Install Anaconda

[Anaconda](https://www.anaconda.com/) is a full distribution that includes Python, Conda, and a large number of pre-installed packages, tools, and libraries that streamline the workflows of data scientists and developers working with Python. Conda makes it easy to manage multiple Python environments with their unique dependencies and versions, allowing users to work on different projects without conflicts.

Follow the installation instructions for your operating system:

- [Windows](https://docs.anaconda.com/anaconda/install/windows/)
- [macOS](https://docs.anaconda.com/anaconda/install/mac-os/)
- [Linux](https://docs.anaconda.com/anaconda/install/linux/)

You can use the Conda command-line interface (CLI) by launching the Anaconda Prompt on Windows or the terminal on Linux and macOS. You can read more about it [here](https://docs.anaconda.com/free/anaconda/install/verify-install/). 

To verify installation, open a command prompt or terminal and type this command:

```
conda --version
```

You will see the version number if conda is installed successfully.

### Step 2: Create a New Conda Environment

Creating a new environment allows you to work with different versions of Python and packages without conflicts. To create a new environment, use the following command:

```
conda create --name myenv python=3.9
```

Replace "myenv" with your desired environment name and "3.9" with the desired Python version. Type `y` to confirm installing missing packages.

### Step 3: Activate or Deactivate Your Conda Environment
To activate (enter) the environment you just created, use the following command:

```
conda activate myenv
```

To deactivate (leave) the environment, use the following command:

```
conda deactivate
```

### Step 4: Manage Your Environments

You can now install packages in your new environment using the `conda install` command:

```
conda install numpy
```

Replace "numpy" with the package you want to install.

You can also install packages from a txt file by using the `conda install` command with the `--file` option.

First, create a txt file containing the names of the packages you want to install, each package name on a new line. For example, call this file `requirements.txt`.

Then, cd to the directory where the `requirements.txt` file is located.

Next, run the following command (make sure you have activated the desired environment before running this command):

```
conda install --file requirements.txt
```

To check what packages are installed in the current active environment, use this command:

```
conda list
```

To list all environments, use this command:

```
conda env list
```

 
