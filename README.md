# ai-programming-foundations-project
This my first project in the capstone course of Udacity's Master's Degree in AI (https://www.udacity.com/masters-artificial-intelligence). 

## Overview
In this project, we build a pipeline for cleaning and exploring a dataset on Airbnb listings in NYC (https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data). 
Among others, the dataset contains information on neighbourhood, room type, reviews, and price, and we are going to explore the relations between these types of information. 
More precisely, we are interested in if and how the price depends on the neighbourhood, room type, and review frequency.
After importing modules and loading the data, we first perform a cleaning of the data. We then run an exploratory data analysis and generate some insightful visualizations, before summarizing our findings.

## How to run the project
The main component of the project is the Jupyter notebook 'data_workflow.ipynb'.
When checking out this repository, the dataset file 'AB_NYC_2019.csv' is already included.
In addition, the repository contains a 'requirements.txt' file with all required dependencies, which was generated via the command
	
	pip freeze > requirements.txt
	
It can be used e.g. in a virtual Anaconda environement by opening an Anaconda prompt window in the project directory and running the following commands:

	conda create -n env_msai_cap_1 python
	conda activate env_msai_cap_1
	pip install -r requirements.txt
	python -m ipykernel install --user --name=env_msai_cap_1
	jupyter notebook
	
The last command opens a Jupyter GUI, where one needs to click on the notebook 'data_workflow.ipynb' and then click on Run... -> Run All Cells