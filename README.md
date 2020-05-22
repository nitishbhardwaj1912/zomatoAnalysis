<p align="center">
  <img width="400" height="250" src="https://static-news.moneycontrol.com/static-mcnews/2019/02/Zomato_company_logo-770x433.jpg" alt="Zomato">
  </p>
  
<p align="center">
Image reference: [1] 
</p>


# Analysis on Zomato 
This repository contains objects related to the machine learning analysis on Zomato Restaurant's data.

## About Dataset

<p align="center">
  <img src="https://economictimes.indiatimes.com/img/68794106/Master.jpg" alt="Zomato Map">
  </p>
  
<p align="center">
Image reference: [2] 
</p>

The dataset contains the details of restaurants in Bengaluru, India. This dataset is based on Zomato, an Indian restaurant search and discovery service. The dataset contains 51717 rows and 17 columns. This information was fetched based on the shape of the dataset. There are various anomalies in the data like columns containing null values, mismatched information, trailing spaces, and invalid characters etc.

There are only one integer based attribute i.e. votes and all other attributes are object type.

The description of the attributes is given below:

* **url** is the url of each restaurant. It is a unique identifier in the dataset.

* **address** is the physical address of the restaurant.

* **name** is the name of the restaurants. They are repeated in the dataset as one location can have multiple branches of the same restaurant.

* **online_order** column has the values of Yes and No. It signifies if the restaurant accepts the online order or not.

* **book_table** also has the value of Yes and No. The value represents if the restaurant has an option to book the table.

* **rate** is the average rate of the restaurant out of 5.

* **votes** signifies the number of votes counted for the rating of the restaurant.

* **phone** column contains the phone number of the restaurant.

* **location** is the physical location of the restaurant.

* **rest_type** explains the type of the restaurant like casual dining, quick bites etc.

* **dish_liked** contains a list of dishes liked at the restaurant.

* **cuisines** is the list of cuisines offered at the restaurant.

* **Approx_cost(for two people)** contains the approximate cost of food at the restaurant for two people.

* **reviews_list** contains the reviews given by the customer for the restaurant. It also has the individual rate given by the customer.

* **menu_item** contains the list of menu items from the menu list of the restaurant.

* **listed_in(type)** is the type of meals or food types provided at the restaurant. The unique values are: 'Buffet', 'Cafes', 'Delivery', 'Desserts', 'Dine-out', 'Drinks & nightlife', 'Pubs and bars'.

* **listed_in(city)** signifies the location where the restaurant is located.

## Business Problem

Perform a detailed Exploratory Data Analysis(EDA) of the Zomato dataset and predict the cost of having food for two people considering the location, rating, restaurant type and cuisine options of the restaurant.

## Research Analysis Steps:
Six major steps of this research are described in this section. However, for the better understanding of each step, every section is divided into sub-questions and each of them are explained in detail.

1. **Exploratory Data Analysis:** A detailed EDA is performed on the dataset.
	- There are 17 columns and 51717 rows in the dataset.
	-   All the columns are objects type except votes which is int64 type.
	-   There are null values present in the dataset.
	-   Distribution of North Indian Food is more in the dataset though the data is based on Bangalore which is located in South India. However, the cuisines column contains repeated values as comma separated values. For right decisions, it should be cleaned.
	-   It is noticed that more restaurant data is provided from the location of BTM. The second largest location where many restaurants are present is Koramangla.
	-   Most of the restaurants at Bangalore accepts the online order.
	-   Based on the distribution of ratings of the restaurants, it can be observed that most of the restaurants in Bangalore have a rating between 3.5 to 4.
	-   Most of the restaurants at Bangalore are delivery type. The least type of restaurants is Pubs and Bars, Buffet and Drinks & Nightlife.

2. **Cleaning:** In this section, the data is cleaned based on the observation and exploration of data. The analysis for cleaning is given below:
	-   Drop the irrelevant columns after taking their backup.
	-   URL and Phone are dropped as they have no relevance in the data.
	-   Address column is dropped as the exploration of data doesn't need the specific address of the restaurant.
	-   Location is dropped as it is having reduntant data for listed_in(city). Based on the graphs plotted above, it is observed that listed_in(city) is having enough data to make the decisions for the models.
	-   Menu_Item is dropped as it is not required to solve the business problem.
	-   Review_List is dropped as we do not need the description of customer reviews to address the problem statement. Rate column is enough for analysis.
	-   Rename the columns i.e. Give them a meaningful name
	-   Verify if there are any null values in the dataset. If they are present remove them.
	-   Cost values in the dataset are object type. The column was also observed to have "," (comma) in the numeric values. Hence, the comma was removed and the values were converted into int64.
	-   Rate column has values with '/5'. It signifies that the rating is out of fie. We need to clean the column for further processing. Hence, '/5' is removed from the column. There are also 'NEW' values which might signify that the restaurant is new and no rating has been given by the customer yet. Hence, these are replaced by 0 for easier reference.

3. **Model Creation and Training:** In this process, five models are trained on the selected features. It is a supervised regression task. The five models that are chosen considering the business problem, available features and the distribution of values in the dataset are: 
	-  Decision Tree
	- Random Forest
	- k-nearest neighbor
	-  Neural Network (Multi-Layer Perceptron)
	-  SVM
	
