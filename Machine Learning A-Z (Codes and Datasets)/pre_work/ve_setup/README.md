# Virtual Environment Setup

__Authors__: Michael Prappas, Riebeeck van Niekerk

### What is the purpose of this document?

This guide aims to bring a newcomer up to speed with Anaconda and working with virtual environments. Please be sure to read through everything if you have never set up environments before. Feel free to use YouTube and Google as a reference if you encounter any issues.

### Why do I need a virtual environment?

In the Apprentice Academy, we work with many different libraries as a starting point for our machine learning development. We're going to use the [Anaconda platform](https://www.anaconda.com/products/individual)'s package manager, known as [Conda](https://docs.conda.io/projects/conda/en/latest/index.html), to ensure that everyone can get up and running with the libraries needed.

Every library you install comes with a version and dependencies. Over time, the authors of that library will add new functionality and publish new versions. More often than not, libraries require code from other libraries; this is known as a dependency. Once you install dozens of libraries, each with their own versions, it's critical to manage dependencies so that nothing breaks when you go to use one of them. Package managers like Conda simplify the process to install and update libraries plus manage the dependencies between them.

Whenever you start a new project or even work with a new library, it's a best practice to create a virtual environment. Virtual environments are separate from your main installation (known as your `base` environment), where you can install fresh copies of libraries. With a smaller number of libraries than you might install in your `base` environment, dependencies become easier to manage. If you install all new libraries in your `base` environment, you will eventually run into dependency issues, too. In addition, you can share a YAML file with a listing of all of the libraries in that virtual environment, so that others can use the same libraries as you when running your code. This prevents issues that might come as a result of broken dependencies or uninstalled libraries.

Professional data scientists almost always work in virtual environments. For the sake of simplicity and ease of installation, we're going to use virtual environments, too, for the Apprentice Academy. See below for how to get up and running.

### 1. Install Anaconda

Download and install your operating system's version of [Anaconda](https://www.anaconda.com/products/individual) with __Python 3.7__.

If you face any issues, you can also install [miniconda](https://docs.conda.io/en/latest/miniconda.html), which is a lightweight version of the Anaconda distribution. For more information on the differences between Anaconda and miniconda, see [here](https://deeplearning.lipingyang.org/2018/12/23/anaconda-vs-miniconda-vs-virtualenv/).

For more information on virtual environments and conda, see [here](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/environments.html) and [here](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html).

### 2. Get up and running with Anaconda

- Once the installation finishes, you should have everything you need to get started
- On Windows, search for "Anaconda Prompt" in the Start Menu

![](images/windows_conda_open.PNG)

- On MacOS, open Terminal

![](images/macOS_conda_open.png)

- Type the command `conda -V` and hit Enter. This tells you that conda is installed and gives the latest version.

![](images/windows_conda_version.png)

- Type the command `conda update conda` and hit Enter. When asked to Proceed, type `y` and hit Enter. This will ensure conda is updated to the latest version

![](images/macOS_conda_update_conda.png)

- Create a new test virtual environment for testing by running the following line and hitting Enter. You can replace `your_env_name` with whatever name you'd like to give to this environment.

  ```conda create --name test_env python=3.7 scipy=1.5.0```
  
  ![](images/windows_conda_test_env.png)

  - At this point, you will see a list of packages to be downloaded and installed. When asked to Proceed, type `y` again and hit Enter.
  - Once you're finished, you will see how to activate and deactivate your environment.
  
  ![](images/windows_conda_test_env_2.png)

- Type the command `conda env list` and hit Enter
  - This shows you the list of environments you have available along with your current environment indicated with `*`.
  
  ![](images/windows_conda_env_list.png)

- To change to your new environment and see the list again, enter the commands `conda activate test_env` and `conda env list`

  ![](images/windows_conda_test_env_activated.png)

- To deactivate and delete this environment, enter the following commands one by one:

  ```
  conda deactivate
  conda env remove -n test_env
  conda env list
  ```
  
  ![](images/windows_conda_remove_test_env.png)
  
  - Now you will see that the test environment you created has been removed
 
 ### 3. Creating a new virtual environment from a YAML file
 
A [YAML](https://en.wikipedia.org/wiki/YAML) file is a commonly used, human-readable configuration file. We will use a pre-built YAML file for building a virtual environment to use during Apprentice Academy.

In short, the `.yaml` file contains a set of libraries and instructions that conda can interpret and use to create a virtual environment. You can open the `.yaml` file to inspect its contents - you'll notice over 300 packages referenced there. These libraries are what you'll need in your virtual environments to run all of the code throughout Apprentice Academy.

__Note__: We have provided separate `.yaml` files for Windows (`academy_windows_env.yaml`) and MacOS (`academy_macos_env.yaml`) in this directory. You'll need your operating system's file available on your hard disk (either as a single file download or in a cloned GitHub repository) to proceed.

- Open Anaconda Prompt (Windows) or Terminal (MacOS) and navigate to the folder where your operating system's `.yaml` file is saved
  - The command `cd` lets you change directories (with an absolute or relative filepath)
  - The command `ls` prints the files in the current directory
  - The command `pwd` prints your current directory
 
- Type the following command to create your environment: `conda env create -f academy_windows_env.yaml` (Windows) or `conda env create -f academy_mac_env.yaml` (Mac)
  - You should see something similar to the following:
  ![](images/windows_env_from_yaml.png)
  - Since over 300 packages will be installed, give this command 5-10 minutes to complete

- Activate your new environment (`conda activate academy`) to ensure that everything installed properly

- Navigate to the folder in which you would like to work for the duration of the Academy. Preferably that folder is where the GitHub repository is cloned

- Finally, run the command `jupyter notebook` to launch Jupyter Notebook from this virtual environment

- If everything has been done correctly, you should see a command line window pop up as well as a new tab in your default web browser open

  ![](images/windows_jupyter_browser.png)

- If you ever close this tab/window by accident, you can reopen Jupyter Notebook without shutting it down by entering the `localhost` address on a new tab of your web browser:

  ![](images/windows_jupyter_cli.png)
