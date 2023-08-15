# ML_Real_State
End-to-End Machine Learning Project

## Create a virtual environment
Open the CMD console, navigate to your project directory, and create your virtual environment.

```bash
  python -m venv venv
```
Go to the project folder. enter venv, script, then activate and install libraries.
```bash
  activate
  pip install -U jupyter matplotlib numpy pandas scipy scikit-learn
```
Once it's activated and the libraries are installed, open the Jupyter Notebook.
```bash
  jupyter notebook
```
## Set up the data 
We will use the dataset from [link](https://raw.githubusercontent.com/ageron/handson-ml2/master/). And create a python function to 
call the data.
```
  import os
  import tarfile
  from six.moves import urllib
  
  DOWNLOAD_ROOT = "https://raw.githubusercontent.com/ageron/handson-ml2/master/"
  HOUSING_PATH = os.path.join("datasets", "housing")
  HOUSING_URL = DOWNLOAD_ROOT + "datasets/housing/housing.tgz"
  #it creates a datasets/housing directory in
  #your workspace, downloads the housing.tgz file, and extracts the housing.csv from it in
  #this directory
  def fetch_housing_data(housing_url=HOUSING_URL, housing_path=HOUSING_PATH):
   if not os.path.isdir(housing_path):
       os.makedirs(housing_path)
       tgz_path = os.path.join(housing_path, "housing.tgz")
       urllib.request.urlretrieve(housing_url, tgz_path)
       housing_tgz = tarfile.open(tgz_path)
       housing_tgz.extractall(path=housing_path)
       housing_tgz.close()
  fetch_housing_data()
```
Lets proceed to turn it into a pandas dataframe:
```
#This function returns a Pandas DataFrame object containing all the data
  import pandas as pd
  def load_housing_data(housing_path=HOUSING_PATH):
   csv_path = os.path.join(housing_path, "housing.csv")
   return pd.read_csv(csv_path)
  housing = load_housing_data()
  housing.head()
```
The information from the datafrmae is:
![image](https://github.com/lictical/ML_Real_State/assets/25531904/e2da11ac-430f-47c5-ab22-a226c9fe93a7)





