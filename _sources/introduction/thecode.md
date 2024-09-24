# The Code

The Code was created using ‘R’ and data from the CSO Census and Copernicus. The easiest way to run the code is via a conda environment.

The environment mimics the R environment that the code was developed upon, therefore allowing the code to run without errors. This environment is created and managed using Anaconda. The following instructions will guide you through the steps to install Anaconda and use the code.

Step 1: Download The Jupyter Book: Clone or download the Jupyter Book repository from GitHub using the button 'Clone or Download' above and save it somewhere locally on your computer, e.g. C:\SVI.

Step 2. Anaconda: Install Anaconda. Open the Anaconda prompt (PC) or on a Mac or Linux system open a terminal window. Use the cd command to change the directory, and navigate to go the folder where you have downloaded the ISEVHI repository (see here for information on how to use the command prompt).

Step 3: Create a new environment: Create a new environment named SVI with all the required packages:

conda env create -f environment.yml -n SVI
This environment should ensure that all the required packages are installed. This environment is called SVI. The next step is to active the environment in the command prompt with:

conda activate SVI
The terminal command line prompt should now have changed from (base) to (SVI).
