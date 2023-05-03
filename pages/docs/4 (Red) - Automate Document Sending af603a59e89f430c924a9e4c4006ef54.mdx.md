# 4 (Red) - Automate Document Sending

- Create a Power Automate Flow triggered by a specific event in Power Apps (e.g., a button click).
i. Integrate askARSAN with Outlook using the Outlook connector in Power Automate. Follow this guide for detailed steps: [https://docs.microsoft.com/en-us/connectors/office365/](https://docs.microsoft.com/en-us/connectors/office365/)
ii. Set up the flow to send an email containing the required documentation to the candidate automatically when they reach the relevant recruitment stage.

Breaking down into more detailed actions that a technician would need to take using Power Automate to automate document sending.

4 (Red) - Automate Document Sending

- Open Power Automate ([https://flow.microsoft.com/](https://flow.microsoft.com/)) using your Office 365 credentials and create a new flow by selecting "Create > Automated flow" or “Create > Instant flow” with Power Apps as the trigger (depending on if you want the flow to start automatically upon a specific event or manually by a button in the Power App).

```
└─[Create New Power Automate Flow]
    ├─[Choose a Trigger]
    │   └─[Select Power Apps Trigger]
    ├─[Set up the Flow]
    │   ├─[Add 'Get File Content' action (SharePoint connector)]
    │   │   └─[Specify SharePoint document library & provide dynamic identifiers for files]
    │   ├─[Combine Documents (optional)]
    │   │   └─[Use a connector like 'Plumsail Documents' or 'Encodian' to merge the documents into a single file]
    │   ├─[Add 'Send an Email' action (Outlook connector)]
    │   │   ├─[Specify recipient (from Power Apps)]
    │   │   ├─[Set subject and body for the email]
    │   │   └─[Attach the document(s) to the email]
    ├─[Save and Test the Flow]
        └─[Confirm successful document sending]

```

- Get File Content - helps you pinpoint a specific file in a SharePoint document library.
1. First, you need to add an action in Power Automate to get the required file from the SharePoint document library. Add the "Get files (properties only)" or the "Get file properties" action from the SharePoint connector.
    
    a. For "Get files (properties only)": configure the action by selecting the SharePoint site address and the desired document library in the 'Library Name' field. You can also add a filter query if needed to narrow down the files (e.g., filtering by file name, file type, or modified date).
    
    b. For "Get file properties": configure the action by selecting the SharePoint site address, the desired document library in the 'Library Name' field, and the specific file id or path.
    
2. Next, add the "Get File Content" action from the SharePoint connector in Power Automate. In the 'Site Address' field, select the SharePoint site address that contains the document library to fetch the file from.
3. In the 'File Identifier' field, provide the identifier for the desired file found in step 1:
    
    a. If you used the "Get files (properties only)" action, select the 'Id' property from the dynamic content of this action (usually displayed as "Id" or "Identifier" in the dynamic content). You can also use "First()" or "Last()" functions to pick the first or last item from the list if you have multiple files returned.
    
    b. If you used the "Get file properties" action, select the 'ItemId' or 'Id' property from the dynamic content of this action.
    
4. Save your flow and test it to ensure the "Get File Content" action retrieves the expected file using the provided file identifier.

By following these steps, you can effectively use the file identifier in the "Get File Content" action for SharePoint to fetch the desired file content for further use in your flow