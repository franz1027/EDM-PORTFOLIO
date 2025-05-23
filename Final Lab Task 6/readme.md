-use mongo_practice
-switched to db mongo_practice
-Insert the following documents into a `movies` collection.

-db.movies.insert({title:"Fight Club", writer: "Chuck Palahniuk", year: "1999", actors:["Brad Pitt", "Edward Norton"]})
-DeprecationWarning: Collection.insert() is deprecated. Use insertOne, insertMany, or bulkWrite.
-{
-  acknowledged: true,
-  insertedIds: {
 -   '0': ObjectId('68307618082aab3cd7c80c9b')
  }
}
 db.movies.insert({title:"Pulp Fiction", writer:"Quentin Tarantino", year:"2009", actors:["John Travolta", "Uma Thurman"]})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307626082aab3cd7c80c9c')
  }
}
db.movies.insert({title:"Inglorious Basterds", writer:"Quentin Tarantino", year:"2009", actors:["Brad Pitt", "Diane Kruger", "Eli Roth"]})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830762e082aab3cd7c80c9d')
  }
}
db.movies.insert({title:"The Hobbit: An unexpected Journey", writer:"J.R.R. Tolkein", year:"2012",franchise:"The Hobbit"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307635082aab3cd7c80c9e')
  }
}
db.movies.insert({title:"The Hobbit: The Desolation of Smaug", writer:"J.R.R Tolkien", year:"2013", franchise:"The Hobbit"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830763d082aab3cd7c80c9f')
  }
}
db.movies.insert({title:"The Hobbit: The Battle of the Five Armies", writer:"J.R.R Tolkien", year:"2002", franchise:"The Hobbit", synopsis:"Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307649082aab3cd7c80ca0')
  }
}
db.movies.insert({title:"Pee Wee Herman's Big Adventures"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830765b082aab3cd7c80ca1')
  }
}
db.movies.insert({title:"Avatar"})
db.movies.find()
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  year: '1999',
  actors: [
    'Brad Pitt',
    'Edward Norton'
  ]
}
{
  _id: ObjectId('68307626082aab3cd7c80c9c'),
  title: 'Pulp Fiction',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'John Travolta',
    'Uma Thurman'
  ]
}
{
  _id: ObjectId('6830762e082aab3cd7c80c9d'),
  title: 'Inglorious Basterds',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'Brad Pitt',
    'Diane Kruger',
    'Eli Roth'
  ]
}
{
  _id: ObjectId('68307635082aab3cd7c80c9e'),
  title: 'The Hobbit: An unexpected Journey',
  writer: 'J.R.R. Tolkein',
  year: '2012',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('6830763d082aab3cd7c80c9f'),
  title: 'The Hobbit: The Desolation of Smaug',
  writer: 'J.R.R Tolkien',
  year: '2013',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('68307649082aab3cd7c80ca0'),
  title: 'The Hobbit: The Battle of the Five Armies',
  writer: 'J.R.R Tolkien',
  year: '2002',
  franchise: 'The Hobbit',
  synopsis: 'Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness.'
}
{
  _id: ObjectId('6830765b082aab3cd7c80ca1'),
  title: "Pee Wee Herman's Big Adventures"
}
{
  _id: ObjectId('68307663082aab3cd7c80ca2'),
  title: 'Avatar'
}
db.movies.find({writer:"Quentin Tarantino"})
{
  _id: ObjectId('68307626082aab3cd7c80c9c'),
  title: 'Pulp Fiction',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'John Travolta',
    'Uma Thurman'
  ]
}
db.movies.find({actors:"Brad Pitt"})
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  year: '1999',
  actors: [
    'Brad Pitt',
    'Edward Norton'
  ]
}
{
  _id: ObjectId('6830762e082aab3cd7c80c9d'),
  title: 'Inglorious Basterds',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'Brad Pitt',
    'Diane Kruger',
    'Eli Roth'
  ]
}
db.movies.find({franchise:"The Hobbit"})
{
  _id: ObjectId('68307635082aab3cd7c80c9e'),
  title: 'The Hobbit: An unexpected Journey',
  writer: 'J.R.R. Tolkein',
  year: '2012',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('6830763d082aab3cd7c80c9f'),
  title: 'The Hobbit: The Desolation of Smaug',
  writer: 'J.R.R Tolkien',
  year: '2013',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('68307649082aab3cd7c80ca0'),
  title: 'The Hobbit: The Battle of the Five Armies',
  writer: 'J.R.R Tolkien',
  year: '2002',
  franchise: 'The Hobbit',
  synopsis: 'Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness.'
}
db.movies.find({year:{$gt:"1990", $lt:"2000"}})
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  year: '1999',
  actors: [
    'Brad Pitt',
    'Edward Norton'
  ]
}
db.movies.find({$or:[{year:{$gt:"2010"}},{year: {$lt:"2000"}}]})
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  year: '1999',
  actors: [
    'Brad Pitt',
    'Edward Norton'
  ]
}
{
  _id: ObjectId('68307635082aab3cd7c80c9e'),
  title: 'The Hobbit: An unexpected Journey',
  writer: 'J.R.R. Tolkein',
  year: '2012',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('6830763d082aab3cd7c80c9f'),
  title: 'The Hobbit: The Desolation of Smaug',
  writer: 'J.R.R Tolkien',
  year: '2013',
  franchise: 'The Hobbit'
}
db.movies.update({_id:ObjectId("5c9f98e5e5c2dfe9b3729bfe")}, {$set:{synopsis:"A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."}})
DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 0
}
db.movies.update({_id:ObjectId("5c9fa42ae5c2dfe9b3729c03")}, {$set:{synopsis:"The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 0
}
db.movies.update({_id:ObjectId("5c9f983ce5c2dfe9b3729bfc")}, {$push:{actors:"Samuel L. Jackson"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 0
}
db.movies.find({synopsis:{$regex:"Bilbo"}})
{
  _id: ObjectId('68307649082aab3cd7c80ca0'),
  title: 'The Hobbit: The Battle of the Five Armies',
  writer: 'J.R.R Tolkien',
  year: '2002',
  franchise: 'The Hobbit',
  synopsis: 'Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness.'
}
db.movies.find({synopsis:{$regex:"Gandalf"}})
db.movies.find({$and:[{synopsis:{$regex:"Bilbo"}}, {synopsis:{$not:/Gandalf/}}]})
{
  _id: ObjectId('68307649082aab3cd7c80ca0'),
  title: 'The Hobbit: The Battle of the Five Armies',
  writer: 'J.R.R Tolkien',
  year: '2002',
  franchise: 'The Hobbit',
  synopsis: 'Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness.'
}
db.movies.find({$or:[{synopsis:{$regex:"dwarves"}}, {synopsis:{$regex:"hobbit"}}]})
db.movies.find({$and:[{synopsis:{$regex:"gold"}}, {synopsis:{$regex:"dragon"}}]})
db.movies.remove({_id:ObjectId("5c9f992ae5c2dfe9b3729c00")})
DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{
  acknowledged: true,
  deletedCount: 0
}
db.movies.remove({_id:ObjectId("5c9f9936e5c2dfe9b3729c01")})
{
  acknowledged: true,
  deletedCount: 0
}
db.users.insert({_id:1,username:"GoodGuyGreg", first_name:"Good Guy", last_name:"Greg"})
{
  acknowledged: true,
  insertedIds: {
    '0': 1
  }
}
db.users.insert({_id:2, username:"ScumbagSteve", fullname:{first: "Scumbag", last:"Steve"}})
{
  acknowledged: true,
  insertedIds: {
    '0': 2
  }
}
db.posts.insert({username:"GoodGuyGreg", title:"Passes out at Party", body:"Raises your credit score"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307726082aab3cd7c80ca3')
  }
}
db.posts.insert({ username:"GoodGuyGreg", title:"Steals your identity", body:"Raises your credit score"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830772f082aab3cd7c80ca4')
  }
}
db.posts.insert({username:"GoodGuyGreg", title:"Reports a bug in your code", body:"Sends you a pull request"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307737082aab3cd7c80ca5')
  }
}
db.posts.insert({ username:"ScumbagSteve", title:"Borrows something", body:"Sells it"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830773e082aab3cd7c80ca6')
  }
}
db.posts.insert({ username:"ScumbagSteve", title:"Borrows everything", body:"The end"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307744082aab3cd7c80ca7')
  }
}
db.posts.insert({username:"ScumbagSteve", title:"Forks your repo on github", body:"Sets to private"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830774d082aab3cd7c80ca8')
  }
}
db.comments.insert({ username:"GoodGuyGreg", comment:"Hope you got a good deal!", post:ObjectId("5ca0b7e96435f98b5901f463")})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307758082aab3cd7c80ca9')
  }
}
db.comments.insert({username:"GoodGuyGreg", comment:"What's mine is yours!", post:ObjectId("5ca0b9706435f98b5901f46a")})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307760082aab3cd7c80caa')
  }
}
db.comments.insert({username:"GoodGuyGreg", comment:"Don't violate the licensing agreement!", post:ObjectId("5ca0b8766435f98b5901f467")})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307773082aab3cd7c80cab')
  }
}
db.comments.insert({username:"ScumbagSteve", comment:"It still isn't clean", post:ObjectId("5ca0b8546435f98b5901f466")})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830777a082aab3cd7c80cac')
  }
}
db.comments.insert({username:"ScumbagSteve", comment:"Denied your PR cause I found a hack", post:ObjectId("5ca0b9256435f98b5901f469")})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307786082aab3cd7c80cad')
  }
}
db.users.find().pretty()
{
  _id: 1,
  username: 'GoodGuyGreg',
  first_name: 'Good Guy',
  last_name: 'Greg'
}
{
  _id: 2,
  username: 'ScumbagSteve',
  fullname: {
    first: 'Scumbag',
    last: 'Steve'
  }
}
db.posts.find().pretty()
{
  _id: ObjectId('68307726082aab3cd7c80ca3'),
  username: 'GoodGuyGreg',
  title: 'Passes out at Party',
  body: 'Raises your credit score'
}
{
  _id: ObjectId('6830772f082aab3cd7c80ca4'),
  username: 'GoodGuyGreg',
  title: 'Steals your identity',
  body: 'Raises your credit score'
}
{
  _id: ObjectId('68307737082aab3cd7c80ca5'),
  username: 'GoodGuyGreg',
  title: 'Reports a bug in your code',
  body: 'Sends you a pull request'
}
{
  _id: ObjectId('6830773e082aab3cd7c80ca6'),
  username: 'ScumbagSteve',
  title: 'Borrows something',
  body: 'Sells it'
}
{
  _id: ObjectId('68307744082aab3cd7c80ca7'),
  username: 'ScumbagSteve',
  title: 'Borrows everything',
  body: 'The end'
}
{
  _id: ObjectId('6830774d082aab3cd7c80ca8'),
  username: 'ScumbagSteve',
  title: 'Forks your repo on github',
  body: 'Sets to private'
}
db.posts.find({username:"GoodGuyGreg"})
{
  _id: ObjectId('68307726082aab3cd7c80ca3'),
  username: 'GoodGuyGreg',
  title: 'Passes out at Party',
  body: 'Raises your credit score'
}
{
  _id: ObjectId('6830772f082aab3cd7c80ca4'),
  username: 'GoodGuyGreg',
  title: 'Steals your identity',
  body: 'Raises your credit score'
}
{
  _id: ObjectId('68307737082aab3cd7c80ca5'),
  username: 'GoodGuyGreg',
  title: 'Reports a bug in your code',
  body: 'Sends you a pull request'
}
db.posts.find({username:"ScumbagSteve"})
{
  _id: ObjectId('6830773e082aab3cd7c80ca6'),
  username: 'ScumbagSteve',
  title: 'Borrows something',
  body: 'Sells it'
}
{
  _id: ObjectId('68307744082aab3cd7c80ca7'),
  username: 'ScumbagSteve',
  title: 'Borrows everything',
  body: 'The end'
}
{
  _id: ObjectId('6830774d082aab3cd7c80ca8'),
  username: 'ScumbagSteve',
  title: 'Forks your repo on github',
  body: 'Sets to private'
}
db.comments.find().pretty()
{
  _id: ObjectId('68307758082aab3cd7c80ca9'),
  username: 'GoodGuyGreg',
  comment: 'Hope you got a good deal!',
  post: ObjectId('5ca0b7e96435f98b5901f463')
}
{
  _id: ObjectId('68307760082aab3cd7c80caa'),
  username: 'GoodGuyGreg',
  comment: "What's mine is yours!",
  post: ObjectId('5ca0b9706435f98b5901f46a')
}
{
  _id: ObjectId('68307773082aab3cd7c80cab'),
  username: 'GoodGuyGreg',
  comment: "Don't violate the licensing agreement!",
  post: ObjectId('5ca0b8766435f98b5901f467')
}
{
  _id: ObjectId('6830777a082aab3cd7c80cac'),
  username: 'ScumbagSteve',
  comment: "It still isn't clean",
  post: ObjectId('5ca0b8546435f98b5901f466')
}
{
  _id: ObjectId('68307786082aab3cd7c80cad'),
  username: 'ScumbagSteve',
  comment: 'Denied your PR cause I found a hack',
  post: ObjectId('5ca0b9256435f98b5901f469')
}
db.comments.find({username:"GoodGuyGreg"})
{
  _id: ObjectId('68307758082aab3cd7c80ca9'),
  username: 'GoodGuyGreg',
  comment: 'Hope you got a good deal!',
  post: ObjectId('5ca0b7e96435f98b5901f463')
}
{
  _id: ObjectId('68307760082aab3cd7c80caa'),
  username: 'GoodGuyGreg',
  comment: "What's mine is yours!",
  post: ObjectId('5ca0b9706435f98b5901f46a')
}
{
  _id: ObjectId('68307773082aab3cd7c80cab'),
  username: 'GoodGuyGreg',
  comment: "Don't violate the licensing agreement!",
  post: ObjectId('5ca0b8766435f98b5901f467')
}
db.comments.find({username:"ScumbagSteve"})
{
  _id: ObjectId('6830777a082aab3cd7c80cac'),
  username: 'ScumbagSteve',
  comment: "It still isn't clean",
  post: ObjectId('5ca0b8546435f98b5901f466')
}

