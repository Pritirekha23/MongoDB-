
- DATABASE NAME: Movies
- collection name: movies
- json file name: movies.json

# OPERATIONS

_(1) FIND ALL THE TITLE ALL THE MOVIES_

```
Movies> db.movies.distinct("title")
[
  'Bahubali: The Beginning',
  'Bajrangi Bhaijaan',
  'PK',
  'Padmaavat',
  'Sultan'
]

```

> The **distinct** method in MongoDB is used to return all unique values for a specified field across a collection. It returns an array of distinct values for the specified field.


_(2)WMQ To find the movies with the tag "Drama"._

```
Movies> db.movies.find({"tags":"Comedy"})
[
  {
    _id: ObjectId('6617c35a9e9ae4ff0c0ae745'),
    title: 'Bajrangi Bhaijaan',
    year: '2015',
    tags: [ 'Comedy', 'Drama' ],
    ratings: [ 8, 7, 6, 7, 7, 8 ],
    contentRating: 'PG',
    duration: 'PT159M',
    releaseDate: '2015-07-17',
    averageRating: 7,
    originalTitle: 'बाजरंगी भाईजान',
    storyline: 'An Indian man with a magnanimous heart takes a young mute Pakistani girl back to her homeland to reunite her with her family.',
    actors: [ 'Salman Khan', 'Harshaali Malhotra', 'Kareena Kapoor' ],
    imdbRating: 8.1,
    author: {
      name: 'Kabir Khan',
      age: 50,
      address: {
        street: '10, Versova, Andheri West',
        city: 'Mumbai',
        country: 'India'
      },
      netWorthDetails: { netWorth: '$15 million', sourceOfWealth: 'Film direction' }
    }
  },
  {
    _id: ObjectId('6617c35a9e9ae4ff0c0ae746'),
    title: 'PK',
    year: '2014',
    tags: [ 'Comedy', 'Drama' ],
    ratings: [ 8, 8, 8, 8, 8, 8 ],
    contentRating: 'PG-13',
    duration: 'PT153M',
    releaseDate: '2014-12-19',
    averageRating: 8,
    originalTitle: 'पीक',
    storyline: 'An alien on Earth loses his spaceship and must learn to live on the planet, while searching for his lost remote.',
    actors: [ 'Aamir Khan', 'Anushka Sharma', 'Sushant Singh Rajput' ],
    imdbRating: 8.2,
    author: {
      name: 'Rajkumar Hirani',
      age: 58,
      address: {
        street: '10, Pali Hill, Bandra West',
        city: 'Mumbai',
        country: 'India'
      },
      netWorthDetails: { netWorth: '$30 million', sourceOfWealth: 'Film direction' }
    }
  }
]
```

_(3)WMQ To find the movies directed by Rajkumar Hirani_

```
Movies> db.movies.find({"author.name":"Rajkumar Hirani"})
[
  {
    _id: ObjectId('6617c35a9e9ae4ff0c0ae746'),
    title: 'PK',
    year: '2014',
    tags: [ 'Comedy', 'Drama' ],
    ratings: [ 8, 8, 8, 8, 8, 8 ],
    contentRating: 'PG-13',
    duration: 'PT153M',
    releaseDate: '2014-12-19',
    averageRating: 8,
    originalTitle: 'पीक',
    storyline: 'An alien on Earth loses his spaceship and must learn to live on the planet, while searching for his lost remote.',
    actors: [ 'Aamir Khan', 'Anushka Sharma', 'Sushant Singh Rajput' ],
    imdbRating: 8.2,
    author: {
      name: 'Rajkumar Hirani',
      age: 58,
      address: {
        street: '10, Pali Hill, Bandra West',
        city: 'Mumbai',
        country: 'India'
      },
      netWorthDetails: { netWorth: '$30 million', sourceOfWealth: 'Film direction' }
    }
  }
]

```

_(4)WMQ To find the movie with the highest imdbRating ._

```
Movies> db.movies.find().sort({"imdbRating":-1}).limit(1)
[
  {
    _id: ObjectId('6617c35a9e9ae4ff0c0ae746'),
    title: 'PK',
    year: '2014',
    tags: [ 'Comedy', 'Drama' ],
    ratings: [ 8, 8, 8, 8, 8, 8 ],
    contentRating: 'PG-13',
    duration: 'PT153M',
    releaseDate: '2014-12-19',
    averageRating: 8,
    originalTitle: 'पीक',
    storyline: 'An alien on Earth loses his spaceship and must learn to live on the planet, while searching for his lost remote.',
    actors: [ 'Aamir Khan', 'Anushka Sharma', 'Sushant Singh Rajput' ],
    imdbRating: 8.2,
    author: {
      name: 'Rajkumar Hirani',
      age: 58,
      address: {
        street: '10, Pali Hill, Bandra West',
        city: 'Mumbai',
        country: 'India'
      },
      netWorthDetails: { netWorth: '$30 million', sourceOfWealth: 'Film direction' }
    }
  }
]
```

