# Important points
Dependency -- Add dependency spring for kafka  
Properties -- add kafka related properties in application.properties/yml file  
Producer -- use KafkaTemplate<String, String> to send message  
Consumer -- use @KafkaListener(topics = "", groupId = "") to subscribe to topic and get message  

# download kafka and install
# run below commands to bring up the kafka server, broker, topic, producer and consumer.
# these commands are for windows machine. change accordingly for mac/linux
cd to Download\kafka  
# Start the ZooKeeper service
$ bin\windows\zookeeper-server-start.bat config\zookeeper.properties  

# Start the Kafka broker service
$ bin\windows\kafka-server-start.bat config\server.properties  
if failes because of log related issue then stop zookeeper and delete log dir and try (check server.properties file for log directory usually C:\tmp\kafka-logs you can also try deleting zookeeper dir under tmp location)  

# topic
$ bin\windows\kafka-topics.bat --create --topic learnwithankit --bootstrap-server localhost:9092  

# producer
bin\windows\kafka-console-producer.bat --topic learnwithankit --bootstrap-server localhost:9092  

# consumer
.\bin\windows\kafka-console-consumer.bat --topic learnwithankit --from-beginning --bootstrap-server localhost:9092  

# READ THE EVENTS (to see the meesage sent by producer to the topic)
bin\windows\kafka-console-consumer.bat --topic learnwithankit --from-beginning --bootstrap-server localhost:9092  

# test the service
GET:  http://localhost:8080/api/v1/kafka/publish?message=hello  

# test with json body
POST: http://localhost:8080/api/v1/kafka/publish  
Body:  
 {  
 "id":2,  
 "firstName":"ankit1",  
 "lastName" :"raj1"  
 }  
