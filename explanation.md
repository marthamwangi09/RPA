# RPA
### Project folders
##### Requests
Where the spreadsheet containing the data to process is stored in a file named `Requests.xlsx` is stored. 
##### Processed 
Accommodate the processed spreadsheets in the name formart `Request_Date_Timestamp.xlsx`

The project is implemented in three workflows.

### Main

- It initiates the automation process. It is also used to invoke the other workflows.
- New variables are created here to store the data that we would get from the `ReadRequests` workflow. These variables are passed to the `SaaSAutomatio`n workflow, where they are used to populate the ticktet fields on Zoho Desk.
- It is also used to move the processed request to the processed folder and rename the files accordingly by using the variable `Now.ToString("MM-dd-yyyy_hh_mm_ss")`.
- It used a parallel process to run a trigger scope that defines a hotkey to trigger the termination of a workflow using the hotkey `esc`.

### ReadRequests

This workflow picks up the Request Excel file from the folder we created, reads the ticket data, and incorporates it into variables for the next workflow to process.

### SaaSAutomation

It uses the data obtained from the Requests file to create the support ticket within Zoho Desk.
