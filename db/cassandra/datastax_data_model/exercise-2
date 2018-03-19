CREATE KEYSPACE  killrvideo WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};
USE killrvideo;
CREATE TABLE videos (
... video_id timeuuid,
... added_date timestamp,
... description text,
... title text,
... user_id uuid,
... PRIMARY KEY (video_id));
cqlsh:killrvideo> DESCRIBE TABLE videos;
cqlsh:killrvideo> COPY videos from 'videos.csv' WITH HEADER = true;
cqlsh:killrvideo> SELECT * FROM videos LIMIT 10;
cqlsh:killrvideo> SELECT COUNT(*) FROM videos;
