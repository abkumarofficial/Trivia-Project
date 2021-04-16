# Full Stack Trivia API Backend
This project is a game where users can test their knowledge answering trivia questions. The task for the project was to create an API and test suite for implementing the following functionality:

    1.Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer.
    2.Delete questions.
    3.Add questions and require that they include question and answer text.
    4.Search for questions based on a text query string.
    5.Play the quiz game, randomizing either all questions or within a specific category.

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Environment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organized. Instructions for setting up a virtual environment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by navigating to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

## Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

## Running the server

From within the `backend` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application. 

## Tasks

One note before you delve into your tasks: for each endpoint you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior. 

1. Use Flask-CORS to enable cross-domain requests and set response headers. 
2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories. 
3. Create an endpoint to handle GET requests for all available categories. 
4. Create an endpoint to DELETE question using a question ID. 
5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score. 
6. Create a POST endpoint to get questions based on category. 
7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question. 
8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions. 
9. Create error handlers for all expected errors including 400, 404, 422 and 500. 

REVIEW_COMMENT
```
This README is missing documentation of your endpoints. Below is an example for your endpoint to get all categories. Please use it as a reference for creating your documentation and resubmit your code. 

Endpoints
GET '/categories'
GET ...
POST ...
DELETE ...

GET '/categories'
- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Arguments: None
- Returns: An object with a single key, categories, that contains a object of id: category_string key:value pairs. 
{'1' : "Science",
'2' : "Art",
'3' : "Geography",
'4' : "History",
'5' : "Entertainment",
'6' : "Sports"}

```


## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```

## API Reference
## Getting Started

    Base URL: Currently this application is only hosted locally. The backend is hosted at http://127.0.0.1:5000/
    Authentication: This version does not require authentication or API keys.
## Error Handling

Errors are returned as JSON in the following format:

{
    "success": False,
    "error": 404,
    "message": "resource not found"
}

The API will return three types of errors:

    400 – bad request
    404 – resource not found
    422 – unprocessable

## Endpoints

## GET /categories

General: Returns a list categories.

Sample: curl http://127.0.0.1:5000/categories

{
   "categories":[
      {
         "categories":"Math"
      },
      {
         "categories":"Science"
      },
      {
         "categories":"Computer Science"
      },
      {
         "categories":"Biology"
      }
   ],
   "success":true
}

## GET /questions

    General:
        Returns a list questions.
        Results are paginated in groups of 10.
        Also returns list of categories and total number of questions and current category set to null

   Sample: curl http://127.0.0.1:5000/questions

{
   "categories":{
      "1":"Math",
      "2":"Science",
      "3":"Computer Science",
      "4":"Biology"
   },
   "current_category":null,
   "questions":[
      {
         "answer":"2",
         "category":"1",
         "difficulty":10,
         "id":3,
         "question":"1+1"
      },
      {
         "answer":"5",
         "category":"1",
         "difficulty":10,
         "id":4,
         "question":"1+4"
      },
      {
         "answer":"6",
         "category":"1",
         "difficulty":10,
         "id":5,
         "question":"1+5"
      },
      {
         "answer":"8",
         "category":"1",
         "difficulty":10,
         "id":7,
         "question":"1+7"
      },
      {
         "answer":"9",
         "category":"1",
         "difficulty":10,
         "id":8,
         "question":"1+8"
      },
      {
         "answer":"11",
         "category":"1",
         "difficulty":10,
         "id":9,
         "question":"1+10"
      },
      {
         "answer":"12",
         "category":"1",
         "difficulty":10,
         "id":10,
         "question":"1+11"
      },
      {
         "answer":"13",
         "category":"1",
         "difficulty":10,
         "id":11,
         "question":"1+12"
      },
      {
         "answer":"15",
         "category":"1",
         "difficulty":10,
         "id":13,
         "question":"1+14"
      },
      {
         "answer":"10",
         "category":"1",
         "difficulty":10,
         "id":15,
         "question":"5 + 5"
      }
   ],
   "success":true,
   "total_questions":14
}

## DELETE /questions/<int:id>

    General:
        Deletes a question by id using url parameters.
        Returns id of deleted question upon success.

    Sample: curl http://127.0.0.1:5000/questions/6 -X DELETE

{
  "id": 1, 
  "success": true
}

## POST /questions

This endpoint either creates a new question

    If no search term is included in request:

    General:
        Creates a new question using JSON request parameters.
        Returns JSON object with newly created question, as well as paginated questions.

   Sample: curl -X POST -d {"question":"new question of math","answer":"maths","difficulty":1,"category":1} -H 'Content-Type:application/json' http://127.0.0.1:5000/questions

