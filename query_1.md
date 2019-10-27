# Update key_answer by test_id and it's number

This show you how to update key_answer on spesific test by test_id and it's number
in this case example we will update key_answer from our client which is "Venol". 
The story begin when they want to update key_answer on number 1987.

here is the solution 

```javascript
db.tests.update(
    {
        _id: ObjectId("5dae90541811d29cb463b6c0"),"questions.number": "1987"
    }, 
    {
        $set: {"questions.$.key_answer": "E"}
    },
    false,
    true
);
```

Enjoy it
