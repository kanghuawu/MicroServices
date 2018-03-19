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
