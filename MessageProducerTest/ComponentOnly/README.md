# testMessageName
    sendTestPayload("camunda-rest:start?processDefinitionKey=message_test_xt", headers, body);
    sendTestPayload("camunda-rest:message?messageName=email_message", headers, body);
    // assert external task received
    
# testMessageNameCorrelationKey
     final Map<String, Object> headers = mapOf("testVar", "stringVal");
     sendTestPayload("camunda-rest:start?processDefinitionKey=message_test_xt&amp;copyHeaders=true", headers, body);
     sendTestPayload("camunda-rest:message?messageName=email_message&amp;correlationKeyName=testVar", headers, body);
     send "CamundaBpmCorrelationKey" to "stringVal";
