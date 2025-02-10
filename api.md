# API REFERENCE

Let's look at some functions and structs used that you can use.


# `data_block` struct
```rs
#[derive(Debug)]
pub struct data_block {
    key: &'static str, // a key
    value: &'static str, // a value
}
```
This struct is the primitive form of data that can be used in a DB<br>
# `db` struct
```rs
#[derive(Debug)]
pub struct db {
    id: &'static str, // the database identifier
    data: [data_block; 50], // an array of data blocks
}
```
This struct is the primitive data block storage system<br>

`std::fmt::Display` is implemented for both structs, which means you can print them out with `println!()`<br>

# `data_block::new(&self, key: &'static str, value: &'static str) -> data_block`
For the `data_block` struct, there is a `new()` method used for instantiating a new data block.

Example usage: 
```rs
let datablock = data_block::new("age", "16");
```


# `db::new(id: &'static str) -> db`
For the `db` struct, there is also a `new()` method used for instantiating new databases.

Example usage:
```rs
let db = db::new("database 1");
```

# `db.write_out(&self, path: &str)`
To write out a db's data to a file, use this function.

Example usage: 
```rs
let db = db::new("test db");
db.write_out("my_path")
```

# `pub fn db_add_data(db: &mut db, datablock: data_block)`

To add data to a db, use this function.

Example usage:
```rs
db_add_data(my_db, my_datablock);
```

# `pub fn db_read(db: &db, key: &'static str) -> Option<&'static str>`

To read a value from a db, use this method.

Example usage:
```rs
let jakes_age = db_read(people, "jake");
```

# `pub fn db_empty(mut db: db)` 

To clear a db (set everything to "")

Example usage:
```rs
db_empty(my_db);
```