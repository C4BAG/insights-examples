# Insights SDK

The Insights page provided by the customer needs to communicate with Contacts by XPhone by passing messages in Javascript. This page describes the list and format of these messages.

## Incoming messages (Tab → Insights)

When the contact selected, the message comes in the following format:

```json
{
    "user": {
        "displayName": "Jane Smith",
        "userPrincipalName": "jane.smith@ventureprise.com"
    },
    "contact": {
        "entryId": "demo-04",
        "entryDn": "CN=Martin Haller,OU=Users,DC=ventureprise,DC=com",
        "dataSource": "Active Directory",
        "personal": {
            "name": {
                "fullName": "Martin Haller",
                "firstName": "Martin",
                "lastName": "Haller",
                "title": "Mr.",
                "displayName": "Martin Haller"
            },
            "birthday": "1985-06-15",
            "address": {
                "street": "123 Main Street",
                "city": "New York",
                "postalCode": "10001",
                "country": "United States"
            }
        },
        "phoneNumbers": {
            "work": [
                "+49899998021",
                "+49899998121"
            ],
            "mobile": "+49123456789",
            "home": "+491713920021",
            "faxNumbers": [
                "+49123456780"
            ]
        },
        "emails": {
            "primary": "Martin.Haller@ventureprise.com",
            "work": [
                "Martin.Haller@ventureprise.com",
                "m.haller@ventureprise.com"
            ]
        },
        "company": {
            "name": "VenturePrise Ltd.",
            "employmentInfo": "Sourcing Manager",
            "department": "Management",
            "website": "https://ventureprise.com",
            "address": {
                "street": "456 Corporate Blvd",
                "city": "San Francisco",
                "postalCode": "94105",
                "country": "United States"
            }
        },
        "customFields": {
            "custom1": "Project Lead",
            "custom2": "Team Alpha",
            "custom3": "Building A",
            "custom4": "Floor 5",
            "custom5": "Desk 42",
            "custom6": "Manager: Jane Smith",
            "custom7": "Start Date: 2020-01-15",
            "custom8": "Security Clearance: Level 2",
            "custom9": "Emergency Contact: Jane Doe",
            "custom10": "Emergency Phone: +1-555-0128",
            "custom11": "Skills: Risk Assessment",
            "custom12": "Certifications: AWS Certified",
            "custom13": "Languages: English, Spanish",
            "custom14": "Time Zone: PST",
            "custom15": "Employee ID: EMP001",
            "custom16": "Cost Center: CC-ENG-001",
            "custom17": "Vacation Days: 15",
            "custom18": "Performance Rating: Excellent",
            "custom19": "Training Completed: Security Awareness",
            "custom20": "Notes: Key team member"
        },
        "dbFields": {
            "dbAppVersion": "2.1.0",
            "dbApplication": "ContactsApp",
            "dbDataBase": "CompanyDB",
            "dbEntityType": "Employee",
            "dbInstance": "PROD-001",
            "dbNativeId": "native-123456",
            "dbParentId": "parent-789",
            "dbServer": "db-server-01.ventureprise.com"
        },
        "thumbnailUrl": "data:image/jpeg;base64,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",
        "contactType": "Default",
        "isObscured": false
    }
}
```

Please keep in mind that most fields are optional, depending on the mapping configured VDir.
The `contract.entryDn` property is always present and guaranteed to be globally unique within this VDir instance.

This message can come multiple times, whenever a new contact is selected.

To subscribe to this message:

```js
window.addEventListener('message', event => {
    // "event.data" contains the message above,
    // e.g. "event.data.contact.entryId" is "demo-04"
});
```

## Outgoing commands (Insights → Tab)

These commands provide a way to interact with the environment which are otherwise restricted by iframe security policy.

To send a message to the Tab, the following code should be used:

```js
const message = { type: "refresh" }; // or any other message described below
window.parent.postMessage(message, "*");
```

### Refresh contact

Makes the Tab resend the contact data to the iframe.
This can be used if the iframe executed a redirect (e.g. a frame was submitted) and needs to get the data once again.

Example:

```json
{ "type": "refresh" }
```

### Send Email

Initiates the process of sending an email to a given address.
If the Tab is working inside Outlook, it will open Outlook’s “New email” editor window.
Otherwise, the system’s default `mailto:` link handler will be used, if any.

Example:

```json
{ "type": "sendEmail", "value": "user@example.com" }
```

### Call Phone Number

Initiates the process of calling a phone number.
If the Tab is configured to use Teams PSTN calls, it will attempt to start the call inside Teams (a confirmation dialog is displayed first).
Otherwise, the system’s default `tel:` link handler will be used, if any.

Example:

```json
{ "type": "callPhoneNumber", "value": "+4917612345678" }
```

### Copy to Clipboard
Copies the given text to clipboard.

Example:

```json
{ "type": "copyText", "value": "hello world" }
```

Note: the regular `navigator.clipboard.writeText` cannot be used inside an iframe because its origin is different from the tab’s origin.