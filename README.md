ServiceNow Incident Management – POC Incident Table
Project Overview
This project contains a ServiceNow proof of concept for an Incident Management table named POC Incident Table (u_poc_incident_table). The table extends the standard ServiceNow Incident table and uses the custom number prefix PINC.
The configuration is captured in the POC_INC_TABLE Update Set exported from a ServiceNow Personal Developer Instance (PDI).
Features Implemented
1. Custom Incident Table
- Created POC Incident Table (u_poc_incident_table) extending the standard Incident table.
- Configured record numbering with the PINC prefix.
- Added custom fields for reassignment tracking and closure information.
- Organized the form into sections such as Incident, Impact, Assignment, Notes, Related Records, Cause, and Resolution, including workspace form layouts.
2. Business Rules
- Reassignment Count (reassignment_count): increments the reassignment count when the assignment group changes from one non-empty group to another. The initial assignment and clearing the assignment group are excluded.
- Choose Current Logged-in User (choose current loggedin user): populates the custom POC Closed By field with the current user when the incident state is Closed, and clears it when the state is not Closed.
3. Client Scripts
- Help Icon: displays help decorations on the Impact and Urgency fields.
- Alert Reassignment Count: displays the current reassignment count in an alert when the form loads.
4. UI Policy
- When state is closed then closed code and closed notes are mandatory: when the state is Closed, makes the custom POC Closed Code and POC Closed Notes fields mandatory.
5. UI Action
- Propose change request record: provides an action that redirects to a new Change Request form.
6. Data Policy
- A Data Policy is configured for the POC Incident Table with the condition that Assignment Group is not empty. Its associated rule makes Work Notes mandatory. The policy is configured to apply to the UI and imports.
7. Import Set / Transform Configuration
The update set also contains an import configuration:
- Data source: u_poc_incident_table.csv (Uploaded)
- Import/staging table: Poc Project 1 (u_poc_project_1)
- Transform Map: POC_Inc_datatransform
- Field maps are included in the update set.
Note: The exported file contains the transform configuration, but its row-transform script is currently a placeholder. Review the field maps and test the import process before using it.

8. Access and Navigation
- Includes an application menu/module for accessing the POC Incident Table.
- Includes a custom role: u_poc_incident_table_user.
- Includes access-control configuration for the custom table.
Custom Fields
The update set includes these custom fields on POC Incident Table:
- Reassignment Count (u_reassignment_count)
- POC Closed By (u_poc_closed_by)
- POC Closed Code (u_poc_closed_code)
- POC Closed Notes (u_closed_notes)
The import/staging table includes fields for values such as category, short description, assigned to, assignment group, number, state, priority, caller, and opened date.
Technologies and ServiceNow Concepts
- ServiceNow Platform / Personal Developer Instance (PDI)
- Incident Management
- Table extension and dictionary configuration
- Business Rules
- Client Scripts
- UI Policies and UI Policy Actions
- UI Actions
- Data Policies
- Import Sets and Transform Maps
- Access Control and Roles
- Update Sets
Deployment Notes
1. Export the Update Set XML from the source ServiceNow instance.
2. In the target instance, retrieve/import the Update Set using the ServiceNow Update Set process.
3. Preview the Update Set and review any collisions or missing dependencies.
4. Commit only after reviewing the preview results.
5. Test the custom table, numbering, Business Rules, Client Scripts, UI Policy, UI Action, Data Policy, access controls, and import configuration in the target instance.
The XML provided is an exported Update Set, not a standalone application installer. Test it in a non-production instance first.
Repository Contents
- README.md – project documentation
- update-set/ – exported ServiceNow Update Set XML (if included in this repository)
- screenshots/ – screenshots of the custom table and configurations (if included)
Project Purpose
This is a hands-on learning project demonstrating ServiceNow administration and platform configuration using Incident Management concepts.
