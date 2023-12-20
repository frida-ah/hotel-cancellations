# Predict availability 

### Business question
Information is available over hotel bookings and a customer will indeed visit the hotel at the timeframe he booked or not. The focus of the exercise is to analyze the data, identify patterns and predict whether a customer will visit the hotel as planned, based on the characteristics of the booking. 


### Testing locally
A Python package has been created which includes all the code that was run to answer the questions. In order to be able to run the code, you may create a conda environment by running the following commands in the terminal:

```
cd <directory>
conda create -n "availability" python=3.9
conda activate availability
pip install -r requirements.txt
```

where `directory` needs to be filled in manually

### Project structure
The project follows the following structure

```bash
root
| README.md
| requirements.txt
| .gitignore
-- src
    -- notebooks
    | explore_data.ipynb : data exploration & analysis
    | modelling.ipynb : logistic regression model
    -- data
    | booking.csv : input raw dataset provided. Source: https://www.kaggle.com/datasets/youssefaboelwafa/hotel-booking-cancellation-prediction/data 
    | data_for_exploration : intermediate data saved after preprocessing
```

### Data exploration
Within the `explore_data` notebook, the data provided was explored. There are some comments every step of the way. Here are the main conclusions, which are also being asked of me.

### Modelling using a logistic regression model
I have chosen to apply a logistic regression on model on the dataset provided. The model predicts whether a customer will visit the hotel he booked (1) or not (0). The model is applied in the notebook `modelling.ipynb`.

#### Strenghts
The logistic regression has some benefits:
- It is easily to understand the modelling mechanism
- The threshold on determining 0 or 1 may be altered to fit business needs
- It is easy to productionize

#### Weaknesses
The weaknesses include:
- Highly dimensional feature space. The categorical variables are encoded into many dummies
- Might not generalise well on new unseen data

#### Parameter tuning
A logistic regression does not have many parameters to tune. Therefore, I have chosen to not apply any extra parameter tuning.

#### Cross-validation
I have chosen to apply a 5-fold cross-validation. In real life, it would be better to do it on a sample, which is the case now, my dataset is already a sample. I wanted to make sure the model doesn't overfit. The model fits on 5 different train sets and tests the results on a respective test set for that fold. The results of the CV are satisfactory.

#### Evaluation metric
The metric AUC-ROC was used an evaluation metric. I aimed at a score of >0.5 for this exercise. However, it would have been better to have a baseline model to compare to. 

#### Feature importance
The feature importance of the model, shows the most important features.
