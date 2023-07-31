<a name="readme-top"></a>

# MongoDB

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#Insert many documents in a collection">Insert many documents in a collection</a>
    </li>
    <li>
      <a href="#Shearch by field">Shearch by field</a>
    </li>
    <li>
      <a href="#Search between dates">Search between dates</a>
    </li>
    <li><a href="#Update a document by _id">Update a document by _id</a></li>
    <li><a href="#Search by field that match regex">Search by field that match regex</a></li>
    <li><a href="#Search by fields that match regex - OR">Search by fields that match regex - OR</a></li>
    <li><a href="#Search by fields that match regex - AND">Search by fields that match regex - AND</a></li>
    <li><a href="#Delete document by _id">Delete document by _id</a></li>
    <li><a href="#Unset a document field that match">Unset a document field that match</a></li>
  </ol>
</details>

---

#### Insert many documents in a collection 

```bash
db.movies.insertMany([{title:'Fight Club',writer: 'Chuck Palahniuk',year: 1999,actors: ['Brad Pitt', 'Edward Norton']},{title: 'Pulp Fiction',writer: 'Quentin Tarantino',year: 1994,actors: ['John Travolta', 'Uma Thurman']},{title: 'Inglourious Basterds',writer: 'Quentin Tarantino',year: 2009,actors: ['Brad Pitt', 'Diane Kruger', 'Eli Roth']},{title:'The Hobbit: An Unexpected Journey',writer: 'J.R.R. Tolkien',year: 2012,franchise:'The Hobbit'},{title: 'The Hobbit: The Desolation of Smaug',writer: 'J.R.R. Tolkien',year: 2013,franchise: 'The Hobbit'},{title: 'The Hobbit: The Battle of the Five Armies',writer: 'J.R.R. Tolkien',year: 2014,franchise: 'The Hobbit',synopsis: 'Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness.'},{title: 'Pee-wee s Big Adventure',year: 1985},{title: 'Avatar',year: 2009}])
```

#### Shearch by field

```bash
db.movies.find({writer:'Quentin Tarantino'})
```

```bash
db.movies.find({actors:'Brad Pitt'})
```

```bash
db.movies.find({franchise:'The Hobbit'})
```

#### Search between dates

```bash
db.movies.find({year:{$gte:1900, $lte:1999}})
```

```bash
db.movies.find({year:{$gte:2000, $lte:2010}})
```

#### Update a document by `_id`

```bash
db.movies.updateOne({_id: ObjectId("64b7f90c4a448846c65d6fd3")},{$set:{synopsis: 'A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with spirited group of dwarves to reclaim their montain home-and the gold within it- from the dragon Smaug.'}})
```

```bash
db.movies.updateOne({_id: ObjectId("64b7f90c4a448846c65d6fd4")},{$set:{synopsis: 'The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring.'}})
```

#### Search by field that match regex

```bash
db.movies.find({title: {$regex:"Hobbit"}})
```

```bash
db.movies.find({synopsis: {$regex:"Gandalf"}})
```

#### Search by fields that match regex - OR

```bash
db.movies.find({ "$or": [{"synopsis": {"$regex": "dwarves"} }, {"synopsis": {"$regex": "hobbit" }}]})
```

#### Search by fields that match regex - AND

```bash
db.movies.find({ "$and": [{"synopsis": {"$regex": "gold"} }, {"synopsis": {"$regex": "dragon" }}]})
```

```bash
db.movies.find({ "$and": [{"synopsis": {"$regex": "Bilbo"} }, {"synopsis":  {$not: {"$regex": "Gandalf" }}}]})
```

#### Delete document by `_id`

```bash
db.movies.deleteOne({_id: ObjectId("64b7f90c4a448846c65d6fd7")})
```

#### Unset a document field that match

```bash
db.movies.updateOne({title: 'Pee-wee s Big Adventure'},{ $unset: {title:''}})
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>