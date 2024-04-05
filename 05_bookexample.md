

CREATED Book DATABASE :
-------------------------
test> use Book
switched to db Book

CREATED COLLECTION NAMED AS Books:
-------------------------------------
Book> db.createCollection("Books")
{ ok: 1 }

---------------------------------------
INSERTED DOCUMENTS IN BOOKS COLLECTION
---------------------------------------
Book> db.Books.insertMany([
... {
... title: "The God of Small Things",
... Author:"Arundhati Roy",
... Price:350,
... PublicationDetails:{
... year:1997,
... phouse:"Ar PublicationHouse",
... address:{
... city:"Balasore",
... landmark:"Near Hanuman temple",
... plot:"A/101",
... pin:756112
... }
... }
... },
... {
... title: "Midnight's Children",
... Author:" Salman Rushdie",
... Price:400,
... PublicationDetails:{
... year:1981,
... phouse:"Sa PublicationHouse",
... address:{
... city:"khorda",
... landmark:"Near Rama temple",
... plot:"B/102",
... pin:756101
... }
... }
... },
... {
...  title: "The White Tiger",
... Author:["Aravind Adiga","Komal Jha"],
...  PublicationDetails:{
... year:2008,
... phouse:"ArKo Publicationhouse",
... address:{
... city:"Cuttack",
... landmark:"Near Appolo",
... plot:"C/200",
... pin:756123
... }
... }
... },
... {
... title:"The Palace of Illusions",
... Author:" Chitra Banerjee Divakaruni",
... Price:340,
...  PublicationDetails:{
... year:2010,
... phouse:"Ch publocationhouse",
... address:{
... city:"Cuttack",
... landmark:"Near Sai temple",
... plot:"D/302",
... pin:756114
... }
... }
... }
... ]
... )
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('660a2b2dd6e35833099f990a'),
    '1': ObjectId('660a2b2dd6e35833099f990b'),
    '2': ObjectId('660a2b2dd6e35833099f990c'),
    '3': ObjectId('660a2b2dd6e35833099f990d')
  }
}


--------------------
SHOWING DOCUMENTS
--------------------

