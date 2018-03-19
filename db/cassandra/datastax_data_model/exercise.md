## Exercise 2

```sql
CREATE KEYSPACE  killrvideo WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};
USE killrvideo;
CREATE TABLE videos (
  video_id timeuuid,
  added_date timestamp,
  description text,
  title text,
  user_id uuid,
  PRIMARY KEY (video_id));
DESCRIBE TABLE videos;
COPY videos from 'videos.csv' WITH HEADER = true;
SELECT * FROM videos LIMIT 10;
SELECT COUNT(*) FROM videos;
```

## Exercise 3

```sql
USE killrvideo;
CREATE TABLE videos_by_title_year (
  title text, 
  added_year int, 
  added_date timestamp, 
  description text, 
  user_id uuid, 
  video_id timeuuid, 
PRIMARY KEY((title, added_year)));
COPY videos_by_title_year FROM 'videos_by_title_year.csv' WITH HEADER=true;
SELECT title, added_year FROM videos_by_title_year WHERE title = 'Sleepy Grumpy Cat' AND added_year = 2015;
SELECT title, added_year FROM videos_by_title_year WHERE added_year = 2015; # throw error
```

## Exercise 4

```sql
CREATE TABLE videos_by_tag_year (
  tag text,
  added_year int,
  video_id timeuuid,
  added_date timestamp,
  description text,
  title text,
  user_id uuid,
  PRIMARY KEY ((tag), added_year, video_id)
) WITH CLUSTERING ORDER BY (added_year DESC);

SELECT title FROM videos_by_tag_year WHERE tag = 'cql';

SELECT title FROM videos_by_tag_year WHERE tag = 'cql' and added_year < 2016;

SELECT title FROM videos_by_tag_year WHERE tag = 'cql' and added_year < 2016;

SELECT title FROM videos_by_tag_year WHERE tag = 'cql' and added_year = 2014;

SELECT COUNT(*) FROM videos_by_tag_year WHERE tag = 'trailer';

SELECT COUNT(*) FROM videos_by_tag_year;
```

## Exercise 5

```sql
TRUNCATE videos;

ALTER TABLE videos ADD tags set<text>;

COPY videos FROM 'videos.csv' WITH HEADER=true;

CREATE TYPE video_encoding (bit_rates set<text>, encoding text, height int, width int);

ALTER TABLE videos ADD encoding frozen <video_encoding>;

COPY videos (video_id, encoding) FROM 'videos_encoding.csv' WITH HEADER=true;

SELECT title, encoding, tags FROM videos LIMIT 10;
```

## Exercise 6

```sql
CREATE TABLE videos_count_by_tag (
  tag text, 
  added_year int, 
  video_count counter, 
PRIMARY KEY((tag, added_year)));

SOURCE 'videos_count_by_tag.cql';

SELECT * FROM videos_count_by_tag LIMIT 10 ;

# update data in first row
UPDATE videos_count_by_tag SET video_count = video_count + 2 WHERE tag = 'dse' AND added_year = 2015;

SELECT * FROM videos_count_by_tag LIMIT 10 ;
```
