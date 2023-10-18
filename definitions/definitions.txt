Jeg har prøvd meg på en metadatadefinisjon og lest meg opp på [definisjoner og variable](https://www.microdata.no/wp-content/uploads/2022/06/Key-Architecture-Choices-in-Microdata.pdf). Men jeg synes det er vanskelig når alle konseptene er nye :sweat_smile:
Her er et forenklet eksempel på data vi har med Antallet av og påstigninger summert over en måned, på et gitt stoppested i en gitt retning på en gitt linje

+-------+---------+-------+------------+---------+-------------------+-------------------+---------------+
| uuid  | år-mnd  | linje | stoppested | retning | antall som går på | antall som går av | passasjertall |
+-------+---------+-------+------------+---------+-------------------+-------------------+---------------+
| uuid1 | 2023-05 | 10    | NSR:10     | 1       | 2000              | 1888              | 5000          |
+-------+---------+-------+------------+---------+-------------------+-------------------+---------------+

Jeg har prøvd å splitte det på til en datum-based approach som her

Temporality type: FIXED
+-------+---------------+---------+------------+----------+
| uuid  | var_ref       | value   | start_date | end_date |
+-------+---------------+---------+------------+----------+
| uuid1 | linje         | 10      |            |          |
+-------+---------------+---------+------------+----------+
| uuid1 | Stoppested    | NSR:10  |            |          |
+-------+---------------+---------+------------+----------+
| uuid1 | Retnign       | 1       |            |          |
+-------+---------------+---------+------------+----------+

Temporality type: ACCUMULATED
+-------+---------------+---------+------------+----------+
| uuid1 | boarding_sum  | 2000    |            |          |
+-------+---------------+---------+------------+----------+
| uuid1 | alighting_sum | 1888    |            |          |
+-------+---------------+---------+------------+----------+
| uuid1 | passasjertall | 5000    |            |          |
+-------+---------------+---------+------------+----------+
