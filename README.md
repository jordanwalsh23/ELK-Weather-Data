# ELK-Weather-Data
ElasticSearch/Logstash/Kibana Ready Repo for Australian Bom Data

Data is available in the 'Downloads' directory.  This has been pulled from the public BoM service here: ftp://ftp.bom.gov.au/anon/gen/fwo/

This has been built with the following versions:
* elasticsearch-2.2.0
* logstash-2.2.2
* kibana-4.4.1

# Getting started

1. Start elasticsearch by browsing to the elasticsearch home directory and running

  `bin/elasticsearch`

2. Start kibana by browsing to the kibana home directory and running 

  `bin/kibana`

*Note:* I had issues running in chrome, but none in safari

3. Update the Logstash config to point to your local `downloads` directory.  

```
input {
    file {
        path => "<PATH TO YOUR DOWNLOADS FOLDER>/*.xml"
        start_position => beginning
        sincedb_path => "/dev/null"
    }
}
```

You can also comment out the `sincedb_path` line to use a proper one. I've used this for debugging purposes.

4. Run logstash

  `bin/logstash -f <path to config> --debug`

You should see logstash start and immediately a new index is created and populated.

You should also now be able to use Kibana to view the information.

Enjoy

