


# Setup Elasticsearch Logstash Kibana in Docker

Setting up a Docker container environment for Elasticsearch, Logstash, and Kibana involves several steps. These tools are often referred to as the "ELK stack" and are commonly used for log aggregation, analysis, and visualization. Here's a step-by-step guide to help you set up the ELK stack using Docker containers:

Create directory ELK and go into

    mkdir ELK
    cd ELK

create new directory with name logstash then create a file logstash.conf and paste the below contents

         

    input{
    file{
         path=> "/root/docker-day-1/temp/inlog.log"
        }
    }
    output {
        elasticsearch {
             hosts => ["http://elasticsearch:9200"]
            }
     }
    
Open  port in firewall

    sudo firewall-cmd --add-port=9200/tcp --permanent
    sudo firewall-cmd --add-port=5601/tcp --permanent
    sudo firewall-cmd --add-port=9600/tcp --permanent
    sudo firewall-cmd --add-port=9300/tcp --permanent
    sudo firewall-cmd --reload


Create ELK stack using  Docker Compose

    Docker-compose -d 

Access ELK stack

    http://your-ip:5601

