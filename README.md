

# SQL and ActiveRecord

# 1a) Find the genre with the name "Hip Hop/Rap".

  Genre.where(name:'Hip Hop/Rap')

# 1b) Count how many tracks belong to the "Hip Hop/Rap" genre

  Genre.where(name:'Hip Hop/Rap').count

# 2) Find the total amount of time required to listen to all the tracks in the database.

  Track.sum("milliseconds")

# 3a) Find the highest price of any track that has the media type "MPEG audio file".

    Track.where(media_type_id:MediaType.where(name:'MPEG audio file').first.id
    ).maximum('unit_price')

# 3b) Find the name of the most expensive track that has the media type "MPEG audio file".

    Track.where(media_type_id:MediaType.where(name:'MPEG audio file').first.id, unit_price:Track.where(media_type_id:MediaType.where(name:'MPEG audio file').first.id
    ).maximum('unit_price')
    ).first.name

# 4) Find the 2 oldest artists.

    Artist.order(created_at: :asc).first(2)

* Columns: attributes, name, data type

* Row: Record, represents a set of data for each column

* Primary key: `id` unique
  * can be an integer (starts at 1 and 10000000)
  * UUID 349tu-hbe0984-5hww9e8y5h

* Foreign key:
Allows you to associate to another table
`objectname_id`

----------------------------------------------------------
Read on ACID
Sanitization  -  looking at basically the valid input
find_by - It gives you back an ActiveRecord
where - returns an array of objects ("NOT specific")

-- You can chain methods on Records of a database

---------------------Migrations----------------------------

DDL -- Changes the structure the datatbase