{
  "currentCategory": null, 
  "questions": [
    {
      "answer": "3", 
      "category": "1", 
      "difficulty": 2, 
      "id": 2, 
      "question": "1+2"
    }, 
    {
      "answer": "4", 
      "category": "1", 
      "difficulty": 4, 
      "id": 3, 
      "question": "1+3"
    }, 
    {
      "answer": "7", 
      "category": "1", 
      "difficulty": 5, 
      "id": 4, 
      "question": "1+6"
    }, 
    {
      "answer": "mathematics", 
      "category": "1", 
      "difficulty": 4, 
      "id": 5, 
      "question": "what is math"
    }, 
    {
      "answer": "new", 
      "category": "1", 
      "difficulty": 1, 
      "id": 6, 
      "question": "new math question"
    }, 
    {
      "answer": "mathematics", 
      "category": "1", 
      "difficulty": 5, 
      "id": 7, 
      "question": "math full form"
    }, 
    {
      "answer": "a2 + b2  = c2", 
      "category": "1", 
      "difficulty": 5, 
      "id": 8, 
      "question": "pythogoras theorem"
    }, 
    {
      "answer": "triangle", 
      "category": "1", 
      "difficulty": 5, 
      "id": 9, 
      "question": "pythogoras theorem based on"
    }, 
    {
      "answer": "ramanujan", 
      "category": "1", 
      "difficulty": 5, 
      "id": 10, 
      "question": "rama_____"
    }, 
    {
      "answer": "eleventh", 
      "category": "1", 
      "difficulty": 1, 
      "id": 11, 
      "question": "eleventh question"
    }, 
    {
      "answer": "maths", 
      "category": "1", 
      "difficulty": 1, 
      "id": 12, 
      "question": "new question of math"
    }
  ], 
  "success": true, 
  "totalQuestions": 11
}

## POST /questions/search

    General:
        Searches for questions using search term in JSON request parameters.
        Returns JSON object with matching questions.

   Sample: curl -X POST -d {"searchTerm":"pythogoras"} -H 'Content-Type:application/json' http://127.0.0.1:5000/questions/search

{
  "current_category": null, 
  "questions": [
    {
      "answer": "a2 + b2  = c2", 
      "category": "1", 
      "difficulty": 5, 
      "id": 8, 
      "question": "pythogoras theorem"
    }, 
    {
      "answer": "triangle", 
      "category": "1", 
      "difficulty": 5, 
      "id": 9, 
      "question": "pythogoras theorem based on"
    }
  ], 
  "success": true, 
  "total_questions": 2
}

## GET /categories/<int:id>/questions

    General:
        Gets questions by category id using url parameters.
        Returns JSON object with matching questions.

    Sample: curl http://127.0.0.1:5000/categories/1/questions

{
  "current_category": 1, 
  "questions": [
    {
      "answer": "3", 
      "category": "1", 
      "difficulty": 2, 
      "id": 2, 
      "question": "1+2"
    }, 
    {
      "answer": "4", 
      "category": "1", 
      "difficulty": 4, 
      "id": 3, 
      "question": "1+3"
    }, 
    {
      "answer": "7", 
      "category": "1", 
      "difficulty": 5, 
      "id": 4, 
      "question": "1+6"
    }, 
    {
      "answer": "mathematics", 
      "category": "1", 
      "difficulty": 4, 
      "id": 5, 
      "question": "what is math"
    }, 
    {
      "answer": "new", 
      "category": "1", 
      "difficulty": 1, 
      "id": 6, 
      "question": "new math question"
    }, 
    {
      "answer": "mathematics", 
      "category": "1", 
      "difficulty": 5, 
      "id": 7, 
      "question": "math full form"
    }, 
    {
      "answer": "a2 + b2  = c2", 
      "category": "1", 
      "difficulty": 5, 
      "id": 8, 
      "question": "pythogoras theorem"
    }, 
    {
      "answer": "triangle", 
      "category": "1", 
      "difficulty": 5, 
      "id": 9, 
      "question": "pythogoras theorem based on"
    }, 
    {
      "answer": "ramanujan", 
      "category": "1", 
      "difficulty": 5, 
      "id": 10, 
      "question": "rama_____"
    }, 
    {
      "answer": "eleventh", 
      "category": "1", 
      "difficulty": 1, 
      "id": 11, 
      "question": "eleventh question"
    }, 
    {
      "answer": "maths", 
      "category": "1", 
      "difficulty": 1, 
      "id": 12, 
      "question": "new question of math"
    }, 
    {
      "answer": "world", 
      "category": "1", 
      "difficulty": 1, 
      "id": 13, 
      "question": "hello"
    }
  ], 
  "success": true, 
  "total_questions": 12
}

## POST /quizzes

    General:
        Allows users to play the quiz game.
        Uses JSON request parameters of category and previous questions.
        Returns JSON object with random question not among previous questions.

    Sample: curl http://127.0.0.1:5000/quizzes -X POST -H "Content-Type: application/json" -d {"previous_questions":[4],"quiz_category":{"type":"click","id":0}}

{
  "question": {
    "answer": "eleventh", 
    "category": "1", 
    "difficulty": 1, 
    "id": 11, 
    "question": "eleventh question"
  }, 
  "success": true
}
