## func string_agg()

    SELECT STRING_AGG(T2.name,', ') AS names,
        T2.country
    FROM (SELECT * FROM (VALUES ('Allie',15,'USA'),('Amanda',14,'USA'),('Alana',20,'China')) 
    AS t (Name,AGE,Country)) AS T2
    GROUP BY T2.country