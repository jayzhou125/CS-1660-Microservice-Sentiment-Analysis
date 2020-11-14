# CS-1660-Microservice-Sentiment-Analysis Optional Lab

This practice is meant to get familiar with Microservices using Docker. 

The Sentiment_Analysis application is credited to **Rinor Maloku**.

Original Repository: https://github.com/rinormaloku/k8s-mastery

# Environment Set-UP
## There's total three application to use for this practice. 

##### 1. sa-fronted
##### 2. sa-web-app
##### 3. sa-logic

# For the frontend, you need to set up React for your local Development.
After setting up the environment:

```npm start```

To run the React Application. 
Go to ```localhost:3000``` to see the actual applicaiton. 

```npm run build```

Will generate the static files for the front end that we will use for the **Nginx** server. 

# For the web-app, you need to set up JDK8 and Maven. 
After setting up the environment:
Remember to set up the property ```sa.logic.api.url```to the correct one. 
Run the web-app as follow:

```java -jar sentiment-analysis-web-0.0.1-SNAPSHOT.jar 
     --sa.logic.api.url=WHAT.IS.THE.SA.LOGIC.API.URL```
     
# For the Logic, make sure that you have Python installed. 


         
