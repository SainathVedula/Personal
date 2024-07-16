# Code Examples in Multiple Languages

<!-- Tab buttons -->
<div class="tab-buttons">
    <button class="tab-button" onclick="showTab('java')">Java</button>
    <button class="tab-button" onclick="showTab('csharp')">C#</button>
    <button class="tab-button" onclick="showTab('python')">Python</button>
</div>

<!-- Java code example -->
<div id="java" class="tab-content">
```java
public SkillAdapterWithErrorHandler(
    Configuration configuration,
    AuthenticationConfiguration authenticationConfiguration
) {
    super(configuration, authenticationConfiguration);
    setOnTurnError(new SkillAdapterErrorHandler());
}

private class SkillAdapterErrorHandler implements OnTurnErrorHandler {

    @Override
    public CompletableFuture<Void> invoke(TurnContext turnContext, Exception exception) {
        return sendErrorMessage(turnContext, exception).thenAccept(result -> {
            logger.severe(String.format("Exception caught : %s", exception));
        });
    }
}
