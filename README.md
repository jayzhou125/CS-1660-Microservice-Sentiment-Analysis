# CS-1660-Microservice-Sentiment-Analysis Optional Lab

The optional lab is for the CS-1660 extra credit. 

This practice is meant to get familiar with Microservices using Docker. 

The Sentiment_Analysis application is credited to **Rinor Maloku**.

Original Repository: https://github.com/rinormaloku/k8s-mastery

## There's total three application to use for this practice. 

##### 1. sa-fronted
##### 2. sa-web-app
##### 3. sa-logic




## For the frontend, you need to set up React for your local Development.
After setting up the environment:

```
npm start
```

To run the React Application. 
Go to ```localhost:3000``` to see the actual applicaiton. 

```
npm run build
```

Will generate the static files for the front end. 

Move the static files in ```build/``` folder to the ```[your_nginx_installation_dir]/html``` 
That way the **Nginx** server will serve our customed frontend code. 

## For the web-app, you need to set up JDK8 and Maven. 
After setting up the environment:
Remember to set up the property ```sa.logic.api.url```to your desired localhost port. 
Run the web-app as follow:

```
java -jar sentiment-analysis-web-0.0.1-SNAPSHOT.jar 
     --sa.logic.api.url=WHAT.IS.THE.SA.LOGIC.API.URL
```
     
## For the Logic, make sure that you have Python installed. 
Run the sa-logic as follow：

```
python sentiment_analysis.py
```

## At this point, you should be able to run the application by running all three commands. 


# From this point on, we will begin build our microsevices using Docker.

BUILD THE FRONT END USING DOCKER
1. start with the base Nginxx image
2. Copy the sa-frontend/build directory to the containers nginx/html directory.

Converted into a Dockerfile it looks like:

```
FROM nginx
COPY build /usr/share/nginx/html
```

Then build the image:
```
docker build -f Dockerfile -t $DOCKER_USER_ID/sentiment-analysis-frontend .
```

Then push it to the Docker Hub so anyone can use:
```
docker push $DOCKER_USER_ID/sentiment-analysis-frontend
```
 
## Do the same thing for the other two applications 
## And you will have your all container images

## Since I already did all these，you can try and pull the images that I created just to see how it works. 
## To Demo:
#####1. run the sa-logic on port number 5000:

```
docker run -d -p 5000:5000 jiz156/sentiment-analysis-logic
```


#####2. run the sa-web-app on port number 8080:
**Make sure you change the URL to your container_IP.**
If you are not sure what the container IP is, use the following command: 
```
docker inspect -f container_name_or_id
```

```
docker run -d -p 8080:8080 -e SA_LOGIC_API_URL='http://172.17.0.2:5000' jiz156/sentiment-analysis-web-app
```

If you are not sure what the container IP is, use the following command: 
```
docker inspect -f container_name_or_id
```


#####3. lastly, run the sa-frontend use at port 80:

```
docker run -d -p 80:80 jiz156/sentiment-analysis-frontend
```

## We are done. Open your browser on ```localhost:80``` to try it out!




         
