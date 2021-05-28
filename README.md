# mgmt590-rest-api
example rest api

## About API
It’s a question answering API where the model returns the answer when provided a question and context. Other features of the API include retrieving the models available in the database as well as recording a timestamp of when a particular question was answered.
## Routes in the API
/models methods are used to handle the information related to the models available in the database.
/answer methods are used to handle the information related to the question, context and answers.
1.	GET /models:
This method is used to retrieve the models available in the database.

Sample Output:
[
    {
        "model": "distilbert-base-uncased-distilled-squad",
        "name": "distilled-bert",
        "tokenizer": "distilbert-base-uncased-distilled-squad"
    },
    {
        "model": "deepset/roberta-base-squad2",
        "name": "deepset-roberta",
        "tokenizer": "deepset/roberta-base-squad2"
    }
]

2.	PUT /models: 
This method is used to insert new models into the database.
	Sample Input:
	{
"name": "bert-tiny",
"tokenizer": "mrm8488/bert-tiny-5-finetuned-squadv2",
"model": "mrm8488/bert-tiny-5-finetuned-squadv2"
}
	Sample Output:
[
    {
        "model": "distilbert-base-uncased-distilled-squad",
        "name": "distilled-bert",
        "tokenizer": "distilbert-base-uncased-distilled-squad"
    },
    {
        "model": "deepset/roberta-base-squad2",
        "name": "deepset-roberta",
        "tokenizer": "deepset/roberta-base-squad2"
    },
    {
        "model": "mrm8488/bert-tiny-5-finetuned-squadv2",
        "name": "bert-tiny",
        "tokenizer": "mrm8488/bert-tiny-5-finetuned-squadv2"
    }
]

3.	DELETE /models?model=<model name>
This method is used to delete the models in the database.
Sample Input:
model=bert-tiny

Sample Output:
[
    {
        "model": "distilbert-base-uncased-distilled-squad",
        "name": "distilled-bert",
        "tokenizer": "distilbert-base-uncased-distilled-squad"
    },
    {
        "model": "deepset/roberta-base-squad2",
        "name": "deepset-roberta",
        "tokenizer": "deepset/roberta-base-squad2"
    }
]



4.	POST /answer?model=<model name>
This method is used to answer a question when given a context with one of the models in the database
Sample Input:
{
"question": "who did holly matthews play in waterloo rd?",
"context": "She attended the British drama school East 15 in 2005,
and left after winning a high-profile role in the BBC drama Waterloo
Road, playing the bully Leigh-Ann Galloway.[6] Since that role,
Matthews has continued to act in BBC's Doctors, playing Connie
Whitfield; in ITV's The Bill playing drug addict Josie Clarke; and
she was back in the BBC soap Doctors in 2009, playing Tansy Flack."
}

Sample Output:
{
    "answer": "Leigh-Ann Galloway",
    "context": "She attended the British drama school East 15 in 2005, and left after winning a high-profile role in the BBC drama Waterloo Road, playing the bully Leigh-Ann Galloway.[6] Since that role, Matthews has continued to act in BBC's Doctors, playing Connie Whitfield; in ITV's The Bill playing drug addict Josie Clarke; and she was back in the BBC soap Doctors in 2009, playing Tansy Flack.",
    "model": "distilled-bert",
    "question": "who did holly matthews play in waterloo rd?",
    "timestamp": 1622168972.7368977
}

5.	GET /answer?model=<model name>&start=<start timestamp>&end=<end timestamp>
This method is used to retrieve the answer and the timestamp at which the question was answered.
Sample Input:
GET
start=1111111111
end=1922168645
Sample Output:
[
    {
        "answer": "Leigh-Ann Galloway",
        "context": "She attended the British drama school East 15 in 2005, and left after winning a high-profile role in the BBC drama Waterloo Road, playing the bully Leigh-Ann Galloway.[6] Since that role, Matthews has continued to act in BBC's Doctors, playing Connie Whitfield; in ITV's The Bill playing drug addict Josie Clarke; and she was back in the BBC soap Doctors in 2009, playing Tansy Flack.",
        "model": "distilled-bert",
        "question": "who did holly matthews play in waterloo rd?",
        "timestamp": 1622168645.5111675
    }
]

  
## Where the API can be located (the base URL): 
https://assignmentrestapi-jyooti7hza-uc.a.run.app

## How to build and run the API locally via Docker or Flask
The app will locally run through localhost link on port 8000 and can be accessed through postman. The methods will work in the similar manner as the one deployed on Google cloud.
  
## Launching the API
Launching the API can easily be done by Flask. The Flask needs to be imported. The address of the host needs to be specified while launching the API

## Handlers
Every handler has a route or path where request comes and gets invoked. 
