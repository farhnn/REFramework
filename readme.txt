Below custom changes made on REFramework :

- For new transactions, start time is added (variable scope is in the state machine)
- LogTable is built with required columns in init (to push transactional log data)
- in SetTransactionStatus, log table rows are added and pushed to DB in all 3 cases
- New log field added to include 'UniqueID' for each transaction while logging.
- UIPATH_DBSTRING asset will be used to push the log data to 'UiPath_CustomLogs' table.
- In the first run, save the project name in 'ProjectDetails.txt'. Will be used for identifying the project for other steps.
- Read Config file based on Asset 'Shared Project Path'
 	- If 'Data', consider it Non prod env and read from Project folder
	- If not, read from common shared folder with specific subfolder name (project name)

Log table columns :

- Process_code - Project Folder name is taken by default. Has to be changed based on the approach
- Reference - Transaction Item reference is taken by default. 
- StartTime - transaction Start time
- EndTime - transaction End time
- ElapsedTime - difference of above, as timespan
- Status - Success, System Exception or Business Exception
- Item - defaulted to 1 for queue based process. OR use this value as number of transactions per execution.

Added Email Notifications in case of BE and SE
- System Exception - Sends email with screenshot, with full error details (source, stacktrace and error message)
