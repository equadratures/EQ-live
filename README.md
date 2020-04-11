# EQ-live
Jupyter notebooks for demonstration, exploration and prototyping of Effective Quadratures. These can be run on the cloud with [Google Colaboratory](https://colab.research.google.com/) or [Azure Notebooks](http://notebooks.azure.com).

The choice of Google Colab or Azure notebooks us yours. Previewing and sharing notebooks is arguably easier with Colab, but reading/writing persistant data files is arguably easier with Azure. It may come down to whether you have a Microsoft or Google account!

# Google Colaboratory
## Opening notebooks

* First Method - To open notebooks from Github. Go to https://colab.research.google.com switch to Github tab and enter an organization or URL.

* Second Method - Github jupyter notebooks can directly be accessed on Google Colaboratory by using CPU/GPU/TPU runtimes by replacing https://github.com in the URL by https://colab.research.google.com/github/.

* Third Method A much easier way is to use “Open in Colab” Extension for Chrome.

Edited from https://www.google-colab.com/google-colab-tips-and-tricks/.

## Sharing notebooks
Notebooks can be saved to your Google drive. The share button in the top right of the colab interface can be used to share notebooks once saveed. Notebooks can also be pushed to github Gist's or Repo's for sharing.

## Loading and saving data
This is more involved, as persistant storage on the Google Virtual Machine (VM) instance isn't available. Data must be stored on Google drive, which can be mounted within notebooks:

```python
from google.colab import drive
drive.mount('/content/drive',force_remount=True)
%cd "/content/drive/My Drive/<folder name>"  ### Change directory to preferred working space
```

Then temporarily copied to the VM for faster read/write speeds:

```python
!cp -r "/content/drive/My Drive/<folder name>" ./img
```

For loading data files required in notebooks in this Repo, we instead download them from github with `wget` to avoid having to maintain an additional Google drive repository. For example:

```python
!wget https://github.com/Effective-Quadratures/EQ-live/blob/master/Blog_posts/points_to_run.npy?raw=true
```

# Azure Notebooks
## Opening notebooks
The notebooks in this repo can be run on Microsoft Azure notebooks by going [here](https://notebooks.azure.com/ascillitoe/projects/eq-live) and cloning the Azure notebooks project. Click on the Jupyter notebook you wish to run, select "Python 3.0" or "Python 3.6" as the kernel, and Azure will then load the neccesary dependencies from the requirements.txt file. 

*Note 1*: The notebooks won't be formatted properly if opened in HTML preview mode. You must sign in and run them properly to see figure etc. 

*Note 2*: Initialising the kernel and loading the dependencies (such as the `equadratures` and `matplotlib` python packages) may take some time, especially when using "Free Compute" resources. Keep an eye on the grey dot in the top right corner, when it goes clear the kernel is "Idle" and you're good to go. For this reason it is recommended that you do not restart the kernel (or rerun the package import cell) when interacting notebooks unless need to. 

## Loading and saving data
The Azure notebook [project](https://notebooks.azure.com/ascillitoe/projects/eq-live) you will clone is itself a clone of this github repo. All the data files stored on this github repo should be accesible from your cloned Azure project. To save data you can download it to a local machine, or push your cloned project to your own github fork of this repo.

## Sharing notebooks
There is an "Open terminal" button on Azure notebooks to open a terminal. Standard git commands can be used here to push to your own fork of this github Repo. 
