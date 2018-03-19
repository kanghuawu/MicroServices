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
