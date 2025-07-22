# MdeAvHealthDashboard
MDE and AV health status pulled from API's for Power bi dashboard.

<b>Summary</b><br>
This Power Bi Dashboard displays health data that is pulled via API directly from an Azure Application Registration.
<br><br><br>
<b>About</b><br>
This Dashboard is using the Application Context to connect to a Defender API and pull data directly into a PowerBi report. This means that you do not need a user's permissions to be set to retrieve the data. The user is considered anonymous because the connection credentials are stored as parameters in the report. Where advanced hunting is used as the API endpoint the dashboard gathers the number of records in a query then uses that number to break the data into chunks to accomodate the limits on a single Advanced Hunting Query data return and then concatenates the data before populating the table with that information. 
<br><br><br>
<b>How to Use</b><br>
As long as the current tenant is up you will see the data from a test tenant without any modification of the downloaded file. To see your own data you will need to<br> 
<br>1. Open the file, 
<br>2. On the buttons along the top of the screen find the "Transform Data" button and click on it 
<br>3. Click the "Transform Data" button, then navigate to the "Edit Parameters" and click on it
<br>4. Fill in the parameters with the information from your Application Registration in Azure
<br>5. Go back to the "Transform Data" button click on the drop down and then select "Data Source Settings"
<br>6. Select the drop down next to the "Clear Permissions" and then select "Clear All Permissions"
<br>7. Confirm the selection
<br>8. Next to the "Transform Data" button on the top of the screen is a "Refresh" button. Click on it.
<br>9. There will be a prompt to edit credentials. When asked select "Anonymous" Authentication. This is done because the credentials are supplied in the queries not by the user context.  
<br><br><br>
Depending on the amount of data being pulled the queries may take some time to complete. Testing has been done with environments containing around 100k endpoints and queries can take up to ~5 minutes to complete in that scenario. 
<br><br><br>
<b>Reference Material</b><br>
This link has a walk through on how to create an App Registration in Azure. The App Registration is where the permissions are allocated for an application. That application is what is used to gather the information from Microsoft Defender for Endpoint API's to populate the data.<br> 
https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro<br><br>
The Application permissions needed: <br>
<br>1. Permissions are set under the "WindowsDefenderATP" section in the API permissions
<br>2. Once that API endpoint is selected "Application Permissions" is the next selection
<br>3. Permissions needed will be under Machine-> Machine.Read.All and then Advanced Query->AdvancedQuery.Read.All
<br><br><br>
<b>Security Considerations</b><br>
This Dashboard is using the Application Context to connect to a Defender API and pull data directly into a PowerBi report. As of July 2025, Power Bi does not directly support the use of certificates for this connection type so using a secret is the only way to pull this information. It is worth considering the use of conditional access to control networks and Service Principal risk as mitigating factors.  
<br>
https://learn.microsoft.com/en-us/entra/workload-id/workload-identities-overview
<br><br><br>

