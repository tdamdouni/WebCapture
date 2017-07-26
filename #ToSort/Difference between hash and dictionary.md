# Difference between hash and dictionary

**`Hash`** is an extremely poorly named data structure where the programmer has confused the interface with implementation (_and_ was too lazy to write the full name, i.e. `HashTable` instead resorting to an abbreviation, `Hash`).

**`Dictionary`** is the [“correct” name](http://xlinux.nist.gov/dads/HTML/dictionary.html) of the interface (= the [ADT](http://xlinux.nist.gov/dads/HTML/abstractDataType.html)), i.e. an associative container that maps (usually unique) keys to (not necessarily unique) values.

A hash table is _one_ possible implementation of such a dictionary that provides quite good access characteristics (in terms of runtime) and is therefore often the default implementation.

Such an implementation has two important properties:

  1. the keys have to be _hashable_ and _equality comparable_.
  2. the entries appear in no particular order in the dictionary.

(For a key to be hashable means that we can compute a numeric value from a key which is subsequently used as an index in an array.)

There exist alternative implementations of the dictionary data structure that impose an _ordering_ on the keys – this is often called a _sorted_ dictionary (and is usually implemented in terms of a search tree, though other efficient implementations exist).

* * *

To summarize: a _dictionary_ is an ADT that maps keys to values. There are several possible implementations of this ADT, of which the _hash table_ is one. `Hash` is a misnomer but in context it’s equivalent to a dictionary that is implemented in terms of a hash table.

---

A dictionary is the collective term given for any data structure implementation used for fast lookups/insertions. This can be achieved/implemented using a variety of data structures like hash table, skip lists, rb tree etc. A hash table is a specific data structure useful for many purposes including implementing a dictionary.

---

"Dictionary" is the name of the concept. A hashtable is a possible implementation.

---

A **dictionary** uses a key to reference the value directly inside of an **associative array**.

i.e `(KEY => VALUE)`

A **hash** is more often described as a **hash table** which uses a **hash function** to calculate the position in memory (or more easily an array) where the value will be. _The hash will take the KEY as input and give a value as output. Then plug that value into the memory or array index._

i.e `KEY => HASH FUNCTION => VALUE`

I guess one is direct while the other isn't. Hash functions may not be perfect either and may sometimes provide an index referencing the wrong value. But that can be corrected.

Best place to look: Wikipedia (_associative array_ and _hash table_)


