# Real World Application

- Consider an application with different message services like MessageService, ErrorMessageService and DirectMessageService.
- A single dependency can not be provided in all cases.
- Normally MessageService is the default option but if an error message is to be sent, the dependency should be changed to ErrorMessageService.
- If the user sets DirectMessage as default the condition should be checked and DirectMessage dependency should be provided.
- All the above requirements can be achieved using Dependency Providers.
