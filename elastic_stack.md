# Elastic Stack

The Elastic stack is a set of technologies that when combined, enable you to store log data and index it for rapid retrieval.  Elastic stack is currently made up of Elastic Search, Logstash, Beats, and Kibana.

A fast way to get a development stack up and running on your local machine, use https://github.com/elastic/stack-docker which uses `docker-compose` to make the install process a breeze.


## Helpful Snippets

refs:
- (Getting Started Tutorial)[https://logz.io/blog/elasticsearch-tutorial/}
- (ES Tutorial)[https://stackify.com/elasticsearch-tutorial/]


###### Create an oAuth token via your password

```
curl -u "elastic:${ELASTIC_PASS}" \
  -k -XPOST \
  -H 'Content-Type: application/json' \
  https://localhost:9200/_security/oauth2/token \
  -d '{ "grant_type" : "client_credentials" }'
```


###### Load data into Elastic

```
curl -u "elastic:${ELASTIC_PASS}" \
  -k -XPOST \
  -H 'Content-Type: application/json' \
  https://localhost:9200/my_index/_doc/ \
  -d '{ "im_a_document" : "i will live in elastic search" }'
```


###### List indecies

```
curl -u "elastic:${ELASTIC_PASS}" \
  -k -XGET \
  'https://localhost:9200/_cat/indices?v&pretty'
```

###### Read a Document from Elastic

```
curl -u "elastic:${ELASTIC_PASS}" \
  -k -XGET \
  -H 'Content-Type: application/json' \
  https://localhost:9200/my_index/
```

###### Search Elastic for Data

Search within any values within an index:
```
curl -u "elastic:${ELASTIC_PASS}" \
  -k -XGET \
  -H 'Content-Type: application/json' \
  https://localhost:9200/my_index/_search?q=search
```

Search for a specific key to have a specific value:
```
curl -u "elastic:${ELASTIC_PASS}" \
  -k -XGET \
  -H 'Content-Type: application/json' \
  https://localhost:9200/my_index/_search?q=im_a_document:i
```