Book> db.Books.find()
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    title: 'The God of Small Things',
    Author: 'Arundhati Roy',
    Price: 350,
    PublicationDetails: {
      year: 1997,
      phouse: 'Ar PublicationHouse',
      address: {
        city: 'Balasore',
        landmark: 'Near Hanuman temple',
        plot: 'A/101',
        pin: 756112
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990b'),
    title: "Midnight's Children",
    Author: ' Salman Rushdie',
    Price: 400,
    PublicationDetails: {
      year: 1981,
      phouse: 'Sa PublicationHouse',
      address: {
        city: 'khorda',
        landmark: 'Near Rama temple',
        plot: 'B/102',
        pin: 756101
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990c'),
    title: 'The White Tiger',
    Author: [ 'Aravind Adiga', 'Komal Jha' ],
    PublicationDetails: {
      year: 2008,
      phouse: 'ArKo Publicationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Appolo',
        plot: 'C/200',
        pin: 756123
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  }
]


------------
OPERATIONS:
------------

---------------------------------------------------------------------------------
(1)WMQ to get all the book documents whose publication year is greater than 2008.
---------------------------------------------------------------------------------
- Ans:
----
``` Book> db.Books.find({"PublicationDetails.year":{$gt:2008}})
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  }
]```

------------------------------------------------------------------------------
(2)WMQ to get all the book documents whose publication year is less than 2008.
------------------------------------------------------------------------------
Ans:
----
```Book> db.Books.find({"PublicationDetails.year":{$lt:2008}})
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    title: 'The God of Small Things',
    Author: 'Arundhati Roy',
    Price: 350,
    PublicationDetails: {
      year: 1997,
      phouse: 'Ar PublicationHouse',
      address: {
        city: 'Balasore',
        landmark: 'Near Hanuman temple',
        plot: 'A/101',
        pin: 756112
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990b'),
    title: "Midnight's Children",
    Author: ' Salman Rushdie',
    Price: 400,
    PublicationDetails: {
      year: 1981,
      phouse: 'Sa PublicationHouse',
      address: {
        city: 'khorda',
        landmark: 'Near Rama temple',
        plot: 'B/102',
        pin: 756101
      }
    }
  }
]

 ```
--------------------------------------------------------------
(3)WMQ to get deatils about the book written by Arundhati Roy.
--------------------------------------------------------------
Ans:
----
```Book> db.Books.find({"Author":"Arundhati Roy"})
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    title: 'The God of Small Things',
    Author: 'Arundhati Roy',
    Price: 350,
    PublicationDetails: {
      year: 1997,
      phouse: 'Ar PublicationHouse',
      address: {
        city: 'Balasore',
        landmark: 'Near Hanuman temple',
        plot: 'A/101',
        pin: 756112
      }
    }
  }
]
 ```
---------------------------------
(4)WMQ to get all author names.
---------------------------------
Ans:
----
``` Book> db.Books.find({}, { "Author": 1, "_id": 0 })
[
  { Author: 'Arundhati Roy' },
  { Author: ' Salman Rushdie' },
  { Author: [ 'Aravind Adiga', 'Komal Jha' ] },
  { Author: ' Chitra Banerjee Divakaruni' }
]```


----------------------------------------------
(5)WMQ to get plot number of all the documents
----------------------------------------------
Ans:
----
```Book> db.Books.find({},{"PublicationDetails.address.plot":1,"_id":0})
[
  { PublicationDetails: { address: { plot: 'A/101' } } },
  { PublicationDetails: { address: { plot: 'B/102' } } },
  { PublicationDetails: { address: { plot: 'C/200' } } },
  { PublicationDetails: { address: { plot: 'D/302' } } }
] ```


OR
----
``` Book> db.Books.find({},{"PublicationDetails.address.plot":1})
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    PublicationDetails: { address: { plot: 'A/101' } }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990b'),
    PublicationDetails: { address: { plot: 'B/102' } }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990c'),
    PublicationDetails: { address: { plot: 'C/200' } }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    PublicationDetails: { address: { plot: 'D/302' } }
  }
]```
-----------------------------------------------------------------------------
(6) WMQ to display all book those who have published in between 2000 to 2020.
-----------------------------------------------------------------------------
```Book> db.Books.find({"PublicationDetails.year": { $gt:2000,$lt:2020}} )
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990c'),
    title: 'The White Tiger',
    Author: [ 'Aravind Adiga', 'Komal Jha' ],
    PublicationDetails: {
      year: 2008,
      phouse: 'ArKo Publicationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Appolo',
        plot: 'C/200',
        pin: 756123
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  }
] ```
------->    
```Book> db.Books.find({"PublicationDetails.year": { $gte:2000,$lte:2020}} )
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990c'),
    title: 'The White Tiger',
    Author: [ 'Aravind Adiga', 'Komal Jha' ],
    PublicationDetails: {
      year: 2008,
      phouse: 'ArKo Publicationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Appolo',
        plot: 'C/200',
        pin: 756123
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  }
] ```

---------------------------------------------
QUESTION FOR THE ABOVE QUERY (OPERATION(6))
--------------------------------------------
------------------------------------------------------------------------------
what is the difference between these two commands?
db.Books.find({"PublicationDetails.year": { $gt:2000,$lt:2020}} ) 
db.Books.find({"PublicationDetails.year": { $gte:2000,$lte:2020}} )
------------------------------------------------------------------------------

Ans:
-----
The difference between the two commands is $gt and $lt  used in the first command and  $gte and $lte  used in the second command.

So,
db.Books.find({"PublicationDetails.year": { $gt:2000,$lt:2020}} ) , This command will give the output where the year is greater than 2000 and less than 2020 that is between the year 2001 and 2019.

db.Books.find({"PublicationDetails.year": { $gte:2000,$lte:2020}} ) , This command will give the output where the year is greater than or equal to 2000 and less than  or equal to 2020 that is between the year 2000 and 2020.

----------------------------------------------------
(7)WMQ to count number of book.
-----------------------------------------------------
Ans
---
Book> db.Books.find().count()
4

-----------------------------------------------------------------------------------
(8)WMQ to display all the book based on publishcation year. (ascending order)  
------------------------------------------------------------------------------------
===================================================================
Note:  1 means ascending order and -1 means (descending order).
===================================================================
Ans:
----
``` Book> db.Books.find().sort({"PublicationDetails.Price": 1})
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    title: 'The God of Small Things',
    Author: 'Arundhati Roy',
    Price: 350,
    PublicationDetails: {
      year: 1997,
      phouse: 'Ar PublicationHouse',
      address: {
        city: 'Balasore',
        landmark: 'Near Hanuman temple',
        plot: 'A/101',
        pin: 756112
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990b'),
    title: "Midnight's Children",
    Author: ' Salman Rushdie',
    Price: 400,
    PublicationDetails: {
      year: 1981,
      phouse: 'Sa PublicationHouse',
      address: {
        city: 'khorda',
        landmark: 'Near Rama temple',
        plot: 'B/102',
        pin: 756101
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990c'),
    title: 'The White Tiger',
    Author: [ 'Aravind Adiga', 'Komal Jha' ],
    PublicationDetails: {
      year: 2008,
      phouse: 'ArKo Publicationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Appolo',
        plot: 'C/200',
        pin: 756123
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  }
]
```
-----------------------------------------------------------------------------------
(9)WMQ to display all the book based on publishcation year. (descending order)
------------------------------------------------------------------------------------
Ans:
----
``` Book> db.Books.find().sort({"PublicationDetails.year": -1})
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990c'),
    title: 'The White Tiger',
    Author: [ 'Aravind Adiga', 'Komal Jha' ],
    PublicationDetails: {
      year: 2008,
      phouse: 'ArKo Publicationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Appolo',
        plot: 'C/200',
        pin: 756123
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    title: 'The God of Small Things',
    Author: 'Arundhati Roy',
    Price: 350,
    PublicationDetails: {
      year: 1997,
      phouse: 'Ar PublicationHouse',
      address: {
        city: 'Balasore',
        landmark: 'Near Hanuman temple',
        plot: 'A/101',
        pin: 756112
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990b'),
    title: "Midnight's Children",
    Author: ' Salman Rushdie',
    Price: 400,
    PublicationDetails: {
      year: 1981,
      phouse: 'Sa PublicationHouse',
      address: {
        city: 'khorda',
        landmark: 'Near Rama temple',
        plot: 'B/102',
        pin: 756101
      }
    }
  }
]```

-----------------------------------------------------------------------------------
(10) WMQ to display all the author names started with 'A'
------------------------------------------------------------------------------------
Ans:
----








---------------------------------------------
(11)WMQ where skip first 3 documents.
---------------------------------------------
Ans:
----
``` Book> db.Books.find().skip(3)
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  }
]```





---------------------------------------------
(12)WMQ wgtgo show first 2 documents.
---------------------------------------------
Ans:
----
```  Book> db.Books.find().limit(2)
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    title: 'The God of Small Things',
    Author: 'Arundhati Roy',
    Price: 350,
    PublicationDetails: {
      year: 1997,
      phouse: 'Ar PublicationHouse',
      address: {
        city: 'Balasore',
        landmark: 'Near Hanuman temple',
        plot: 'A/101',
        pin: 756112
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990b'),
    title: "Midnight's Children",
    Author: ' Salman Rushdie',
    Price: 400,
    PublicationDetails: {
      year: 1981,
      phouse: 'Sa PublicationHouse',
      address: {
        city: 'khorda',
        landmark: 'Near Rama temple',
        plot: 'B/102',
        pin: 756101
      }
    }
  }
]
```
------------------------------------
pretty() Method in MongoDB:
-----------------------------------

The pretty() method in MongoDB is used to display query results in a more readable format. It formats the output with indentation and additional white space, making it easier to read, especially for complex documents.

```Book> db.Books.find().pretty()
[
  {
    _id: ObjectId('660a2b2dd6e35833099f990a'),
    title: 'The God of Small Things',
    Author: 'Arundhati Roy',
    Price: 350,
    PublicationDetails: {
      year: 1997,
      phouse: 'Ar PublicationHouse',
      address: {
        city: 'Balasore',
        landmark: 'Near Hanuman temple',
        plot: 'A/101',
        pin: 756112
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990b'),
    title: "Midnight's Children",
    Author: ' Salman Rushdie',
    Price: 400,
    PublicationDetails: {
      year: 1981,
      phouse: 'Sa PublicationHouse',
      address: {
        city: 'khorda',
        landmark: 'Near Rama temple',
        plot: 'B/102',
        pin: 756101
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990c'),
    title: 'The White Tiger',
    Author: [ 'Aravind Adiga', 'Komal Jha' ],
    PublicationDetails: {
      year: 2008,
      phouse: 'ArKo Publicationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Appolo',
        plot: 'C/200',
        pin: 756123
      }
    }
  },
  {
    _id: ObjectId('660a2b2dd6e35833099f990d'),
    title: 'The Palace of Illusions',
    Author: ' Chitra Banerjee Divakaruni',
    Price: 340,
    PublicationDetails: {
      year: 2010,
      phouse: 'Ch publocationhouse',
      address: {
        city: 'Cuttack',
        landmark: 'Near Sai temple',
        plot: 'D/302',
        pin: 756114
      }
    }
  }
]

 ```