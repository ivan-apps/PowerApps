# POWER PROJECT
Power Project is a simple project management app built on Dataverse. It can be customized to fit specific needs, and Power Automate flows can be added to customize your notification needs. It accomplishes the following goals:
 - Tracks Project level data, budgeting and POCs
 - Tracks important milestones needed for Senior Leadership briefs w/ visual chart display
 - Tracks project Dependencies and assigned POCs for clearing dependencies
 - Tracks Risks, priority and probability w/ risk factor. Mitigated risk impact, probability + risk factor included.
 - Centralization of project statuses and transparency for on-demand status updates
 - Document repository with SPO native integration
 - Tracks ServiceNow CRQ numbers
 - Task tracking for associated projects, tied to Milestones.
 - Definition of Capability Teams, and associated project resources w/ skills mapping for task assignment.
 - Data is rolled up into a project management dashboard in PBI, Quad Chart for leadership view + gantt chart for progress tracking. Outlines project status for Top 10 priority projects.
 - Senior Leadership briefing and reduction of time spent on preparing brief slides is primary goal. Task tracking is optional as many other tools can accomplish task management.
 - Built for DoD on a DoD tenant, should be compatible with all gov & commercial clouds.   

<br>

# **POWER PROJECT Tech details**
  - Data source is Dataverse with a SharePoint Online connected site for document management
  - Native Dataverse/SPO integration for single source project tracking via Model-Driven app. 
  - Power BI workspace can be configured via environment variable. You can ignore this environment variable during intial install.
  - Ideal for use cases where Dataverse/Power Apps Premium licensing is available and customization is desired
  - Simple install on Power App environments - 2 solution files only.  Can share environment with other apps, isolated environment not necessary (default environment not recommended)


<br>  

# Installation Steps
- Determine Environment to install this app in. You must be at least an System Customizer + Environment Maker & have Dataverse installed.
- Install the AFCommonCore_x_x_x_x_managed.zip solution first.
- Install the PowerProject_x_x_x_x_managed.zip after successful install of Common Core.
- If you have not connected a SPO site to your Dataverse environment already, do so now.
  - Visual guide: https://www.matthewdevaney.com/how-to-setup-sharepoint-integration-model-driven-power-apps/
  - Enable the "Project" entity for document management.
- Power BI Config 
  - Create Power BI Workspace for this application
  - Open and connect the PBIT report to your new data sources (creating a PBIX) and publish it to your workspace. 
  - Go to the "PowerProject/Project Dashboard" environment variable and connect it to the your Workspace and published PBIX report.
  - Configure your refresh as needed.

<br>

# Customizations
The idea behind this app is to set you up with a starting framework for project management using Power Apps when alternatives may not be available. You are fully expected to make customizations and create the necessary flows to polish the app to your needs, just keep in mind a few things:
- This app has an MIT license. It is freely available to all government and commercial entities without cost. Please do not violate this licensing. It is provided as a managed solution to ensure the core functionality can be separated from customizations targetted for your needs.
- Any customizations will be added as an 'unmanaged layer' on top of the 'managed' layer of this app. Read more about managed and unmanaged solution layering on the Microsoft learn site: [LINK](https://learn.microsoft.com/en-us/power-platform/alm/solution-concepts-alm).
  - when updates to the core solution are released you will need to export your unmanaged layer first and re-import when the update is installed. Follow proper ALM practices in regards to your customized layer.
  - You can always revert to the core install by removing the unmanaged layer from the app or uninstalling your managed customizations. 

<br>
