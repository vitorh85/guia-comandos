# Python, Jupyter e VSCode

## 1. Instalar as extensões no VSCode:

* Python
* Pylance
* Remote Development
* Jupyter
* Code Runner
* Material Icon Theme

## 2. Criar novo jupyter notebook no VSCode:

	Ctrl + Shift + P
	>Jupyter: Create New Blank Notebook

## 3. Roda trechos do código em uma janela interativa do python (como se estivesse no jupyter notebook):

	#%%

## 4. Abre o Jupyter notebook (https://jupyter.org/install):

	I. JupyterLab:
	> pip install jupyterlab
	> jupyter-lab

	II. Jupyter Notebook:
	> pip install notebook
	> jupyter notebook

## 5. Configurações do VSCode via JSON:

```json
{
    "[python]": {
        "editor.formatOnType": true
    },
    "workbench.iconTheme": "material-icon-theme",
    "explorer.compactFolders": false,
    "code-runner.runInTerminal": true,
    "code-runner.executorMap": {
        "python": "cls ; python -u",
    },
    "code-runner.ignoreSelection": true
}
```

## 6. Módulos populares do Python:

* __Requests__: python HTTP for humans
	> pip install requests

* __Django__: a high-level (heavyweight) python web framework that allow you to make well enterprise-level websites
	> pip install Django

* __Flask__: a simple framework for building complex applications (lightweight Django competitor)
	> pip install Flask

* __BeautifulSoup4__: screen-scraping library
	> pip install beautifulsoup4

* __Selenium__: automation on websites essentially
	> pip install selenium

* __Numpy__: is the fundamental package for array computing with python
	> pip install numpy

* __Pandas__: powerful data structures for data analysis, time series and statistics
	> pip install pandas

* __Matplotlib__: python plotting package
	> pip install matplotlib

* __Opencv-python__: wrapper package for OpenCV python bindings (image and video data processing)
	> pip install opencv-python

* __Tensorflow__: complete open source for machine learning (GPU support)
	> pip install tensorflow

* __Scikit-learn__: simple and efficient tools for predictive data analysis (built on NumPy, SciPy, and matplotlib)
	> pip install scikit-learn
