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

## Reflection Questions

### Bias and Data Quality
The overall quality of the dataset is quite good. 
The deductive imputation applied on the NA values in the reviews_per_month variable should not lead to any bias, as it applied the NA with factually correct values. 
The truncation at the 0.5% and 99.5% quantile of price andreviews_per_month should have little impact on the descriptive statistics (quartiles) of the relationship between price and categorial variables. 
It might have an impact on the correlation between price and reviews_per_month, but this is an intended impact, as outliers can distort the correlation, 
and we are interested in the relationship for the bulk of the data rather than outliers.

### Future Integration: Machine Learning Workflow
If the dataset would be prepared as input data for a machine learning model, some additional steps would be in order.
- First, both numerical variables price and reviews_per_month are quite skewed in there distribution, so a logarithmic transformation could make sense for these.
- Second, the categorial variables neighbourhood_group and room_type need to be transformed to a format that can be processed by the model, e.g. via one-hot encoding.
- Third, the dataset needs to be split into a training set and a test set.

### Future Integration: Neural Network Preparation
If the dataset would be prepared as input data for a neural network, some additional steps would be in order.
- In order to facilitate training the two numerical variables need to be rescaled to zero mean and unit variance
- Again, the categorial variables need to be encoded e.g. via one-hot encoding
- NA values need to be cleaned for neural network training, which is already ensured in our workflow
- If the last_review variable (datetime) was used for training, it needed to be transformed into a numerical variables, e.g. via pd.to_timedelta(df.pd.to_timedelta(df.date).dt.total_seconds()).dt.total_seconds()
- Again, the dataset needs to be split into a training set and a test set.

### Agentic Automation Potential
- An agent could automatically detects outlier thresholds using statistical tests, and call the clean_outliers method
- An agent could automatically detects NA values, and call the drop_na_values method
- Automation of the clean_review_columns is a bit more tricky (on generic data), as deductive imputation requires thorough analysis of data and deduction of correct values is hard to generalize in prompt instructions