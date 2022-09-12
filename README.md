
# Trivia API


## Get Started

* Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, http://127.0.0.1:5000/, which is set as a proxy in the frontend configuration.
* Authentication: This version of the application does not require authentication or API keys.

## Error Handling
Errors are returned as JSON objects in the following format:
```bash
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```
The API will return three error types when requests fail:

* 400: Bad Request
* 404: Resource Not Found
* 422: Not Processable
## Endpoints


## GET /questions


* General:
    * Returns a list of questions objects, success value, and total number of questions
    * Results are paginated in groups of 10. Include a request argument to choose page number, starting from 1.
* ``` curl http://127.0.0.1:5000/questions```

```
  {
  "categories": [
    {
      "id": 1,
      "type": "Science"
    },
    {
      "id": 2,
      "type": "Art"
    },
    {
      "id": 3,
      "type": "Geography"
    },
    {
      "id": 4,
      "type": "History"
    },
    {
      "id": 5,
      "type": "Entertainment"
    },
    {
      "id": 6,
      "type": "Sports"
    }
  ],
  "questions": [
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }
  ],
  "success": true,
  "total_questions": 10
}
```
### GET /categories

* General:
    * Returns a list of categories objects, success value, and total number of books
    * Results are paginated in groups of 8. Include a request argument to choose page number, starting from 1.
* ```curl http://127.0.0.1:5000/categories```

```{
  "categories": [
    {
      "id": 1,
      "type": "Science"
    },
    {
      "id": 2,
      "type": "Art"
    },
    {
      "id": 3,
      "type": "Geography"
    },
    {
      "id": 4,
      "type": "History"
    },
    {
      "id": 5,
      "type": "Entertainment"
    },
    {
      "id": 6,
      "type": "Sports"
    }
  ],
  "success": true,
  "totals_categories": 6
}
```
## DELETE  /questions/{question_id}

* General:
    * Deletes the question of the given ID if it exists. Returns the id of the deleted question, success value, total questions, and questions list.
* ```curl -X DELETE http://127.0.0.1:5000/questions/10```

```{
    "deleted": 10,
    "questions": [
        {
            "answer": "Maya Angelou",
            "category": 4,
            "difficulty": 2,
            "id": 5,
            "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
        },
        {
            "answer": "Muhammad Ali",
            "category": 4,
            "difficulty": 1,
            "id": 9,
            "question": "What boxer's original name is Cassius Clay?"
        },
        {
            "answer": "Apollo 13",
            "category": 5,
            "difficulty": 4,
            "id": 2,
            "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
        },
        {
            "answer": "Tom Cruise",
            "category": 5,
            "difficulty": 4,
            "id": 4,
            "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
        },
        {
            "answer": "Edward Scissorhands",
            "category": 5,
            "difficulty": 3,
            "id": 6,
            "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
        },
        {
            "answer": "Uruguay",
            "category": 6,
            "difficulty": 4,
            "id": 11,
            "question": "Which country won the first ever soccer World Cup in 1930?"
        },
        {
            "answer": "George Washington Carver",
            "category": 4,
            "difficulty": 2,
            "id": 12,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Lake Victoria",
            "category": 3,
            "difficulty": 2,
            "id": 13,
            "question": "What is the largest lake in Africa?"
        },
        {
            "answer": "The Palace of Versailles",
            "category": 3,
            "difficulty": 3,
            "id": 14,
            "question": "In which royal palace would you find the Hall of Mirrors?"
        },
        {
            "answer": "Agra",
            "category": 3,
            "difficulty": 2,
            "id": 15,
            "question": "The Taj Mahal is located in which Indian city?"
        }
    ],
    "success": true,
    "total_questions": 20
}
```
## POST /questions
* General:
    * Creates a new question using the submitted question, anwser, category and defficulty. Returns the id the created question, success value, total questions, and questions.
* ```curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d '{ "question": "New question", "answer": "new awnser ", "category": 5, "difficulty": 6}'```

```{
    "created": 34,
    "questions": [
        {
            "answer": "Apollo 13",
            "category": 5,
            "difficulty": 4,
            "id": 2,
            "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
        },
        {
            "answer": "Tom Cruise",
            "category": 5,
            "difficulty": 4,
            "id": 4,
            "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
        },
        {
            "answer": "Maya Angelou",
            "category": 4,
            "difficulty": 2,
            "id": 5,
            "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
        },
        {
            "answer": "Edward Scissorhands",
            "category": 5,
            "difficulty": 3,
            "id": 6,
            "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
        },
        {
            "answer": "Muhammad Ali",
            "category": 4,
            "difficulty": 1,
            "id": 9,
            "question": "What boxer's original name is Cassius Clay?"
        },
        {
            "answer": "Uruguay",
            "category": 6,
            "difficulty": 4,
            "id": 11,
            "question": "Which country won the first ever soccer World Cup in 1930?"
        },
        {
            "answer": "George Washington Carver",
            "category": 4,
            "difficulty": 2,
            "id": 12,
            "question": "Who invented Peanut Butter?"
        },
        {
            "answer": "Lake Victoria",
            "category": 3,
            "difficulty": 2,
            "id": 13,
            "question": "What is the largest lake in Africa?"
        },
        {
            "answer": "The Palace of Versailles",
            "category": 3,
            "difficulty": 3,
            "id": 14,
            "question": "In which royal palace would you find the Hall of Mirrors?"
        },
        {
            "answer": "Agra",
            "category": 3,
            "difficulty": 2,
            "id": 15,
            "question": "The Taj Mahal is located in which Indian city?"
        }
    ],
    "success": true,
    "total_questions": 10
}

```
## POST /questions/search
* General:
    * Resturns questions list, total questions, succes value based on a search Term
* ```curl http://127.0.0.1:5000/questions/search -X POST -H "Content-Type: application/json" -d '{ "searchTerm": "New"}```
```{
    "current_category": [
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 27,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 28,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 29,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 30,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 31,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 32,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 33,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 34,
            "question": "New question"
        }
    ],
    "questions": [
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 27,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 28,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 29,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 30,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 31,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 32,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 33,
            "question": "New question"
        },
        {
            "answer": "new awnser ",
            "category": 5,
            "difficulty": 6,
            "id": 34,
            "question": "New question"
        }
    ],
    "success": true,
    "total_questions": 8
}
```