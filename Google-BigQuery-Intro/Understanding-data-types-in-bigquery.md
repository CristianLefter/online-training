# Understanding data types in BigQuery (e.g., INTEGER, FLOAT, STRING, TIMESTAMP)

It is essential to have a thorough understanding of Google BigQuery data types in order to fully utilize the tool's on-demand capabilities and features.

BigQuery supports the following key data types:
- **INTEGER**: This is a signed 64-bit integer type. Examples of values: 1, -5, 0.
- **FLOAT**: This is a double-precision floating-point number. Examples of values: 3.14, -0.01, 0.0.
- **BOOLEAN**: This is a type with two possible values: TRUE or FALSE.
- **STRING**: This is a sequence of characters, such as "hello", "world", or "foo".
- **BYTES**: This is a sequence of bytes, represented as a base-64 string.
- **TIMESTAMP**: This is a type for storing a single point in time, with up to nanosecond precision. Examples of values: "2022-01-01 00:00:00", "2022-12-31 23:59:59.999999999".
- **DATE**: This is a type for storing a calendar date (year, month, and day) without a time. Examples of values: "2022-01-01", "1900-01-01".
- **TIME**: This is a type for storing a time of day (hour, minute, second, and subsecond). Examples of values: "12:34:01", "00:00:00.123456".
- **DATETIME**: This is a type for storing a date and time value. It is a combination of the DATE and TIME types. Examples of values: "2022-01-01 12:34:01", "1900-01-01 00:00:00".
- **ARRAY**: This is a type for storing an ordered list of values. Example of value: [1, 2, 3]
- **STRUCT**: This is a type for storing a nested record with a set of named fields. Example of value: {"x": 1, "y": 2}

The following example is using the declaration of several variables to ilustrate the use of data types:
```sql
-- Declare a STRING variable
DECLARE x STRING(6);
-- A valid assignment to x.
SET x = "hello";
-- OUT_OF_RANGE error.
SET x = "hello world";

-- Declare a NUMERIC variable
DECLARE y NUMERIC(5, 2) DEFAULT 123.45;
```
