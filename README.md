# 'bananapp': SpringBoot server & Google App Engine servlets + React.js client + Docker

An application for predicting banana age with image recognition, managing user accounts and their personal bananas - deployed on Docker.

The structure is as follows: <br>
main server: 'spring-and-react' <br>
image recognition servlets: 'bananapp-264116'<br>
client: 'bananapp-react'

The whole app consists of two RESTful backends and a frontend, which communicates with them through ajax calls.

### 'spring-and-react': (SpringBoot backend)
This is the server of bananapp, jar-packaged - a Spring Boot application.

The server utilizes Spring Security and Hibernate for login and registration, and calls the second Google App Engine server for image recognition purposes.

### 'bananapp-react': (React.js frontend)
This is the frontend of bananapp, a React.js app, communicating with the two servers by ajax calls.

### 'bananapp-264116': (Google App Engine backend)
This is the second server of bananapp, a war-packaged and servlet-based backend for redirecting the ajax calls. It receives the banana images from the frontend, passes them to the Google Cloud Platform (more specifically - the custom bananapp AutoML model at Google Cloud Vision), and answers with the response (utilizing Google image labeling, based on labels defined at bananapp model) - the age of a banana and the level of certainty.
<br>
<br>

## User flow:
#### 1 - Welcome page
![alt text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/welcome-page.png)
This is the initial page that anyone can access.

#### 2 - Instant image upload
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/instant-upload.png)
You can upload your banana image from disk (only jpg!) without authorizing.

### 3 - Waiting for results
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/waiting.png)
The frontend sends a request to the second server ('bananapp-264116'), which gets the image labeling from custom AutoML model via Google Cloud Vision.

#### 4 - Image recognition results
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/results.png)
The results for an instant processing (as opposed to an authorized processing) are not saved to a database.

#### 5 - Register
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/register.png)
If you want to be able to store your bananas with predictions, you have to create an account.

#### 6 - Login
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/login.png)
To access your personal page you have to log-in.

#### 7 - Authorized user
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/auth.png)
After authorizing, bananas with their predicted ages are being saved to your own database.

#### 8 - User's personal bananas
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/personal-bananas.png)
...and you can access your personal bananas anytime.

#### 9 - Delete personal banana
![alt-text](https://raw.githubusercontent.com/k-wasilewski/bananas/master/screenshots/del-img.png)
You also can delete unwanted bananas.


