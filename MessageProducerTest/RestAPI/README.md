# testMessageName
1. deploy message_test.bpmn
2. note processDefinitionId, messageName
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H "accept: application/json" -H "Content-Type: application/json" -d ""
4. curl -X POST "http://localhost:8080/engine-rest/message" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"messageName\":\"email_message\"}"
5. note processInstance terminated

# testMessageNameCorrelationKey
1. deploy message_test.bpmn
2. note process/General/Id, receive task/Message/Name
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"variables\":{\"testVar\":{\"value\":\"stringVal\",\"type\":\"String\"}}}"
4. curl -X POST "http://localhost:8080/engine-rest/message" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"messageName\":\"email_message\",\"correlationKeys\":{\"testVar\":{\"value\":\"stringVal\",\"type\":\"String\"}}}"
5. note processInstance terminated

# testMessageNameProcessInstanceId
1. deploy message_test.bpmn
2. note receive task/Message/Name, process/General/Id
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H "accept: application/json" -H "Content-Type: application/json" -d ""
4. copy Id of the process instance
5. curl -X POST "http://localhost:8080/engine-rest/message" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"messageName\":\"email_message\",\"processInstanceId\":\"db24f931-8daf-11ed-a271-00ff09576864\"}"
6. note processInstance terminated

# testMessageNameBusinessKey
1. deploy message_test.bpmn
2. note process/General/Id, receive task/Message/Name
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"businessKey\":\"BusinessKey12345\"}"
4. curl -X POST "http://localhost:8080/engine-rest/message" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"messageName\":\"email_message\",\"businessKey\":\"BusinessKey12345\"}"
5. note processInstance terminated

# testBusinessKey
1. deploy message_test.bpmn
2. note process/General/Id
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"businessKey\":\"businesskey_messagetest\"}"
4. curl -X GET "http://localhost:8080/engine-rest/execution?businessKey=businesskey_messagetest&processInstanceId=627103d5-8dc9-11ed-a271-00ff09576864&activityId=email_activityId" -H  "accept: application/json"
5. curl -X POST "http://localhost:8080/engine-rest/execution/6278cc07-8dc9-11ed-a271-00ff09576864/signal" -H  "accept: */*" -H  "Content-Type: application/json" -d ""
6. note processInstance terminated

# testInstanceId tbd
