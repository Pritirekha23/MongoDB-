# QUERY OPERATORS:
### Relational/Comparison Operators:
- _**$eq**_ : equal
- _**$ne**_ : not equal
- _**$gt**_ : greater than another value
- _**$gte**_ :greater than or equal to 
- _**$lt**_ : less than another value
- _**$lte**_ : less than or equal to 

> 2 more special Operators
- _**$in**_ :Value is matched within an array
- _**$nin**_ :Value is NOT  matched within an array


## Logical Operators:
It is used to combine Relational or Comparison operator.
- _**$and**_: Returns documents where both queries match
- _**$or**_: Returns documents where either query matches
- _**$not**_: Returns documents where the query does not match
- _**$nor**_:Returns documents where both queries fail to match

## Evaluation Operators:



> USE university database,
> created collection named as Books
- use books.json dcouments

## OPERATIONS:
> _(1) WMQ to display all the book whose edition is 2nd Edition ._

```
university> db.Books.find({'edition':{$eq:"2nd Edition"}})
[
  {
    _id: ObjectId('66136e16fe8d7f68a97644d3'),
    title: 'Ramayana',
    author: 'Valmiki',
    language: 'Sanskrit',
    publication_year: 300,
    price: 400,
    is_available: true,
    details: { pages: 1200, publisher: 'Sacred Texts Publishing' },
    tags: [ 'Hinduism', 'Epic', 'Mythology' ],
    description: 'A Sanskrit epic narrating the life of Prince Rama and his quest to rescue his wife Sita from the demon king Ravana.',
    edition: '2nd Edition',
    weight_kg: Decimal128('1.2')
  }
]
```

> _(2) WMQ display all the books whose author is Valmiki._

``` 
university> db.Books.find({"author":{$eq:'Patanjali'}})
[
  {
    _id: ObjectId('66136e16fe8d7f68a97644d4'),
    title: 'Yoga Sutras',
    author: 'Patanjali',
    language: 'Sanskrit',
    publication_year: 150,
    price: 250,
    is_available: true,
    details: { pages: 200, publisher: 'Yoga Wisdom Books' },
    tags: [ 'Hinduism', 'Yoga', 'Philosophy' ],
    description: 'An ancient Indian text on the practice of yoga and meditation.',
    edition: '3rd Edition',
    weight_kg: Decimal128('0.2')
  }
]
```

> _(3) WMQ display all the documents whose tags is "Mythology" or "Yoga" or "Epic"._

```
university> db.Books.find({"tags":{$in:['Mythology','Yoga','Epic']}})
[
  {
    _id: ObjectId('66136e16fe8d7f68a97644d1'),
    title: 'Mahabharata',
    author: 'Vyasa',
    language: 'Sanskrit',
    publication_year: 400,
    price: 450,
    is_available: true,
    details: { pages: 2000, publisher: 'Vedic Publications' },
    tags: [ 'Hinduism', 'Epic', 'Mythology' ],
    description: 'An ancient Indian epic depicting the Kurukshetra War and the teachings of Krishna to Arjuna.',
    edition: '1st Edition',
    weight_kg: Decimal128('1.5')
  },
  {
    _id: ObjectId('66136e16fe8d7f68a97644d3'),
    title: 'Ramayana',
    author: 'Valmiki',
    language: 'Sanskrit',
    publication_year: 300,
    price: 400,
    is_available: true,
    details: { pages: 1200, publisher: 'Sacred Texts Publishing' },
    tags: [ 'Hinduism', 'Epic', 'Mythology' ],
    description: 'A Sanskrit epic narrating the life of Prince Rama and his quest to rescue his wife Sita from the demon king Ravana.',
    edition: '2nd Edition',
    weight_kg: Decimal128('1.2')
  },
  {
    _id: ObjectId('66136e16fe8d7f68a97644d4'),
    title: 'Yoga Sutras',
    author: 'Patanjali',
    language: 'Sanskrit',
    publication_year: 150,
    price: 250,
    is_available: true,
    details: { pages: 200, publisher: 'Yoga Wisdom Books' },
    tags: [ 'Hinduism', 'Yoga', 'Philosophy' ],
    description: 'An ancient Indian text on the practice of yoga and meditation.',
    edition: '3rd Edition',
    weight_kg: Decimal128('0.2')
  }
]
```
> _(4) WMQ display all the records whose tags is not "Mythology" or "Epic"._

