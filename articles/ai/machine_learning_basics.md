## Machine learning basics

There are fancier models that give more accurate predictions. But decision trees are easy to understand, and they are the basic building block for some of the best models in data science.

Below is the simplest possible decision tree.

<img width="200" alt="image" src="https://github.com/user-attachments/assets/2f279bde-9933-49fc-a4a6-d48c2e386eaa" />

It divides houses into only two categories. The predicted price for any house under consideration is the historical average price of houses in the same category.

In simple terms to improve the prediction we can add more decision trees to the decision making process.

### Using Pandas to Get Familiar With Your Data
The first step in any machine learning project is familiarize yourself with the data for which Pandas is the primary tool data scientists use.

`import pandas as pd`

The most important part of the Pandas library is the DataFrame. A DataFrame holds the type of data you might think of as a table.
This is similar to a sheet in Excel, or a table in a SQL database.

```
import pandas as pd

file_path = '../input/data-snapshot/data.csv'
data = pd.read_csv(melbourne_file_path)
data.describe()
```

### Choosing "Features"

The columns that are inputted into our model (and later used to make predictions) are called "features."
This is an important step for model building and training.

```
features = ['Rooms', 'Bathroom', 'Landsize', 'Lattitude', 'Longtitude']
X = data[features]
X.describe()
```

`X.describe()` method is an important method to check your data to know different statatistics of the dataset.
To interpret the min, 25%, 50%, 75% and max values, imagine sorting each column from lowest to highest value. 
The first (smallest) value is the min. 
If you go a quarter way through the list, you'll find a number that is bigger than 25% of the values and smaller than 75% of the values. 
That is the 25% value (pronounced "25th percentile"). The 50th and 75th percentiles are defined analogously, and the max is the largest number.

<img width="400" alt="image" src="https://github.com/user-attachments/assets/224770a3-73d5-4f7c-815a-a620e80f6b20" />

`X.dropna(axis=0)` will drop the missing values. `X.head()` will give top 5 records for X dataframe.

### Building Your Model
You will use the `scikit-learn` library to create your models. 
Scikit-learn is easily the most popular library for modeling the types of data typically stored in DataFrames.

**The steps to building and using a model are:**

* **Define:** What type of model will it be? A decision tree? Some other type of model? Some other parameters of the model type are specified too.
* **Fit:** Capture patterns from provided data. This is the heart of modeling.
* **Predict:** Just what it sounds like
* **Evaluate:** Determine how accurate the model's predictions are.

```
from sklearn.tree import DecisionTreeRegressor

# Define model. Specify a number for random_state to ensure same results each run
model = DecisionTreeRegressor(random_state=1)

# Fit model
model.fit(X, y) # X = dataframe that you created from features from a large set and y = data.Price a column to predict

# Predict
print(model.predict(X))

```

