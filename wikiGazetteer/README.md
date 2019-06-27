## WikiGazetteer

Gazetteer generated from Wikipedia and enriched with Geonames data. Data used to create it:
$ https://dumps.wikimedia.org/enwiki/20190320/enwiki-20190320-redirect.sql.gz
$ https://dumps.wikimedia.org/enwiki/20190320/enwiki-20190320-page.sql.gz
$ https://dumps.wikimedia.org/enwiki/20190320/enwiki-20190320-geo_tags.sql.gz
$ http://download.geonames.org/export/dump/cities500.zip
$ http://download.geonames.org/export/dump/alternateNamesV2.zip
$ https://github.com/alan-turing-institute/Living-with-Machines-code/blob/master/language-lab-mro/gazetteer_construction/locdisENinlinks.json (not open-access yet)

### Tables in gazetteer:

* Table `location`:
  * `id`: id of the location in the gazetteer
  * `wiki_id`: id of the corresponding wikipedia entry (wikipedia `page.page_id`)
  * `wikigt_id`: id of the corresponding entry in wikipedia `geo_tags` table (wikipedia `geo_tags.gt_id`)
  * `geo_id`: id of the corresponding entry in geonames (geonames `geoname.id`)
  * `wiki_title`: wikipedia title, which is the last part of a Wikipedia URL (wikipedia `page.page_title`)
  * `page_len`: wikipedia page length (wikipedia `page.page_len`)
  * `lat`: latitude corresponding to the location (wikipedia `geo_tags.gt_lat`)
  * `lon`: longitude corresponding to the location (wikipedia `geo_tags.gt_lat`) 
  * `dim`: approximate size of an object, default in metres, optional km suffix (wikipedia `geo_tags.dim`)
  * `type`: type of object with these coordinates, can be one of the following: country, satellite, state, adm1st, adm2nd, adm3rd, city, isle, mountain, river, waterbody, event, forest, glacier, airport, railwaystation, edu, pass, camera, landmark (wikipedia `geo_tags.type`)
  * `country`: country code of location (wikipedia `geo_tags.country` and geonames `geoname.countrycode`)
  * `region`: region of location (wikipedia `geo_tags.region`)
  * `population`: population of location if populated place (geonames `geoname.population`)

* Table `altname`:
  * `id`: id of the altname in the gazetteer
  * `main_id`: reference to `location.id`
  * `altname`: alternate name of the location
  * `source`: source of the alternate name. Types:
    * `wikimain`: Wikipedia title, cleaned (wikipedia `page.page_title`)
    * `wikiredirect`: Wikipedia title of a redirecting page, cleaned (wikipedia `page.page_title`)
    * `geonamesmain`: Main geonames name of location (geonames `geoname.name`)
    * `geonamesascii`: Main geonames name of location, ascii-ed, if different (geonames `geoname.asciiname`)
    * `geonamesalt`: Alternate name from geonames (geonames `alternateNamesV2.alternatename`)

* Table `inlinks`: (minimal approach, see below for proper approach):
  * `main_id`: reference to `location.id`
  * `inlinks`: number of pages linking to this location's page in Wikipedia.

### Examples of queries:

Return all locations that may be known as "Barcelona":
```
mysql> SELECT wiki_title, lat, lon, type, country, region FROM location
JOIN altname ON altname.main_id=location.id
WHERE altname="Barcelona";

+--------------------------------------------------+----------+----------+--------+---------+--------+
| wiki_title                                       | lat      | lon      | type   | country | region |
+--------------------------------------------------+----------+----------+--------+---------+--------+
| Barcelona                                        |  41.3833 |  2.18333 | city   | ES      | NULL   |
| Province_of_Barcelona                            |    41.45 |  2.08333 | adm2nd | ES      | NULL   |
| Sorsogon                                         |  12.8663 |  124.145 | city   | PH      | SOR    |
| Blooming_Grove,_Ohio                             |  40.7078 | -82.7167 | city   | US      | OH     |
| Barcelona,_Venezuela                             |  10.1167 | -64.7167 | city   | NULL    | NULL   |
| Barcelona,_Sorsogon                              |    12.87 |   124.13 | NULL   | PH      | NULL   |
| Barcelona_(Congress_of_Deputies_constituency)    |    41.45 |  2.08333 | NULL   | NULL    | NULL   |
| Barcelona,_Cornwall                              |  50.3552 |  -4.5047 | NULL   | NULL    | NULL   |
| Barcelona,_Rio_Grande_do_Norte                   | -5.93333 | -35.9333 | city   | BR      | NULL   |
| Barcelona,_Arkansas                              |  35.6206 | -94.4561 | city   | US      | AR     |
| Barcelona_(Parliament_of_Catalonia_constituency) |    41.45 |  2.08333 | NULL   | NULL    | NULL   |
+--------------------------------------------------+----------+----------+--------+---------+--------+
11 rows in set (0.49 sec)
```

Return all possible names for Quebec City: 
```
mysql> SELECT altname, source, wiki_title FROM altname
JOIN location ON location.id=altname.main_id
WHERE wiki_title="Quebec_City"

+------------------+---------------+-------------+
| altname          | source        | wiki_title  |
+------------------+---------------+-------------+
| Quebec City      | wikimain      | Quebec_City |
| Quebec llaqta    | geonamesalt   | Quebec_City |
| Siudad ti Quebec | geonamesalt   | Quebec_City |
| Kota Quebec      | geonamesalt   | Quebec_City |
| Quebecstad       | geonamesalt   | Quebec_City |
...
| Kebek            | geonamesalt   | Quebec_City |
| Kebeku           | geonamesalt   | Quebec_City |
| Quebecum urbs    | geonamesalt   | Quebec_City |
| Kvebeka          | geonamesalt   | Quebec_City |
| Kebeko           | geonamesalt   | Quebec_City |
+------------------+---------------+-------------+
23 rows in set (0.38 sec)
```
Note: Wiki URL for Quebec City is `https://en.wikipedia.org/wiki/Quebec_City`, so `wiki_title` is just `Quebec_City`)

Return number wiki title and number of inlinks for all locations that may be known as "Barcelona":
```
mysql> SELECT location.wiki_title, inlinks.inlinks FROM location
JOIN altname ON altname.main_id=location.id
JOIN inlinks on inlinks.main_id=location.id
WHERE altname="Barcelona";

+--------------------------------------------------+---------+
| wiki_title                                       | inlinks |
+--------------------------------------------------+---------+
| Barcelona                                        |    3874 |
| Province_of_Barcelona                            |     215 |
| Sorsogon                                         |     135 |
| Blooming_Grove,_Ohio                             |       9 |
| Barcelona,_Venezuela                             |      12 |
| Barcelona,_Sorsogon                              |      15 |
| Barcelona_(Congress_of_Deputies_constituency)    |      25 |
| Barcelona,_Cornwall                              |       1 |
| Barcelona,_Rio_Grande_do_Norte                   |       2 |
| Barcelona,_Arkansas                              |       5 |
| Barcelona_(Parliament_of_Catalonia_constituency) |       0 |
+--------------------------------------------------+---------+
11 rows in set (0.53 sec)

```
