# Employee Turnover Prediction With Deep Learning

_Captured: 2018-01-15 at 20:51 from [dzone.com](https://dzone.com/articles/employee-turnover-prediction-with-deep-learning?edition=352124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-15)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

Mexico ranks eighth in the world for employee turnover, with an average turnover rate of about 17% each year -- and some industries, like food service, getting up to 50%. According to a [study](https://www.zanebenefits.com/blog/bid/312123/employee-retention-the-real-cost-of-losing-an-employee) from Catalyst, the cost of replacing an employee is around 50% to 75% of the employee's annual salary, on average. Considering a mid-level position with a monthly salary of 20,000 pesos, the total cost of replacing this employee would be around 140,000 pesos. On average, it takes around 50 days to replace an employee, and the costs incurred due to productivity loss will keep adding up. For a big company like everis with over 20,000 employees, considering a turnover rate of 15% and an average salary of $15,000 pesos, the total annual cost of turnover would rise up to at least 270 million pesos.

In this article, we provide details about a neural network model that is capable of identifying employee candidates with a high risk of turnover, accomplishing this task with around 96% accuracy.

## **Methodology**

We used the dataset [HR Employee Attrition and Performance](https://community.watsonanalytics.com/wp-content/uploads/2015/03/WA_Fn-UseC_-HR-Employee-Attrition.xlsx), a fictional dataset created by IBM data scientists. It contains 1,470 rows of employee historical data.

An exploratory data analysis was done to identify features that had the highest correlation with employee turnover. These are the most important features we found:

    * Age
    * Distance from home
    * Overtime
    * Education
    * Marital status
    * Number of companies worked at
    * Total working years
    * Monthly income

These features were used to train the model to predict turnover risk. The dataset already contained a feature called _attrition_, which indicated whether the employee left the position and had to be replaced. This feature was one-hot encoded (showed after splitting data into training and testing sets) and was used as the target for the neural network's predictions. Here are the helper functions used for one-hot encoding:
    
    
        for i in range(len(one_hot)):
    
    
            inverse.append(label_encoder.inverse_transform([np.argmax(one_hot[i, :])])[0])

Due to the unbalanced nature of the dataset (employees labeled with turnover represented around 16% of the population, or 237 of 1,470 cases), an upsample technique was used to repeat turnover cases -- so the data had 1,233 cases with turnover and 1,233 cases without turnover.

Upsampling the dataset avoids a situation where the model learns to predict "no turnover" every time; in this case it would achieve around 84% of accuracy by doing so (this accuracy serves as our baseline).
    
    
    data_empleados_upsampled = pd.concat([data_empleados_majority, data_empleados_minority_upsampled])
    
    
    data_empleados_upsampled = data_empleados_upsampled.sample(frac=1)

Next, a `StandardScaler` was used to normalize data to ranges from -1 to 1 to avoid outliers to affect the predictions in a disproportionate way.
    
    
        def add_scaler(self, scaler, name):
    
    
        scaled = standard_scaler.fit_transform(data.astype('int64').values.reshape(-1, 1))
    
    
    def scale_append(data, scalers, name):
    
    
        scaled, scaler = scale_and_generate_scaler(data[name])
    
    
        data_empleados_upsampled[var], scalers_empleados = scale_append(data_empleados_upsampled, scalers_empleados, var)

After having the data prepared, it was randomly split into training data (80%) and testing data (20%), using a random seed for reproducibility.
    
    
    X_train, X_test = train_test_split(data_empleados_upsampled, test_size=0.2, random_state=RANDOM_SEED)
    
    
    X_train = X_train.drop(['Attrition_Num', 'Attrition', 'BusinessTravel', 'OverTime', 'MaritalStatus', 'YearsAtCompany'], axis=1)
    
    
    X_test = X_test.drop(['Attrition_Num', 'Attrition', 'BusinessTravel', 'OverTime', 'MaritalStatus','YearsAtCompany'], axis=1)
    
    
    y_train_hot, label_encoder = one_hot_values(y_train)
    
    
    y_test_hot, label_encoder_test = one_hot_values(y_test)

Then, the neural network was built using Keras. Its architecture is the following:
    
    
    model.add(Dense(512, activation='relu', input_dim=input_d))
    
    
    model.add(Dense(128, activation='relu', input_dim=input_d))
    
    
    model.add(Dense(64, activation='relu'))
    
    
    sgd = SGD(lr=0.01, decay=1e-6, momentum=0.9, nesterov=True)

It's a simple three-layer neural network, with two neurons at the last layer to predict the correct class based on the one-hot encoded message used as the target for the model; no attrition = [0,1] and attrition = [0,1].

A stochastic gradient descent optimizer was used with a learning rate of 0.01, a batch size of 64, and a loss function of `categorical_crossentropy`. It was trained for 200 epochs, achieving a validation accuracy of 96.15% (compared to baseline 84% for always predict turnover).

The output for each prediction is an array of size 2; the elements of this array sum up to 1. For extracting the predicted class, the highest element from the array is taken. If the first element is larger, the predicted class has no attrition. Similarly, the predicted class has attrition if the second element is larger than the first. The function `inverse_one_hot()` is used to get the predicted class from one-hot encoded model predictions. Here's an example:

Here's an example of how to perform prediction on a custom profile; let's say, a potential candidate for a job:
    
    
    perfil = ['26', '2', '1', '1', '1', '1', '2500', '1', '1', '2', '2', '6', '1', '2']
    
    
        scaled_input.append(scalers_empleados.scalers[data_vars[i]].transform(perfil[i]))
    
    
    scaled_input = np.array(scaled_input).flatten().reshape(1,len(data_vars))
    
    
    res = [inverse_one_hot(label_encoder,np.array([list(pred[i])])) for i in range(len(pred))]
    
    
    print({'pred':str(res[0])})

A similar neural network was built to predict `YearsAtCompany`, a variable that corresponds to the total number of years the employee is expected to last in the company. The architecture is the same, with the exception of the last layer, which has five neurons instead of two to predict 0, 1, 2, 4 or 10 years.

It was trained for 350 epochs and yielded an accuracy of 82.52% (compared to baseline 20% for a random guess, a 1/5 chance; or 22% for always predicting four years).

Here's a function to get insights into the model's performance:
    
    
        y_train_inv = [inverse_one_hot(label_encoder_train,np.array([list(y_train_hot[i])])) for i in range(len(y_train_hot))]
    
    
        y_train_inv = np.array(y_train_inv).flatten()
    
    
        preds_inv = [inverse_one_hot(label_encoder_train,np.array([list(preds[i])])) for i in range(len(preds))]
    
    
        for i in range(len(preds_inv)):
    
    
            if preds_inv[i] == y_train_inv[i]:
    
    
            elif (preds_inv[i]) < (y_train_inv[i]):
    
    
            elif (preds_inv[i]) > (y_train_inv[i]):
    
    
            errors.append(((preds_inv[i]) - (y_train_inv[i])))
    
    
        print("correct: {}, over {}, under {}, accuracy {}, mse {}".format(correct, over, under, round(correct/len(preds_inv),3), np.round(np.array(np.power(errors,2)).mean(),3)))
    
    
        print("errors:",pd.Series(np.array([abs(i) for i in errors if i != 0])).describe())
    
    
        print(sns.boxplot(np.array([abs(i) for i in errors if i != 0])))

## **Implementation and Results**

A front-end was designed for the user to input characteristics of a candidate, and both models will yield a result: first identifying if the candidate has a risk of turnover and then predicting how many years the candidate would be predicted to stay at the potential position..

![Image title](https://dzone.com/storage/temp/7789908-interface-turnover.png)

A graph is also created to compare the normalized values of the candidates' characteristics with the average value of all the employees in the dataset. This is used to see which characteristics differ the most from the normal values.

![Image title](https://dzone.com/storage/temp/7789910-results-turnover.png)

## **Conclusion**

There is still work to be done. It would be great to test these models with _real_ data coming from a Mexican company. Also, the features that have a higher correlation with turnover risk may differ from dataset to dataset. Additionally, other features could be added in, like monthly grocery and housing expenses, as well as a more detailed analysis based on industry and the position for which the candidate applies.

The expected years at company prediction could also be a little more specific, especially for the first two years. Right now, the model can only predict one year or another, but maybe it would be worthwhile to predict months instead of years to differentiate candidates using more information.

Still, recruiters could greatly benefit from these kinds of tools; they can have objective information at hand to make more informed decisions, and if the candidate turns out to have a high risk of turnover, at least it's something that can be discussed directly with the candidate to negotiate how both parties can benefit. With these tools and novel strategies to combat turnover, companies around the world could reduce their turnover significantly, potentially increasing their income by millions.

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.
