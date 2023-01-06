# testMessageName
    sendTestPayload("camunda-rest:start?processDefinitionKey=message_testxt", headers, body);
    sendTestPayload("camunda-rest:message?messageName=email_message", headers, body);
    // assert external task received
