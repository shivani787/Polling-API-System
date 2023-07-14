**Project Polling API**
This app is a Backend build for Polling System.

App provides you the APIs to interact with the database. Anyone can create questions with options and also add votes to it. Authentication/User identity is not needed, this is going to be a completely open application.

Following are the different APIs configured :

1.Get all questions and its options details:
  Type : GET
  URL : {hostedURL / localhost:8000}/questions
  
2.Get specific questions and its options details:
  Type : GET
  URL : {hostedURL / localhost:8000}/questions/:id
  
3.Create new question:
  Type : POST
  URL : {hostedURL / localhost:8000}/questions/create
  Form parameter : title : New question title
  
4.Add option to specific question:
  Type : POST
  URL : {hostedURL / localhost:8000}/questions/:id/options/create
  Form parameter : text : New option text
  
5.To delete a question and its options (it is not allowed to delete the question even if single option is having more than zero vote):
  Type : POST
  URL : {hostedURL / localhost:8000}/questions/:id/delete
  
6.To delete an option (it is not allowed to delete an option even if it is having more than zero vote):
  Type : POST
  URL : {hostedURL / localhost:8000}/options/:id/delete
  
7.To increment the count of vote for an option:
  Type : POST
  URL : {hostedURL / localhost:8000}/options/:id/add_vote
  
Hosted URL : https://polling-api-26u3.onrender.com(If you want to test it through hosted server/Ready to test, no need to install anything)

Locally hosted server : http://localhost:8000/(If you want to test it on your system after completing the below mentioned setup.)

**Prerequisites:**
1.Node should be installed on your Device
2.Mongo DB should be installed

**How to setup ?**
1.Download the zip file for this project from the repository or Click here to download !
2.Extract the file open in VS Code.
3.Run npm i this will install all dependencies.
4.Run nodemon index.js (if this command doesn't work, then nodemon is not installed globally in your system, please run npm i nodemon before running this command.)
5.The app will be live on port 8000, you can access API's now. To send the request please use POSTMAN or just install vs code extension RapidAPI Client.
Note : To run in local environment and link to your local mongo data base just uncomment the line 9 and comment line 3 and 10 in mongoose.js as the project is linked to cloud data base.

**Sample Responses:**
1.All Question details:
{
  "msg": "Question Fetched !",
  "response": [
    {
      "_id": "63ee699641cd1a4861adf518",
      "title": "Question 1",
      "options": [
        "63ee6a8841cd1a4861adf51b",
        "63ee6ad941cd1a4861adf521",
        "63ee6adf41cd1a4861adf526"
        ],
      "createdAt": "2023-02-16T17:36:22.311Z",
      "updatedAt": "2023-02-16T17:41:51.147Z",
      "__v": 3
    }
  ]
}

2.Create Question:
{
  "msg": "Question Created !",
  "response": {
    "title": "Question 1",
    "options": [],
    "_id": "63ee699641cd1a4861adf518",
    "createdAt": "2023-02-16T17:36:22.311Z",
    "updatedAt": "2023-02-16T17:36:22.311Z",
    "__v": 0
  }
}

**3.Create new option:
{
  "msg": "Option Created and linked successfully !",
  "response": {
    "_id": "63ee699641cd1a4861adf518",
    "title": "Question 1",
    "options": [
      {
        "question": "63ee699641cd1a4861adf518",
        "text": "Option 1",
        "votes": 0,
        "link_to_vote": "http://localhost:8000/options/63ee6a8841cd1a4861adf51b/add_vote",
        "_id": "63ee6a8841cd1a4861adf51b",
        "createdAt": "2023-02-16T17:40:24.177Z",
        "updatedAt": "2023-02-16T17:40:24.177Z",
        "__v": 0
      }
    ],
    "createdAt": "2023-02-16T17:36:22.311Z",
    "updatedAt": "2023-02-16T17:36:22.311Z",
    "__v": 0
  }
}
