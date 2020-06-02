# Description
A helper class for sending messages to Microsoft Teams via webhook.



# How to Use
1. Generate a Teams Webhook URL for the channel you would like to message. From the Teams page, click the vertical ellipsis (three dots) icon next to the channel and select _Connectors_. Then click _Configure_ next to **Incoming Webhook**. Follow the prompts and complete the information, making sure to copy the URL once it is generated.


2. Add the TeamsHelper nuget package from the SUPPLY.com nuget feed. _Note: the target framework is .NET Core_


3. Add a `using` statement for `TeamsHelper`


4. Create a new `TeamsMessage` object and pass a message **title**, **text** _(ie, content of the message)_, **color**, and **webhook URL** in the constructor:
		_Note: currently available colors are red, yellow, green and purple_

```
	TeamsMessage teamsMessage = new TeamsMessage(title, text, color, teamsUrl);
```


5. Call the `LogToMicrosoftTeams` method and pass the `TeamsMessage` object as the parameter:
```
	teamsMessage.LogToMicrosoftTeams(teamsMessage);
```



## Example
```
	try
	{
		DoSomething();
	}
	catch (Exception ex)
	{
		string title = "Error in DoSomething method";
		string text = $"Error message: {ex.Message}";
		string color = "red";
		string teamsUrl = "{yourWebhookUrl}";
		TeamsMessage teamsMessage = new TeamsMessage(title, text, color, teamsUrl);
		teamsMessage.LogToMicrosoftTeams(teamsMessage);
	}
```