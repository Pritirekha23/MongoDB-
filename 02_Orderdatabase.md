
Note: For reference please visit the ordertablee.pdf 

CREATED DATABASE NAMED AS Order THHEN INSERTS  4 documents TO THE COLLECTION NAMED AS Transaction.
--------------------------------------------------------------------------------------------------- 
``` 
test> use Order
switched to db Order


Order> db.Transaction.insertMany([
... {
... Tid:53666,
... Product:{
... Pid:389,
... Pname:"banana",
... Price:4
... },
... Customer:{
... Cid:24221,
... Fname:"James",
... Lname:"Smith"
... }
... },   

... {
... Tid:50333,
... Product:{
... Pid:789,
... Pname:"Apple",
... Price:5
... },
... Customer:{
... Cid:24222,
... Fname:"Sam",
... Lname:"Jones"
... }
... },

... {
... Tid:54673,
... Product:{
... Pid:879,
... Pname:"Watermelon",
... Price:5
... },
... Customer:{
... Cid:24223,
... Fname:"Ann",
... Lname:"Taylor"
... }
... },

... {
... Tid:58930,
... product:{
... Pid:975,
... Pname:"Mango",
... Price:7
... },
... Customer:{
... Cid:24224,
... Fname:"Sue",
... Lname:"Burton"
... }
... }

... ]
... )

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('66048303acbff470029f990a'),
    '1': ObjectId('66048303acbff470029f990b'),
    '2': ObjectId('66048303acbff470029f990c'),
    '3': ObjectId('66048303acbff470029f990d')
  }
}
```

select document the Transaction whose Tid=58930
------------------------------------------------
``` Order> db.Transaction.find({Tid:58930})
[
  {
    _id: ObjectId('66048303acbff470029f990d'),
    Tid: 58930,
    product: { Pid: 975, Pname: 'Mango', Price: 7 },
    Customer: { Cid: 24224, Fname: 'Sue', Lname: 'Burton' }
  }
]
```
Select document of the Transaction whose Pid=389
-------------------------------------------------
