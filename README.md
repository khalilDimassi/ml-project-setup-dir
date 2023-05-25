# ML Project Setup Script

This is a setup script for initializing a machine learning project directory structure and environment.

## Usage

1. Open a command prompt or terminal.
2. Navigate to the desired location where you want to create the project.
3. Copy and paste the following script into a new file with a `.bat` extension (e.g., `setup.bat`).
4. Run the script by double-clicking on the `.bat` file.

## Script

```batch
@echo off

REM Prompt user for project name
set /p project_name=Enter project name:

REM Create the main project directory and navigate into it
mkdir %project_name%
cd %project_name%

REM Create the directory structure
mkdir app
mkdir app\api
mkdir app\config
mkdir app\models
mkdir data
mkdir data\external
mkdir data\processed
mkdir data\raw
mkdir data\splits
mkdir docs
mkdir models
mkdir notebooks
mkdir tests

REM Create __init__.py files
echo. > app\__init__.py
echo. > app\api\__init__.py
echo. > app\config\__init__.py
echo. > app\models\__init__.py
echo. > data\__init__.py
echo. > data\external\__init__.py
echo. > data\processed\__init__.py
echo. > data\raw\__init__.py
echo. > data\splits\__init__.py
echo. > docs\__init__.py
echo. > models\__init__.py
echo. > tests\__init__.py

REM Create initial Python script files
echo. > app\api\endpoints.py
echo. > app\config\settings.py
echo. > app\models\model.py
echo. > app\main.py
echo. > data\external\download.py
echo. > data\processed\preprocessing.py
echo. > models\train.py
echo. > models\evaluate.py

REM Create initial Jupyter notebooks
echo. > notebooks\exploratory_data_analysis.ipynb
echo. > notebooks\model_training.ipynb

REM Create required files
echo. > .gitignore
echo. > Dockerfile
echo. > README.md
echo. > LICENSE

REM Create a virtual environment and activate it
python -m venv MyEnv
.\MyEnv\Scripts\Activate.ps1

REM Create requirements.txt file with basic Python libraries
echo pandas >> requirements.txt
echo numpy >> requirements.txt
echo matplotlib >> requirements.txt
echo seaborn >> requirements.txt
echo scikit-learn >> requirements.txt
echo jupyterlab >> requirements.txt

REM Upgrade pip
python -m pip install --upgrade pip

REM Install required Python modules
pip install -r requirements.txt

REM Create requirements.txt file with basic Python libraries
echo pandas >> requirements.txt
echo numpy >> requirements.txt
echo matplotlib >> requirements.txt
echo seaborn >> requirements.txt
echo scikit-learn >> requirements.txt
echo jupyterlab >> requirements.txt


REM Add basic .gitignore lines
echo __pycache__/ >> .gitignore
echo MyEnv/ >> .gitignore
echo .vscode/ >> .gitignore
echo .idea/ >> .gitignore
echo *.pyc >> .gitignore
echo *.pyo >> .gitignore
echo *.pyd >> .gitignore
echo __pycache__/ >> .gitignore
echo dist/ >> .gitignore
echo build/ >> .gitignore
echo *.egg-info/ >> .gitignore
echo .cache/ >> .gitignore
echo .coverage >> .gitignore

REM Ask user for Git repository creation
set /p create_git_repo=Do you want to create a Git repository? (Y/N):
if /i "%create_git_repo%"=="Y" (
  REM Initialize Git repository and make first commit
  git init
  git add .
  git commit -m "Setup project complete"
)

echo Project setup completed.
```

Next open vscode (or your preffered IDE) and start the virtual envirement:
```shell
.\MyEnv\Scripts\Activate.ps1
```

you can start by installing the basic modules i included in your requirements file.
```shell
python -m pip install .\requirements.txt
```


## Explanation

The script performs the following steps:

1. It prompts the user to enter the project name.
2. It creates the main project directory and navigates into it.
3. It creates the directory structure for the project, including subdirectories for app, data, docs, models, notebooks, and tests.
4. It creates empty __init__.py files in each subdirectory to mark them as Python packages.
5. It creates initial Python script files in relevant subdirectories, such as endpoints.py, settings.py, model.py, etc.
6. It creates initial Jupyter notebooks for exploratory data analysis and model training.
7. It creates necessary files like .gitignore, Dockerfile, README.md, and LICENSE.
8. It sets up a virtual environment named MyEnv.
10. It adds basic lines to the .gitignore file to exclude common files and directories.
11. It prompts the user to decide whether to create a Git repository for the project.
12. If the user chooses to create a Git repository, it initializes a Git repository, adds all files, and makes the initial commit.
13. Finally, it displays a message indicating the completion of the project setup.

Feel free to customize the script according to your specific project requirements.
Please note that the script assumes you have Python and Git installed on your system.
