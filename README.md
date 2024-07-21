# Capstone Project: A car dealership's review portal website

Project Details: A national car dealership with local branches spread across the United States recently conducted a market survey. One of the suggestions that emerged from the survey was that customers would find it beneficial if they could access a central database of dealership reviews across the country.

In this project, I have build a website that allows new and existing customers to look up different branches by state and look at customer reviews of the various branches. Customers will be able to create an account and add their review for any of the branches. By these functions, the management hopes this will bring transparency to the system and also increase the trust customers have in the dealership.

This Project was divided in 4 parts
1. Adding user management which includes user registration, login and logout along with session management to the Django application with the react front end.
2. Created back-end services in JavaScript that connect with MongoDB. In addition, containerized MongoDB and express server to provide the API endpoints, accessing data about the dealership and their reviews. Also, deployed a sentiment analyzer microservice written with Python, flask and natural language toolkit or NLTK using the IBM cloud code engine.
3. This part was all about adding dynamic react pages to get dealership details, get reviews of the dealership for all end users and add reviews to the dealership for registered users. I have aimed to create user friendly and aesthetic fronted pages to present these services to the end users.
4. Implemented continuous integration and continuous delivery or CI/CD with GitHub workflow for linting. Before moving ahead, ensured that Exprsmongo server is running on Docker and that the sentiment analyzer microservice is accessible. Then provided application with the ability to run in a container.

The Solution architecture

1. The user interacts with the "Dealerships Website", a Django website, through a web browser.

2. The Django application provides the following microservices for the end user:

- get_cars/ - To get the list of cars from
- get_dealers/ - To get the list of dealers
- get_dealers/:state - To get dealers by state
- dealer/:id - To get dealer by id
- review/dealer/:id - To get reviews specific to a dealer
- add_review/ - To post review about a dealer

3. The Django application uses SQLite database to store the Car Make and the Car Model data.

4. The "Dealerships and Reviews Service" is an Express Mongo service running in a Docker container. It provides the following services::

- /fetchDealers - To fetch the dealers
- /fetchDealer/:id - To fetch the dealer by id
- fetchReviews - To fetch all the reviews
- fetchReview/dealer/:id - To fetch reviews for a dealer by id
- /insertReview - To insert a review

5. "Dealerships Website" interacts with the "Dealership and Reviews Service" through the "Django Proxy Service" contained within the Django Application.

6. The "Sentiment Analyzer Service" is deployed on IBM Cloud Code Engine, it provides the following service:

- /analyze/:text - To analyze the sentiment of the text passed. It returns positive, negative or neutral.

7.The "Dealerships Website" consumes the "Sentiment Analyzer Service" to analyze the sentiments of the reviews through the Django Proxy contained within the Django application.

