# RPA
### Project structure
##### Requests
Accomodates spreadsheet containing the data to process is stored in a file named `Requests.xlsx` is stored. 
##### Processed 
Accommodate the processed spreadsheets in the name formart `Request_Date_Timestamp.xlsx`

The project is implemented in three workflows.

### Main Workflow

- It initiates the automation process. It is also used to invoke the other two workflows.
- Declares New variables that are used to store the data that from the `ReadRequests` workflow. They are then passed to the `SaaSAutomation` workflow, where they are used to populate the ticktet fields on Zoho Desk.
- It is also used to move the processed request to the processed folder and rename the files while caputing the timestamp using `Now.ToString("MM-dd-yyyy_hh_mm_ss")`.
- It also defines a parallel controll activity to accomodate a trigger scope that defines a hotkey to trigger the termination of a workflow using the hotkey `ctrl + t` sto stop automation.

### ReadRequests Workflow

It picks up the Request Excel file from the Requests folder, reads the ticket data, and processes them and maps them to it into variables for the next workflow to process.

### SaaSAutomation Workflow

It uses the data obtained from the Requests file to create the support ticket within Zoho Desk.
