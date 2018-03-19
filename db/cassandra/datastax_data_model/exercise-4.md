
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
