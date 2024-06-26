C:\Users\ASUS>mongosh
Current Mongosh Log ID: 66045365b4d898ccce9f9909
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.2.2
Using MongoDB:          7.0.7
Using Mongosh:          2.2.2

For mongosh info see: https://docs.mongodb.com/mongodb-shell/


To help improve our products, anonymous usage data is collected and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

------
   The server generated these startup warnings when booting
   2024-03-22T00:31:18.148+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------


__________________________________

test> show dbs
admin   40.00 KiB
config  60.00 KiB
local   72.00 KiB

CREATING DATABASE:
-------------------
test> use university
switched to db university

In university database we are trying to show the database but there is no database present in university database:
------------------------------------------------------------------------------------------------------------------
university> show dbs
admin   40.00 KiB
config  72.00 KiB
local   72.00 KiB

createCollection
-----------------
university> db.createCollection("students")
{ ok: 1 }

inserting document to the collection:
-----------------------------------------
  inserting single document to the collection:
  --------------------------------------------- 
university> db.students.insertOne(
... {
... name:"priti",
... age:21,
... mark:75,
... dept:"CSE"
... }
... )
{
  acknowledged: true,
  insertedId: ObjectId('66045618b4d898ccce9f990a')
}

selecting documents:
---------------------

university> db.students.find()
[
  {
    _id: ObjectId('66045618b4d898ccce9f990a'),
    name: 'priti',
    age: 21,
    mark: 75,
    dept: 'CSE'
  }
]

inserting many documents to the collection:
-------------------------------------------
university> db.students.insertMany([
... {
... name:"Rahul",
... age:22,
... mark:65,
... dept:'ECE'
... },
... {
... name:"Zini",
... age:23,
... mark:76,
... dept:"EE"
... },
... {
... name:"Smruti",
... age:22,
... mark:87,
... dept:"EE"
... }
... ]
... )
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('66045c70b4d898ccce9f990b'),
    '1': ObjectId('66045c70b4d898ccce9f990c'),
    '2': ObjectId('66045c70b4d898ccce9f990d')
  }
}

selecting documents:
--------------------
university> db.students.find()
[
  {
    _id: ObjectId('66045618b4d898ccce9f990a'),
    name: 'priti',
    age: 21,
    mark: 75,
    dept: 'CSE'
  },
  {
    _id: ObjectId('66045c70b4d898ccce9f990b'),
    name: 'Rahul',
    age: 22,
    mark: 65,
    dept: 'ECE'
  },
  {
    _id: ObjectId('66045c70b4d898ccce9f990c'),
    name: 'Zini',
    age: 23,
    mark: 76,
    dept: 'EE'
  },
  {
    _id: ObjectId('66045c70b4d898ccce9f990d'),
    name: 'Smruti',
    age: 22,
    mark: 87,
    dept: 'EE'
  }
]



HOW TO GET ALL THE COLLECTION NAMES PRESENT IN A DATABASE:
----------------------------------------------------------
LET WE SELECTED university DATABASE
------------------------------------
Commands:
-----------
university>use university
university>show collections
employee
students


select the document of priti
--------------------------------

university> db.students.find({name:"priti"})
[
  {
    _id: ObjectId('66045618b4d898ccce9f990a'),
    name: 'priti',
    age: 21,
    mark: 75,
    dept: 'CSE'
  }
]


collection name :employee
--------------------------
select all the employee documents whose salary is greater than 20000:
--------------------------------------------------------------------
university> db.employee.find({esal:{$gt:20000}})
[
  {
    _id: ObjectId('660466afb4d898ccce9f990e'),
    ename: 'Ram',
    esal: 22000,
    yoj: 2022
  }
]

select all the employee documents whose salary is less than 15000:
------------------------------------------------------------------
university> db.employee.find({esal:{$lt:15000}})
[
  {
    _id: ObjectId('660466afb4d898ccce9f990f'),
    ename: 'Sam',
    esal: 12000,
    ypj: 2023
  }
]