4. **Model Evaluation:** Evaluation metrics are used to evaluate the model. Following metrics have been analysed in this process: 
	- Mean Squared Error (MSE)
	- Root Mean Squared Error (RMSE)
	- Mean Absolute Error (MAE)
	- R Squared (R²)
	- Mean Absolute Percentage Error (MAPE)
	
	After analyzing the data,  **MSE and R²**  are selected as the evaluation metric over the other metrics. The analysis is given in the notebook.

5. **Model Testing with real data:** In this process, the model is given the  testing data and its performance is validated. A bar graph is plotted to evaluate the performance of the model.

6. **Scope for the Model Improvement:** In this section, GRIDSEARCHCV is used for hyperparameter optimization and Relief feature is implemented.

## References:
[1]_Static-news.moneycontrol.com_, 2019. [Online]. Available: https://static-news.moneycontrol.com/static-mcnews/2019/02/Zomato_company_logo-770x433.jpg. [Accessed: 22- Jun- 2019].

[2]"So, what is urban India eating? Zomato just gave you every detail", _The Economic Times_, 2019. [Online]. Available: https://economictimes.indiatimes.com/industry/cons-products/food/so-what-does-urban-india-like-to-eat-zomato-just-gave-you-every-detail/articleshow/68793746.cms. [Accessed: 22- Jun- 2019].

[3] "Zomato", En.wikipedia.org, 2019. [Online]. Available:  [https://en.wikipedia.org/wiki/Zomato](https://en.wikipedia.org/wiki/Zomato). [Accessed: 22- Jun- 2019].

[4]"API Reference — scikit-learn 0.21.2 documentation", Scikit-learn.org, 2019. [Online]. Available:  [https://scikit-learn.org/stable/modules/classes.html](https://scikit-learn.org/stable/modules/classes.html). [Accessed: 28- Jun- 2019].

[5] Evaluation Metrics in Regression Models - Regression | Coursera", Coursera, 2019. [Online]. Available:  [https://www.coursera.org/lecture/machine-learning-with-python/evaluation-metrics-in-regression-models-5SxtZ](https://www.coursera.org/lecture/machine-learning-with-python/evaluation-metrics-in-regression-models-5SxtZ)?. [Accessed: 29- Jun- 2019]."

[6] "How to select the Right Evaluation Metric for Machine Learning Models: Part 1 Regression Metrics", Towards Data Science, 2019. [Online]. Available:  [https://towardsdatascience.com/how-to-select-the-right-evaluation-metric-for-machine-learning-models-part-1-regrression-metrics-3606e25beae0](https://towardsdatascience.com/how-to-select-the-right-evaluation-metric-for-machine-learning-models-part-1-regrression-metrics-3606e25beae0). [Accessed: 30- Jun- 2019].

[7] "MAE and RMSE — Which Metric is Better? - Human in a Machine World - Medium", Medium, 2019. [Online]. Available:  [https://medium.com/human-in-a-machine-world/mae-and-rmse-which-metric-is-better-e60ac3bde13d](https://medium.com/human-in-a-machine-world/mae-and-rmse-which-metric-is-better-e60ac3bde13d). [Accessed: 30- Jun- 2019].

[8] "Choosing the Right Metric for Evaluating Machine Learning Models — Part 1", Medium, 2019. [Online]. Available:  [https://medium.com/usf-msds/choosing-the-right-metric-for-machine-learning-models-part-1-a99d7d7414e4](https://medium.com/usf-msds/choosing-the-right-metric-for-machine-learning-models-part-1-a99d7d7414e4). [Accessed: 30- Jun- 2019].

[9] "Coefficient of Determination: Definition", Stattrek.com, 2019. [Online]. Available:  [https://stattrek.com/statistics/dictionary.aspx?definition=coefficient_of_determination](https://stattrek.com/statistics/dictionary.aspx?definition=coefficient_of_determination). [Accessed: 30- Jun- 2019].

[10] F. Provost and T. Fawcett, Data science for business. O’Reilly, 2013, pp. 111-138.

[11] J. Frost, "How To Interpret R-squared in Regression Analysis - Statistics By Jim", Statistics By Jim, 2019. [Online]. Available:  [https://statisticsbyjim.com/regression/interpret-r-squared-regression/](https://statisticsbyjim.com/regression/interpret-r-squared-regression/). [Accessed: 02- Jul- 2019].

[12] "Documentation scikit-learn: machine learning in Python — scikit-learn 0.21.2 documentation", Scikit-learn.org, 2019. [Online]. Available:  [https://scikit-learn.org/stable/documentation.html](https://scikit-learn.org/stable/documentation.html). [Accessed: 02- Jul- 2019].

[13] "Hyperparameter Tuning the Random Forest in Python - Towards Data Science", Medium, 2019. [Online]. Available:  [https://towardsdatascience.com/hyperparameter-tuning-the-random-forest-in-python-using-scikit-learn-28d2aa77dd74](https://towardsdatascience.com/hyperparameter-tuning-the-random-forest-in-python-using-scikit-learn-28d2aa77dd74). [Accessed: 02- Jul- 2019].

[14] "Finding the best restaurants in Bangalore | Kaggle", Kaggle.com, 2019. [Online]. Available:  [https://www.kaggle.com/parthsharma5795/finding-the-best-restaurants-in-bangalore](https://www.kaggle.com/parthsharma5795/finding-the-best-restaurants-in-bangalore). [Accessed: 01- Jul- 2019].
