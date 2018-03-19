```sql
TRUNCATE videos;

ALTER TABLE videos ADD tags set<text>;

COPY videos FROM 'videos.csv' WITH HEADER=true;

CREATE TYPE video_encoding (bit_rates set<text>, encoding text, height int, width int);

ALTER TABLE videos ADD encoding frozen <video_encoding>;

COPY videos (video_id, encoding) FROM 'videos_encoding.csv' WITH HEADER=true;

SELECT title, encoding, tags FROM videos LIMIT 10;
```
