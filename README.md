es-query-export
===========

A CLI Tool for Querying Elasticsearch and Exporting the results in CSV format. Uses the Lucene query syntax that Kibana utilizes.

This Fork bases on [stash-query](https://github.com/robbydyer/stash-query). It provides better way to build query, work with indexes without being bound to time span and ability to query Elasticsearch cluster by URL.

Usage:
-------
```

-u, --url [URL]                  URL to Elasticsearch host to run query on (default: http://localhost:9200)
-i, --index-prefix [PREFIX]      Index name prefix(es). Defaults to 'logstash-*'. Comma delimited
-q, --query [QUERY]              Query string
-t, --tags [TAGS]                Tags to query. Comma delimited
-w, --write [FILE]               Write output file location
-f, --fields [FIELDS]            Comma delimited list of docs fields in output. Defaults to "_all" fields
-l, --delimiter [DELIMITER]      Delimiter to use in output. Defaults to ","
-d, --debug                      Debug mode
-s, --silent                     Run silently
-m, --max [INTEGER]              Maximum number of results to return. Non-integer arguments default to 0.

```

Examples:
-------
```
es-query-export -u http://kibana.com:80/es -i logstash-2015.10.* -q host:localhost and host:127.0.0.1 -f message,date,host -w output.csv -l ';'
es-query-export -u kibana.com:80/es -i logstash-2015.10.11,logstash-2015.10.03,logstash-2015.10.25 -q host:localhost -f _all
es-query-export -u localhost:9200 -i logstash-2011.*,logstash-2012.*,logstash-2015.* -q host:localhost and cluster:c2 -f _all
es-query-export -u localhost:9200 -i logstash-* -q cluster:c5 and cluster:c2 -f host,date
es-query-export -u http://localhost:9200 -i _all -q cluster:c2 -t prod,dev
es-query-export -u localhost:9200 -i _all -q *:* -f _all -w output.csv
es-query-export -i _all -q *:* -f status,host -w output.csv
es-query-export -i _all -q *:* -f _all -w output.csv -s
es-query-export -u http://user:password@kibana.com:80/es -i _all -q *:* -f _all
es-query-export -q *:*
```
