1-SELECT
  REGEXP_REPLACE(MixedValue, '[^0-9]', '', 'g') AS IntegerPart,
  REGEXP_REPLACE(MixedValue, '[^A-Za-z]', '', 'g') AS CharacterPart
FROM SeperateNumbersAndCharcters;

2-SELECT w1.Id
FROM weather w1
JOIN weather w2 ON w1.RecordDate = w2.RecordDate + INTERVAL '1 day'
WHERE w1.Temperature > w2.Temperature;

3-SELECT PlayerID, Device
FROM (
  SELECT PlayerID, Device,
         ROW_NUMBER() OVER (PARTITION BY PlayerID ORDER BY EventDate) AS rn
  FROM Activity
) sub
WHERE rn = 1;

4-SELECT PlayerID, MIN(EventDate) AS FirstLoginDate
FROM Activity
GROUP BY PlayerID;

5-SELECT SPLIT_PART(FruitList, ',', 3) AS ThirdItem
FROM fruits;

6-WITH chars AS (
  SELECT unnest(string_to_array('sdgfhsdgfhs@121313131', NULL)) AS character
)
SELECT character FROM chars;
