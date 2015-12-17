es-query-export
===========

A CLI Tool for Querying Elasticsearch and Exporting the results in CSV format. Uses the Lucene query syntax that Kibana utilizes. 

Usage:
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
```
es-query-export -u http://kibana.com:80/es -i logstash-2015.10.* -q host:localhost and host:127.0.0.1 -f message,date,host -w output.csv -l ';'
es-query-export -u kibana.com:80/es -i logstash-2015.10.11,logstash-2015.10.03,logstash-2015.10.25 -q host:localhost -f _all
es-query-export -u http://localhost:9200 -i _all -q cluster:c2 -t prod,dev
es-query-export -u localhost:9200 -i _all -q *:* -f _all -w output.csv
es-query-export -q *:*
```
