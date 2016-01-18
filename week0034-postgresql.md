# Week 0034 "PostgreSQL"
**2015-01-18**

Topic: Hello PostgreSQL

Mike Putnam will demonstrate some basic functionality of PostgreSQL 9.5.

* Setting up [a Postgres sandbox virtual machine with vagrant](https://github.com/jackdb/pg-app-dev-vm)
* Basic SQL exection (sample below)
* Documentation
    * [General](http://www.postgresql.org/docs/9.5/static/index.html)
    * [SQL Commands](http://www.postgresql.org/docs/9.5/static/sql-commands.html)
* Tools `psql` and [pgadmin3](http://www.pgadmin.org/docs/1.22/index.html)
* Libraries / db <-> language drivers. Python [psycopg2](http://initd.org/psycopg/docs/index.html), ORMs, etc.
* How not to write SQL injectable python according to psycopg2 "Warning Never, never, NEVER use Python string concatenation (+) or string parameters interpolation (%) to pass variables to a SQL query string. Not even at gunpoint."

===
```
ALTER ROLE codercooperative SET client_encoding TO 'utf8';
ALTER ROLE codercooperative SET default_transaction_isolation TO 'read committed'; --blocks reads from uncommitted transactions
ALTER ROLE codercooperative SET timezone TO 'UTC';

DROP TABLE topics CASCADE;
DROP TABLE meetups CASCADE;
DROP TABLE attendees CASCADE;
DROP TABLE person CASCADE;

CREATE TABLE topics (
    topic_id serial PRIMARY KEY,
    topic_descr VARCHAR(35) NOT NULL
);
CREATE TABLE meetups (
    meetup_id serial PRIMARY KEY,
    meetup_timestamp TIMESTAMP WITH TIME ZONE NOT NULL DEFAULT NOW(),
    topic_id integer REFERENCES topics
);
CREATE TABLE person (
    person_id serial PRIMARY KEY,
    person_name VARCHAR(35) NULL DEFAULT 'Undefined'
);
CREATE TABLE attendees (
    attendee_id serial PRIMARY KEY,
    person_id integer REFERENCES person,
    meetup_id integer REFERENCES meetups
);

INSERT INTO topics (topic_descr) VALUES ('Open Topic');
INSERT INTO topics (topic_descr) VALUES ('PostgreSQL');
INSERT INTO topics (topic_descr) VALUES ('Git/Github');
INSERT INTO topics (topic_descr) VALUES ('Intro to SQL');
INSERT INTO topics (topic_descr) VALUES ('Intro to Android');
INSERT INTO topics (topic_descr) VALUES ('Timezones');
INSERT INTO topics (topic_descr) VALUES ('Google Calendar API via Python');
INSERT INTO topics (topic_descr) VALUES ('Lets List Our Liked Libraries!');
INSERT INTO topics (topic_descr) VALUES ('Crash Course in Command Line');

INSERT INTO person (person_name) VALUES ('Mike');
INSERT INTO person (person_name) VALUES ('Justin');
INSERT INTO person (person_name) VALUES ('Irena');
INSERT INTO person (person_name) VALUES ('Kristen');
INSERT INTO person (person_name) VALUES ('Bob');

INSERT INTO meetups (meetup_timestamp,topic_id) VALUES ('2016-01-17 00:00:00',2);

INSERT INTO attendees (person_id,meetup_id) VALUES (1,1);
INSERT INTO attendees (person_id,meetup_id) VALUES (2,1);
INSERT INTO attendees (person_id,meetup_id) VALUES (4,1);

SELECT * FROM topics;
SELECT * FROM meetups;
SELECT * FROM person;
SELECT * FROM attendees;

SELECT A.person_name, B.topic_descr
FROM person AS A, topics as B, meetups as C, attendees as D
WHERE C.topic_id = B.topic_id
AND A.person_id = D.person_id
AND C.topic_id = B.topic_id

UPDATE topics SET topic_descr = 'Intro to PostgreSQL' WHERE topic_id = 2;
```
===

After report:

