CREATED Roadmap DATABASE :
-------------------------
test> use Roadmap
switched to db Roadmap

CREATEd COLLECTION NAMED AS fullstack:
-------------------------------------
Roadmap> db.createCollection("fullstack")
{ ok: 1 }

INSERTING MULTIPLE DOCUMENTS TO THE DATABASE:
----------------------------------------------


Roadmap> db.fullstack.insertMany([ { category:"frontend", skills:[ { name:"HTML5", author:"Tim Berners-Lee", yop:1993 }, { name:"CSS3", author:["Hakon Wium Lie","Bert Bos"], yop:1996, frameworks:["Bootstrap","tailwind CSS"] }, { name:"JavaScript", author:"Brendan Eich", yop:1995, frameworks:["React","Angular","Vue.js"] }] }, { category:"Backend", skills:[ { name:"Python", author:"Guido Van Rossum", yop:1991, frameworks:["Flask","Django"] }, { name:"Node.js", author:"Ryan Dahl", yop:2009, Frameworks:["Express","Next,js"] } ] }, { category:"Database" , skills:[ { name:"SQL", author:["Raymond Boyce","Donald Chamberlain"], yop:1970, frameworks:["MySQL","PostgresSQL","SQLite"] }, { name:"NoSQL", author:"Carl Strozz", yop:1998, frameworks:["MongoDB","FireBase","CouchDB"] } ] } ])

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6608686b86652064169f990a'),
    '1': ObjectId('6608686b86652064169f990b'),
    '2': ObjectId('6608686b86652064169f990c')
  }
}


SHOWING ALL THE DATA:
---------------------
Roadmap> db.fullstack.find()
[
  {
    _id: ObjectId('6608686b86652064169f990a'),
    category: 'frontend',
    skills: [
      { name: 'HTML5', author: 'Tim Berners-Lee', yop: 1993 },
      {
        name: 'CSS3',
        author: [ 'Hakon Wium Lie', 'Bert Bos' ],
        yop: 1996,
        frameworks: [ 'Bootstrap', 'tailwind CSS' ]
      },
      {
        name: 'JavaScript',
        author: 'Brendan Eich',
        yop: 1995,
        frameworks: [ 'React', 'Angular', 'Vue.js' ]
      }
    ]
  },
  {
    _id: ObjectId('6608686b86652064169f990b'),
    category: 'Backend',
    skills: [
      {
        "name": "Python",
        "author": "Guido Van Rossum",
        "yop": 1991,
        "frameworks": [ "Flask", "Django" ]
      },
      {
        "name": "Node.js",
        "author": 'Ryan Dahl',
        "yop": 2009,
        "frameworks": [ 'Express', 'Next,js' ]
      }
    ]
  },
  {
    _id: ObjectId('6608686b86652064169f990c'),
    category: 'Database',
    skills: [
      {
        "name": "SQL",
        "author": [ "Raymond Boyce", "Donald Chamberlain" ],
        "yop": 1970,
        "frameworks": [ "MySQL", "PostgresSQL", "SQLite" ]
      },
      {
        "name": "NoSQL",
        "author": "Carl Strozz",
        "yop": 1998,
        "frameworks": [ "MongoDB", "FireBase", "CouchDB" ]
      }
    ]
  }
]


QUESTIONS:
----------
(1) WMQ to get all the Roadmap documents whose year of publish(yop) is greater than 1998.


issue
======
Roadmap> db.fullstack.find({"skills.yop":{$gt:1998}})
[
  {
    _id: ObjectId('6608686b86652064169f990b'),
    category: 'Backend',
    skills: [
      {
        name: 'Python',
        author: 'Guido Van Rossum',
        yop: 1991,
        frameworks: [ 'Flask', 'Django' ]
      },
      {
        name: 'Node.js',
        author: 'Ryan Dahl',
        yop: 2009,
        Frameworks: [ 'Express', 'Next,js' ]
      }
    ]
  }
]
