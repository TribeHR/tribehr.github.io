---
category: General
title: 'Roles and Permissions'
layout: default
---

The Roles and Permissions feature allows you to customize what your users can see and do in TribeHR. 
You create roles that have permissions to view, create, and change a subset of information as well as use selected features in your TribeHR account. 

You can tailor those roles further by setting limits on the permissions based upon location, department, reporting structure, and other aspects of your organization. 

Historically in TribeHR, users were assigned just one of three roles: employee, manager, or administrator.
Generally, an employee was allowed to see and do things only having to do with themselves and public information.
Managers had more visibility and permissions having to do with their reports.
Administrators could do literally anything in TribeHR.
 
With our new Roles and Permissions architecture, users can have more than one role depending upon their responsibilities within your organization, and these roles are “additive”, meaning that a person has the sum of all permissions given to them by the roles you assign to them. 

Because you can limit permissions, you can create different types of administrators with permissions to use different parts of TribeHR, and even limit them by where they work or which part of your organization they report to. 

For example, you have an administrator who handles most routine support issues for your employees, but should not be able to view sensitive information such as salary. You can customize a role for that person that they can only see information and perform actions necessary for their job. 

Or perhaps you want the recruiting coordinator for your San Francisco office to not be able to work with job postings in Paris or New York. In this case, you can create a San Francisco recruiting role that gives someone the ability to create, edit, and delete job postings, but only for San Francisco. 

With Roles and Permissions enabled, we provide four default roles for all accounts, but you can change the permissions for these default roles, as well as create as many new roles as you need. 
Here are the four default roles: 

 - **Employee** will largely be the same as the current employee role, giving those users the ability to see detailed information about themselves but more basic information about the company and their coworkers.
   By default, this role is assigned to all users, but you can take that role away from users as needed. 

 - **Manager** will add several additional permissions appropriate for that role, such as approving time-off and performing evaluations.
   These settings can also control whether the manager could view or act on information throughout their whole hierarchy or only for direct reports.

 - **System Administrator** will oversee management of users, system access, TribeHR features and integrations, and management of roles themselves (creating, editing, deleting).
   This role will not have permission to see or change some personally identifiable information about employees.
   Users who currently have the administrator role in your TribeHR account will be given this role when Roles and Permissions is enabled.
   Because this role can create, edit, and delete role definitions themselves, we strongly recommend that very few people in your organization have this role. 

 - **HR Administrator** will oversee areas having to do with employees: jobs, departments, recruiting, and assigning roles to users. 

The Roles and Permissions feature will replace some existing TribeHR functionality, in addition to adding new functionality.
Here are some changes: 

  - Unfortunately, the TribeHR mobile application will not function properly with our new Roles and Permissions architecture, so it will be discontinued. 
  
  - Privacy settings will no longer be available under Company > General Info.  
  
  - Privacy settings for documents, notes, custom fields, goals, and feedback will be separated from roles, meaning that users can decide who can see the items that belong to them regardless of roles and permissions. 
  
  - The current manager actions, such as approving time-off requests or updating employee skills, will now, by default, apply to all reports, not just direct reports. 
    You can configure this to match your organization’s structure when creating or changing a role.
    
  - Any integrations that you have developed to work with the TribeHR API may no longer work as intended.
    Integrations use an API key that is mapped to a particular TribeHR user, so if that user’s permissions change with our new roles and permissions architecture, the integration may not work.
    Make sure that the user whose API key you are using has the appropriate roles and permissions. 

Here are some features that will function as they do now: 

  - Timeoff requests and approvals

  - Performance reviews