```
university> db.Books.find({"tags":{$nin:['Mythology','Epic']}})
[
  {
    _id: ObjectId('66136e16fe8d7f68a97644d0'),
    title: 'Bhagavad Gita',
    author: 'Vyasa',
    language: 'Sanskrit',
    publication_year: 200,
    price: 350,
    is_available: true,
    details: { pages: 856, publisher: 'GITA Press' },
    tags: [ 'Hinduism', 'Philosophy', 'Spirituality' ],
    description: null,
    weight_kg: Decimal128('0.3')
  },
  {
    _id: ObjectId('66136e16fe8d7f68a97644d2'),
    title: 'Upanishads',
    author: 'Various',
    language: 'Sanskrit',
    publication_year: 100,
    price: 300,
    is_available: true,
    details: { pages: 500, publisher: 'Vedanta Publications' },
    tags: [ 'Hinduism', 'Philosophy', 'Spirituality' ],
    description: null,
    weight_kg: Decimal128('0.8')
  },
  {
    _id: ObjectId('66136e16fe8d7f68a97644d4'),
    title: 'Yoga Sutras',
    author: 'Patanjali',
    language: 'Sanskrit',
    publication_year: 150,
    price: 250,
    is_available: true,
    details: { pages: 200, publisher: 'Yoga Wisdom Books' },
    tags: [ 'Hinduism', 'Yoga', 'Philosophy' ],
    description: 'An ancient Indian text on the practice of yoga and meditation.',
    edition: '3rd Edition',
    weight_kg: Decimal128('0.2')
  }
]
```
> _(5) WMQ to display all books whose price is in between 400 to 500._

```
university> db.Books.find({$and:[{"price" : {$gt:400}},{"price" : {$lt:500}}]})
or
university> db.Books.find({"price":{$gt:400,$lt:500}})
[
  {
    _id: ObjectId('66136e16fe8d7f68a97644d1'),
    title: 'Mahabharata',
    author: 'Vyasa',
    language: 'Sanskrit',
    publication_year: 400,
    price: 450,
    is_available: true,
    details: { pages: 2000, publisher: 'Vedic Publications' },
    tags: [ 'Hinduism', 'Epic', 'Mythology' ],
    description: 'An ancient Indian epic depicting the Kurukshetra War and the teachings of Krishna to Arjuna.',
    edition: '1st Edition',
    weight_kg: Decimal128('1.5')
  }
]
```

> _(6)WMQ display all the book whose price is in between 200 to 400  or is_avaiable false._

```
university> db.Books.find({$or:[{"price" : {$gt:200, $lt:400}},{"is_available":false}]})
[
  {
    _id: ObjectId('66136e16fe8d7f68a97644d0'),
    title: 'Bhagavad Gita',
    author: 'Vyasa',
    language: 'Sanskrit',
    publication_year: 200,
    price: 350,
    is_available: false,
    details: { pages: 856, publisher: 'GITA Press' },
    tags: [ 'Hinduism', 'Philosophy', 'Spirituality' ],
    description: null,
    weight_kg: Decimal128('0.3')
  },
  {
    _id: ObjectId('66136e16fe8d7f68a97644d2'),
    title: 'Upanishads',
    author: 'Various',
    language: 'Sanskrit',
    publication_year: 100,
    price: 300,
    is_available: true,
    details: { pages: 500, publisher: 'Vedanta Publications' },
    tags: [ 'Hinduism', 'Philosophy', 'Spirituality' ],
    description: null,
    weight_kg: Decimal128('0.8')
  },
  {
    _id: ObjectId('66136e16fe8d7f68a97644d4'),
    title: 'Yoga Sutras',
    author: 'Patanjali',
    language: 'Sanskrit',
    publication_year: 150,
    price: 250,
    is_available: false,
    details: { pages: 200, publisher: 'Yoga Wisdom Books' },
    tags: [ 'Hinduism', 'Yoga', 'Philosophy' ],
    description: 'An ancient Indian text on the practice of yoga and meditation.',
    edition: '3rd Edition',
    weight_kg: Decimal128('0.2')
  }
]
```
> CONSIDER DATA production.json.

> _(1) 
WMQ to dispaly all the products whose rating is greater than 4 and price is in between 400 to 700._

``` 
Order> db.production.find({"rating":{$gt:4}, "price":{$gt:400,$lt:2000}})
or
Order> db.production.find({$and:[{"rating":{$gt:4}},{"price":{$gt:400,$lt:2000}}]})
[
  {
    _id: ObjectId('661374e0fe8d7f68a97644db'),
    name: 'Yoga Mat',
    description: 'Premium-quality yoga mat for daily practice and meditation',
    category: 'Fitness',
    price: 1200,
    rating: 4.8
  },
  {
    _id: ObjectId('661374e0fe8d7f68a97644df'),
    name: 'Ganesh Idol',
    description: 'Handcrafted Ganesh idol for religious ceremonies and home decor',
    category: 'Home Decor',
    price: 500,
    rating: 4.6
  }
]
```
