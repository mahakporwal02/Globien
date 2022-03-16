## Blog single-page application written on MEVN stack (MongoDB, Express, Vue.js, Node.js)


### Functions:

* Register a new user
* Login using generated JWT token (expires in 1 week)
* Get list of all posts in blog saved to MongoDB
* Pagination (8 posts per page)
* Create a new post
* You can edit or delete post only if you are it's author
* You must be logged in to see post's details
* User's profile
* You can add personal info or edit it

Application is based on Vue.js framework called [Vuetify.js](https://vuetifyjs.com/en/)

### Installation

* Frontend
```
cd vue-blog/front
npm run start
 ```

* Backend
```
cd vue-blog
npm run start
 ```
* Add .env file 
```
NODE_ENV = development
PORT = 4050
PROD_MONGODB = mongodb://localhost:27017/blog
MONGOOSE_DEBUG = true
SECRET = 29fe02c1-7de9-493a-b3c5-d33e56555a98
```
