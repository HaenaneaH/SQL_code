# SQL_code
SQL 실습용
SELECT COUNT(*) FROM sample51;
SELECT COUNT(*) FROM sample51;

SELECT * FROM sample51 WHERE name = 'A';
SELECT COUNT(*) FROM sample51 WHERE name = 'A';

SELECT * FROM sample51;
SELECT COUNT(no) , COUNT(name) FROM sample51;

SELECT  ALL name FROM sample51;
SELECT DISTINCT name FROM sample51;

SELECT COUNT(ALL name) , COUNT(DISTINCT name) FROM sample51;

SELECT SUM(quantity) FROM sample51;

SELECT AVG( quantity), SUM(quantity)/COUNT(quantity) FROM sample51;

SELECT AVG(CASE WHEN quantity lS NULL THEN 0 ELSE quantity END)
  AS avgnull0 FROM sample51;

SELECT M1N(quantity) , MAX(quantity), M1N(name), MAX(name)
  FROM sample51;

SELECT name FROM sample51 GROUP BY name;

SELECT name, COUNT(name), SUM(quantity)
   FROM sample51 GROUP BY name;

SELECT name, COUNT(name) FROM sample51
  WHERE COUNT(name) = 1 GROUP BY name;

SELECT name, COUNT(name) FROM sample51 GROUP BY name;
SELECT name, COUNT(name) FROM sample51
  GROUP BY name HAVING COUNT(name) = 1;

SELECT name AS n, COUNT(name) AS cn
  FROM sample51 GROUP BY n HAVING cn = 1;

SELECT MIN(no), name, SUM(quantity) FROM sample51 GROUP BY name;

SELECT name, quantity FROM sample51 GROUP BY name, quantity;

SELECT name, COUNT(name), SUM(quantity)
  FROM sample51 GROUP BY name ORDER BY SUM(quantity) DESC;

DELETE FROM sample54 WHERE a = (SElECT MIN(a) FROM sample54);
SELECT * FROM sample54;

SELECT MIN(a) FROM sample54;
SELECT no FROM sample54;
SELECT MIN(a), MAX(no) FROM sample54;
SELECT no, a FROM sample54;

DELETE FROM sample54 WHERE a = (SELECT MIN(a) FROM sample54);

SELECT
  (SELECT COUNT(*) FROM sample51 ) AS sq1,
  (SELECT COUNT(*) FROM sample54) AS sq2;

SELECT
  (SELECT COUNT(*) FROM sample51 ) AS sq1,
  (SELECT COUNT(*) FROM sample54) AS sq2 FROM DUAL;

UPDATE sample54 SET a = (SELECT MAX(a) FROM sample54);

SELECT * FROM (SELECT * FROM sample54) sq;

SELECT * FROM (SELECT * FROM sample54) AS sq;

SELECT * FROM (SELECT * FROM (SELECT * FROM sample54) sq1) sq2;

INSERT INTO sample541 VALUES (
 (SELECT COUNT(*) FROM sample51),
 (SELECT COUNT(*) FROM sample54)
);
SELECT * FROM sample541;

INSERT INTO sample541 SELECT 1, 2;
SELECT * FROM sample541;

INSERT INTO sample542 SELECT * FROM sample543;

UPDATE sample551 SET a = '있음' WHERE
EXISTS (SELECT * FROM sample 552 WHERE no2 = no);
SELECT * FROM sample551;

UPDATE sample551 SET a = '없음'， WHERE
NOT EXISTS (SELECT * FROM sample552 WHERE no2 = no);
SELECT * FROM sample551;

UPDATE sample551 SET a = '있음' WHERE
  EXISTS (SELECT * FROM sample552 WHERE sample552.no2 = sample551.no);

SELECT * FROM sample551 WHERE no IN (3 , 5);

SELECT * FROM sample551 WHERE no IN
   (SELECT no2 FROM sample 552);

CREATE TABLE sample62 (
  no INTEGER NOT NULL,
  a VARCHAR(30),
  b DATE);
DESC sample62;

ALTER TABLE sample62 MODIFY newcol VARCHAR(20);
DESC sample62;

ALTER TABLE sample62 CHANGE newcol c VARCHAR(20);
DESC sample62;

CREATE TABLE smalpe631 (
    a INTEGER NOT NULL,
    b INTEGER NOT NULL UNIQUE,
    c VARCHAR(30)
);

CREATE TABLE sample632 (
  no INTEGER NOT NULL,
  sub_no INTEGER NOT NULL,
  name VARCHAR(38),
  PRIMARY KEY (no, sub_no)
);

CREATE TABLE sample632 (
  no INTEGER NOT NULL,
  sub_no INTEGER NOT NULL,
  name VARCHAR (30),
  CONSTRAINT pkey_sample PRIMARY KEY (no, sub_no)
);

ALTER TABLE sample631 MODIFY c VARCHAR (30) NOT NULl;

ALTER TABLE sample631 ADD CONSTRAINT pkey_sample631 PRIMARY KEY(a);

ALTER TABLE sample631 MODIFY c VARCHAR(30);

ALTER TABLE sample631 DROP CONSTRAINT pkey_sample631;

ALTER TABLE sample631 DROP PRIMARY KEY;

CREATE TABLE sample634(
  p INTEGER NOT NULL,
  a VARCHAR(30),
  CONSTRAINT pkey_sample634 PRIMARY KEY(p)
);

INSERT INTO sample634 VALUES (2 , '넷째줄');
ERROR 1062 (23000): Duplicate entry '2' for key 'PRIMARY'

UPDATE sample634 SET p=2 WHERE p=3;
ERROR 1062 (23000): Duplicate entry '2' for key 'PRIMARY'

DROP INDEX isample65 ON sample62;

EXPLAIN SELECT * FROM sample62 WHERE a = 'a';

EXPLAIN SELECT * FROM sample62 WHERE no > 10;

CREATE VIEW sample_view_67 AS SELECT * FROM sample54;
SELECT * FROM sample_view_67;

CREATE VIEW sample_view_672(n , v, v2) AS
SELECT no , a, a*2 FROM sample54;
SELECT * FROM sample_view _672 WHERE n = 1;

DROP VIEW sample_view_67;
