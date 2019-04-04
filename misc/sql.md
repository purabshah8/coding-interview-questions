# SQL Questions

## Online Music Store DB

### Description
A database for music store where customers can find and buy music

### Tables
Tracks
Artists
Albums
Customers
Invoices
Invoice Items
Employees
Playlist
PlaylistTrack
Genre


1) create a database for music
2) add playlists feature
3) add feature: buying music from employees

### Queries


Get the top 10 artists with the most songs on playlists sorted by number of tracks

```sql
SELECT 
    artists.name, COUNT(tracks.id) as "Appearances"
FROM 
    artists
JOIN 
    albums ON albums.artist_id = artists.id
JOIN
    tracks ON tracks.album_id = albums.id
JOIN
    playlist_track ON playlist_track.track_id = tracks.id;
GROUP BY 
    artists.name
ORDER BY 
    COUNT(tracks.id)
LIMIT 10;
```

Find the tracks sold by genre, ordering by amount sold
```sql
SELECT 
    genre.name, SUM(invoice_item.quantity) as "tracks sold"
FROM
    invoice_item
JOIN
    track ON track.id = invoice_item.track_id
JOIN
    genre ON track.genre_id = genre.id
GROUP BY
    genre.name
ORDER BY
    "tracks sold" 
DESC;

```


Find the customers who have spent the most money on purchases, ordered by $$
```sql

```



## School DB

Tables



Students
id
name

Classes
id
name
dept_id
professor_id

Professors
id 
name

Enrollments
class_id
student_id

Departments
id
name

Sample Questions:
Find count of classes for a student

SELECT students.name, COUNT(enrollments.class_id) FROM students LEFT JOIN enrollments ON enrollments.student_id GROUP BY students.name

Find students with more than 3 classes

Find professor with largest class

Find avg class size for a dept


```sql

SELECT 
    users.name, properties.name, avg_rating
FROM
    properties
JOIN
    ratings on properties.id = ratings.rated_id
JOIN
    users on users.id = 
```