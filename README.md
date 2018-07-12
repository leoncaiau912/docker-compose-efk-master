Docker compose file for setting up a EFK service
================================================

A basic docker compose file that will set up Elasticsearch, Fluentd, and Kibana.

Example
-------

The file `example/httpd.yml` shows how to configure a service to use EFK as its logging facility. To test using this file, just run:

    docker-compose -f docker-compose.yml -f example/httpd.yml up

Then, go to your browser and access `http://localhost:8088` (httpd) and `http://localhost:5601` (kibana). You should be able to see the httpd's logs in kibana's discovery tab. By the way, if you are wondering what is this index kibana asks the fist time you access it, it is `fluentd-*`.

After you are done, just run:

    docker-compose -f docker-compose.yml -f example/httpd.yml rm -f

And all services will be reclaimed.

# docker-compose-efk-master

username: elastic
password: changeme


#another example to run nginx
docker run -d --log-driver fluentd --log-opt fluentd-address=localhost:24224 --log-opt tag="nginx-test" --log-opt fluentd-async-connect  --name nginx-test -p 8888:80 nginx

#note
restart fluentd if see the error logs like "ConnectionFailure error="Can not reach Elasticsearch cluster ({:host=>\"elasticsearch\", :port=>9200, :scheme=>\"http\", :user=>\"elastic\", :password=>\"obfuscated\"})!""