_(5)WMQ To find the movie with the lowest imdbRating ._

```
Movies> db.movies.find().sort({"imdbRating":1}).limit(1)
[
  {
    _id: ObjectId('6617c35a9e9ae4ff0c0ae748'),
    title: 'Padmaavat',
    year: '2018',
    tags: [ 'Drama', 'History' ],
    ratings: [ 7, 7, 7, 7, 7, 7 ],
    contentRating: 'PG-13',
    duration: 'PT164M',
    releaseDate: '2018-01-25',
    averageRating: 7,
    originalTitle: 'पद्मावत',
    storyline: "Set in medieval Rajasthan, Queen Padmavati is married to a noble king and they live in a prosperous fortress with their subjects until an ambitious Sultan hears of Padmavati's beauty and forms an obsession over her.",
    actors: [ 'Deepika Padukone', 'Shahid Kapoor', 'Ranveer Singh' ],
    imdbRating: 7,
    author: {
      name: 'Sanjay Leela Bhansali',
      age: 59,
      address: {
        street: '10, Pali Hill, Bandra West',
        city: 'Mumbai',
        country: 'India'
      },
      netWorthDetails: { netWorth: '$100 million', sourceOfWealth: 'Film direction' }
    }
  }
]
```

_(6)WMQ to display all the authors name whose age is in between 50 to 60._

```
Movies> db.movies.find({$and:[{"author.age" : {$gt:50}},{"author.age" : {$lt:60}}]})
or 
Movies> db.movies.find({"author.age" : {$gt:50,$lt:60}})

[
  {
    _id: ObjectId('6617c35a9e9ae4ff0c0ae746'),
    title: 'PK',
    year: '2014',
    tags: [ 'Comedy', 'Drama' ],
    ratings: [ 8, 8, 8, 8, 8, 8 ],
    contentRating: 'PG-13',
    duration: 'PT153M',
    releaseDate: '2014-12-19',
    averageRating: 8,
    originalTitle: 'पीक',
    storyline: 'An alien on Earth loses his spaceship and must learn to live on the planet, while searching for his lost remote.',
    actors: [ 'Aamir Khan', 'Anushka Sharma', 'Sushant Singh Rajput' ],
    imdbRating: 8.2,
    author: {
      name: 'Rajkumar Hirani',
      age: 58,
      address: {
        street: '10, Pali Hill, Bandra West',
        city: 'Mumbai',
        country: 'India'
      },
      netWorthDetails: { netWorth: '$30 million', sourceOfWealth: 'Film direction' }
    }
  },
  {
    _id: ObjectId('6617c35a9e9ae4ff0c0ae748'),
    title: 'Padmaavat',
    year: '2018',
    tags: [ 'Drama', 'History' ],
    ratings: [ 7, 7, 7, 7, 7, 7 ],
    contentRating: 'PG-13',
    duration: 'PT164M',
    releaseDate: '2018-01-25',
    averageRating: 7,
    originalTitle: 'पद्मावत',
    storyline: "Set in medieval Rajasthan, Queen Padmavati is married to a noble king and they live in a prosperous fortress with their subjects until an ambitious Sultan hears of Padmavati's beauty and forms an obsession over her.",
    actors: [ 'Deepika Padukone', 'Shahid Kapoor', 'Ranveer Singh' ],
    imdbRating: 7,
    author: {
      name: 'Sanjay Leela Bhansali',
      age: 59,
      address: {
        street: '10, Pali Hill, Bandra West',
        city: 'Mumbai',
        country: 'India'
      },
      netWorthDetails: { netWorth: '$100 million', sourceOfWealth: 'Film direction' }
    }
  }
]
```


_(7)WMQ to display all the originalTitle of the movies._

```
Movies> db.movies.distinct("originalTitle")
[ 'पद्मावत', 'पीक', 'बाजरंगी भाईजान', 'सुल्तान', 'బాహుబలి: దయము' ]
```

_(8)WMQ to display  all movies released in 2015 with the tag 'Drama' and the author's net worth over $10 million: ._
```
```