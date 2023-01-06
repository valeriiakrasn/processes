# testMessageName
1. deploy message_test.bpmn
2. note activityId and processDefinitionId
3. curl -X POST "http://localhost:8080/engine-rest/process-definition/key/message_test/start" -H "accept: application/json" -H "Content-Type: application/json" -d ""
4. 
