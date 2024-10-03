
## Table of Contents
- [Power Apps](#power-apps)
- [**DD2875 Approval Routing and Generation App**](#dd2875-approval-routing-and-generation-app)
- [Installation Steps](#installation-steps)
- [Customizations](#customizations)
- [Process Flow](#process-flow)
- [Roadmap](#roadmap)
- [Gallery](#gallery)
  - [App](#app)
  - [Power BI Reports](#power-bi-reports)

# Power Apps
This repo is home to sample apps built for GCC, GCC High & DoD clouds. It is provided as-is without explicit or implicit support. Issues may be posted to Github issues list and may contribute to the overall project. You are encouraged to modify and configure the app to suit your needs but keep in mind the MIT licensing guidelines.

<br>

# **DD2875 Approval Routing and Generation App**
  - Data source is SPO lists & Document library templates
  - Word Document replica for DD2875 and DD2842
  - No premium connectors/licensing needed
  - Environment Variables allow for easy configuration to different environments
  - 1 Canvas app for both admins and end-users
  - E-signature capable (not digitial)
  - Implementation includes several safeguards for SSNs required to look up clearance info in DISS
  - Configurable approver roster via SPO lists
  - Sample Power Automate flow for periodic reminders
  - Power BI Process Overview report template (obtain appropriate license or E5)
  - Responsive app design (target is still desktop for best experience)
  - Document preview screen for submission attachments
  - Security Managers have unique app dashboard that bypasses delegation issues and prefilters requests relevant to themselves.
  - Search capabilities is delegable


<br>  

# Installation Steps
- Determine Environment to install this app in. You must be at least an Environment Maker.
- Determine SPO Site to install this app in. You should be an SCA in order to create and configure the permissions.
- Install all list & document templates on the [SPO List Templates](/PowerApps/DD2875%20Routing/SPO%20List%20Templates/) folder
- *NEW* List templates are now provided in CSV schema files for easier creation. Unfortunately DocLibs do not have a similar .CSV export so those are still .STP files.
- Add the Word document template for the DD2875 on the appropriate document library. [LINK](/PowerApps/DD2875%20Routing/Word%20Templates/Template-DD-2875%20SAAR%20for%20SharePoint.docx)
- Secured SSN List
  - break inheritance on this list and remove inherited permissions. Ensure this list has item-level permissions so that users can only see what they created. 
  - Create a group for Security Managers in SharePoint and give that group either full control or the ability to see all items in the list. 
  - Sync this group to the SPO list for security managers via Flow (not included in solution).
- Populate the supporting configuration lists (ex: Countries, Orgs, Directorates, Divisions, etc.). The app has dependent choice fields that respond to this configuration.
- Populate Admin lists & Approver lists
- Power BI Config 
  - Create Power BI Workspace for this application, 
  - Open and connect the PBIT report to your new data sources (creating a PBIX) and publish it to your workspace. 
  - Get the embedded Power BI Report link (for Website or Portal) and save the link for the Environment Variable config.
- In your desired environment, go to the maker portal and click on 'Solutions'
- Import the DoD_ASD_App_1_0_0_35_managed.zip solution file.
- Proceed with the prompts. It will ask you to enter several environment variable URLs for the imported lists as well as the Power BI report link. Continue until it begins the import.
- Once the import is completed, publish all customizations and verify that the solution exists with all the necessary flows activated.
- Test the app in the app editor to fix any outstanding issues.
  - KNOWN ISSUE: Refreshing data seems to attempt to reconnect to the my dev tenant SPO location. While you don't manually refresh the data source, it should read the environment variable and play the app just fine. If you encounter a need to manually refresh, simply remove the existing connection and re-add without the environment variable and it should refresh just fine. 

<br>

# Customizations
The idea behind this app is to set you up with a starting framework for processing DD2875's digitally with as little overhead as possible. You may remove screens and configure the app to fit your specific needs, just keep in mind a few things:
- This app has an MIT license. It is freely available to all government and commercial personnel without cost. Please do not violate this licensing. It is provided as a managed solution to ensure the core functionality can be separated from customizations targetted for your needs.
- Any customizations will be added as an 'unmanaged layer' on top of the 'managed' layer of this app. Read more about managed and unmanaged solution layering on the Microsoft learn site: [LINK](https://learn.microsoft.com/en-us/power-platform/alm/solution-concepts-alm).
  - when updates to the core solution are released you will need to export your unmanaged layer first and re-import when the update is installed.
  - You can always revert to the core install by removing the unmanaged layer from the app.

<br>

# Process Flow
The app flows in the following manner:
![image](/images/ASD_Flow.png)
- Only ASD Initial or ASD Final can kick back a request. Everyone else only provides recommendations or info for the request.
- Documents are generated by button click at the ASD Final stage
- Emails are sent out at every stage entry. Timestamps are recorded at each transition for Power BI Process Insights reporting
- A reminder email scheduled flow is provided, it can be replicated to apply to any stage you want.
- SSNs are deleted after the security manager is done with clearance verification


# Roadmap
- Utilization of Creator Kit FluentUI details list for a more compact view of requests.
- Utilization of Canvas components for the Process Flow on the request screens (to tell you which step you're on)
- Documentation generation via PowerDocu
- More admin tools, searching, sorting, etc.

# Gallery
## App
![image](/images/Homescreen.png)
![image](/images/ListView.png)
![image](/images/SMScreen.png)
![image](/images/ASDFinal_DocGenerated.png)
## Power BI Reports
![image](/images/ASD_PowerBI_Overview.png)
![image](/images/ASD_ProcessInsights.png)
![image](/images/ASD_ProcessInsights-Trends.png)
