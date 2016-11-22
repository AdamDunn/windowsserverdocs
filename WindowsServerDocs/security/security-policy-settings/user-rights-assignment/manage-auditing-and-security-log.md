---
title: Manage auditing and security log
description: "Windows Server Security"
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-policy-settings
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2238b05b-e89d-4b53-b8f3-90e46eb7fbce
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
---
# Manage auditing and security log

>Applies To: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

This security policy reference topic for the IT professional describes the best practices, location, values, policy management, and security considerations for this policy setting.  
  
## Reference  
This policy setting determines which users can specify object access audit options for individual resources such as files, Active Directory objects, and registry keys. These objects specify their system access control lists (SACL). A user who is assigned this user right can also view and clear the Security log in Event Viewer.  
  
This policy setting is supported on versions of Windows that are designated in the **Applies To** list at the beginning of this topic.  
  
Constant: SeSecurityPrivilege  
  
### Possible values  
  
-   User-defined list of accounts  
  
-   Administrators  
  
-   Not Defined  
  
### Best practices  
  
1.  Before removing this right from a group, investigate whether applications are dependent on this right.  
  
2.  Generally, assigning this user right to groups other than Administrators is not necessary.  
  
### Location  
*GPO_name*\Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment  
  
### Default values  
By default this setting is Administrators on domain controllers and on stand-alone servers.  
  
The following table lists the actual and effective default policy values for the most recent supported versions of Windows. Default values are also listed on the policy's property page.  
  
|Server type or GPO|Default value|  
|-----------|---------|  
|Default Domain Policy|Not defined|  
|Default Domain Controller Policy|Administrators|  
|Stand-Alone Server Default Settings|Administrators|  
|Domain Controller Effective Default Settings|Administrators|  
|Member Server Effective Default Settings|Administrators|  
|Client Computer Effective Default Settings|Administrators|  
  
### Operating system version differences  
There are no differences in the way this policy setting works between the supported versions of Windows that are designated in the **Applies To** list at the beginning of this topic.  
  
This policy setting is supported on versions of Windows that are designated in the **Applies To** list at the beginning of this topic.  
  
## Policy management  
This section describes features, tools, and guidance to help you manage this policy.  
  
A restart of the computer is not required for this policy setting to be effective.  
  
Any change to the user rights assignment for an account becomes effective the next time the owner of the account logs on.  
  
Audits for object access are not performed unless you enable them by using the Local Group Policy Editor, the Group Policy Management Console (GPMC), or the Auditpol command-line tool.  

  
### Group Policy  
Settings are applied in the following order through a Group Policy Object (GPO), which will overwrite settings on the local computer at the next Group Policy update:  
  
1.  Local policy settings  
  
2.  Site policy settings  
  
3.  Domain policy settings  
  
4.  OU policy settings  
  
When a local setting is greyed out, it indicates that a GPO currently controls that setting.  
  
## Security considerations  
This section describes how an attacker might exploit a feature or its configuration, how to implement the countermeasure, and the possible negative consequences of countermeasure implementation.  
  
### Vulnerability  
Anyone with the **Manage auditing and security log** user right can clear the Security log to erase important evidence of unauthorized activity.  
  
### Countermeasure  
Ensure that only the local Administrators group has the **Manage auditing and security log** user right.  
  
### Potential impact  
Restricting the **Manage auditing and security log** user right to the local Administrators group is the default configuration.  
  
> [!WARNING]  
> If groups other than the local Administrators group have been assigned this user right, removing this user right might cause performance issues with other applications. Before removing this right from a group, investigate whether applications are dependent on this right.  
  
## See Also  
[User Rights Assignment](user-rights-assignment.md)  
  
