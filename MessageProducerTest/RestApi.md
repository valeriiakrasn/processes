# testMessageName
1. deploy message_test.bpmn
2. note processDefinitionId, messageName
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H "accept: application/json" -H "Content-Type: application/json" -d ""
4. curl -X POST "http://localhost:8080/engine-rest/message" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"messageName\":\"email_message\"}"
5. note processInstance terminated

# testMessageNameCorrelationKey
1. deploy message_test.bpmn
2. note process/General/Id
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"variables\":{\"testVar\":{\"value\":\"stringVal\",\"type\":\"String\"}}}"
4. 

