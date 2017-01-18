# uap-redshift
Redshift python library for user agent detection, using uap-python (https://github.com/ua-parser/uap-python).

## Installing
```sql
CREATE OR REPLACE LIBRARY uap_python LANGUAGE plpythonu
  FROM 'https://github.com/ajlai/uap-redshift/releases/download/0.7.2/uap-redshift.zip';
```
See http://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_LIBRARY.html for more documentation on installing custom python modules in redshift.

## Usage
```sql
-- set up a UDF for what you want extracted from the user_agent
CREATE OR REPLACE FUNCTION parse_ua_family (ua VARCHAR)
RETURNS VARCHAR IMMUTABLE AS $$
  from ua_parser import user_agent_parser
  return user_agent_parser.ParseUserAgent(ua)['family']
$$ LANGUAGE plpythonu;

-- Use UDF to start parsing user agents
SELECT parse_ua_family('Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2272.104 Safari/537.36')
--> Chrome
```
