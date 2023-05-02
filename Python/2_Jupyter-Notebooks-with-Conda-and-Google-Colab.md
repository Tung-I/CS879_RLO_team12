# Jupyter Notebooks with Conda and Google Colab

In this chapter, we will cover how to use Jupyter Notebooks with Conda and Google Colab. Jupyter Notebooks are interactive, web-based computing environments that allow you to create, share, and collaborate on documents that contain live code, equations, visualizations, and narrative text.

### Step 1: Launch Jupyter Notebook using Conda 

In your command prompt or terminal, navigate to your preferred working directory and run the following command:

```
jupyter notebook
```

This will open a new browser window with the Jupyter Notebook interface. You can now create, edit, and run notebooks in your local environment.

### Step 2: Create a New Notebook

In the Jupyter Notebook interface, click the "New" button in the top-right corner and select "Python 3" (or the appropriate kernel for your environment). This will create a new notebook with an empty code cell.

```
conda create --name myenv python=3.9
```

Replace "myenv" with your desired environment name and "3.9" with the desired Python version. Type `y` to confirm installing missing packages.

### Step 3: Notebook Cells
There are two main types of cells in Jupyter Notebooks: code cells and markdown cells. Code cells contain executable code, while markdown cells contain formatted text, equations, and images.

- To add a new cell, click the "+" button in the toolbar or use the keyboard shortcut "Shift + Enter".
- To change the cell type, use the dropdown menu in the toolbar or press "M" for markdown and "Y" for code.
- To execute a code cell, click the "Run" button in the toolbar or use the keyboard shortcut "Shift + Enter".

You can learn more about working with Jupyter Notebooks by following this free [tutorial](https://www.dataquest.io/blog/jupyter-notebook-tutorial/).

### Step 3: Try Google Colab

Google Colab is a free, cloud-based Jupyter Notebook environment that allows you to create, share, and collaborate on Python code and data science project (think Google Docs for Jupyter Notebooks).

Visit the Google Colab [website](https://colab.research.google.com/). Sign in with your Google account if prompted.

Click the "File" menu in the top-left corner and select "New notebook" to create a new Jupyter Notebook. Alternatively, you can open an existing notebook from your Google Drive or GitHub repository by selecting "Open notebook" from the "File" menu.

Google Colab's interface is similar to Jupyter Notebooks.

Or you can learn more about working with Jupyter Notebooks by following this free [tutorial]( https://colab.research.google.com/notebooks/intro.ipynb).
