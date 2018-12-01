---
 
copyright:
  years: 2018
lastupdated: "2018-11-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# IBM Cloud Hyper Protect DBaaS CLI plugin
{: #dbaas_cli_plugin}

Use the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} CLI plug-in to create, delete, 
and display information about databases and users, to show details about clusters, 
to start and stop instances, and to list and download log files.
{:shortdesc} 


**Note:** As a prerequisite for the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} plug-in, 
install the [{{site.data.keyword.Bluemix_notm}} CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](docs/cli/index.html#overview). 
{{site.data.keyword.Bluemix_notm}} CLI requires Java SDK 1.7.0.
The prefix for running commands by using the {{site.data.keyword.Bluemix_notm}} CLI is `ibmcloud`.

In the terminal, you are notified when updates to the `ibmcloud` CLI and plug-ins are available. 
Be sure to keep your CLI up-to-date so that you can use all the available commands and flags.

To install the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} CLI plug-in, 
see [Installing the DBaaS CLI plug-in](/docs/services/hyper-protect-dbaas/dbaasplugin_install.html#dbaas_plugin_install). 
If you want to view the current version of your {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} 
CLI plugin, run `ibmcloud plugin show dbaas-cli`.


## IBM Cloud Hyper Protect DBaaS commands index
{: #commands_index}

You can specify one of the following commands:

<table summary="CLI plugin usage command table"
<caption>CLI plug-in usage command</caption>  
 <thead>
 <th colspan="5">CLI plug-in usage command</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[ibmcloud dbaas help](#display_list)</td> 
 <td></td>
 <td></td> 
 <td></td> 
 </tr> 
 </tbody> 
 </table> 

<table summary="Cluster command table"
<caption>Cluster command</caption>  
 <thead>
 <th colspan="5">Cluster command</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[ibmcloud dbaas cluster-show](#cluster_show)</td>
 <td></td>
 <td></td>
 <td></td>
 </tr> 
 </tbody> 
 </table> 

<table summary="Database commands table"
<caption>Database commands</caption>  
 <thead>
 <th colspan="5">Database commands</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[ibmcloud dbaas database-create](#db_create)</td> 
 <td>[ibmcloud dbaas database-delete](#db_delete)</td>
 <td>[ibmcloud dbaas database-list](#db_list)</td>
 <td></td>
 </tr> 
 </tbody> 
 </table> 

 <table summary="Database User commands table"
<caption>Database User commands</caption>  
 <thead>
 <th colspan="5">Database User commands</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[ibmcloud dbaas user-create](#user_create)</td>
 <td>[ibmcloud dbaas user-delete](#user_delete)</td>
 <td>[ibmcloud dbaas user-list](#user_list)</td> 
 <td>[ibmcloud dbaas user-show](#user_show)</td>
 </tr> 
 </tbody> 
 </table> 

<table summary="Instance commands table"
<caption>Instance commands</caption>  
 <thead>
 <th colspan="5">Instance commands</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[ibmcloud dbaas instance-restart](#instance_restart)</td> 
 <td>[ibmcloud dbaas instance-start](#instance_start)</td>
 <td>[ibmcloud dbaas instance-stop](#instance_stop)</td>
 <td></td>
 </tr> 
 </tbody> 
 </table> 

<table summary="Log commands table"
<caption>Log commands</caption>  
 <thead>
 <th colspan="5">Log commands</th>
 </thead>
 <tbody> 
 <tr> 
  <td>[ibmcloud dbaas log-get](#log_get)</td>
 <td>[ibmcloud dbaas log-list](#log_list)</td> 
 <td></td>
 <td></td>
 </tr> 
 </tbody> 
 </table> 



## CLI plug-in usage command
{: #plugin_use}

### ibmcloud dbaas help
{: #display_list}

This command displays a list of DBaaS commands:

<pre><code class="hljs">ibmcloud help dbaas</pre></code>

**Command options**: None.  

## Cluster command
{: #cluster_cmds}

### ibmcloud dbaas cluster-show
{: #cluster_show}

This command shows the details of the specified cluster, including information about each replica member.  

**ibmcloud dbaas cluster-show** *resource_name*

**Command options**: 

| Parameter        |  Description                                                    |
| :--------------- |  :------------------------------------------------------------- |
| *resource_name*  |  The name of the cluster resource. To find the resource name, use the IBM Cloud command **ibmcloud resource service-instances**. |


## Database commands
{: #db_cmds}

### ibmcloud dbaas database-create
{: #db_create}

This command creates a database and, optionally, a collection. 

**Note:** For MongoDB, a collection *must* be created with the database.

**ibmcloud dbaas database-create** *resource_name* *database_name* [*collection*]

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*     |  The name of the cluster resource.        |
| *database_name* | The name of the database to create. |
| *collection*       | The name of the collection to create. Although this is an optional parameter, it is required for MongoDB. |


### ibmcloud dbaas database-delete
{: #db_delete}

This command deletes a database. 

**Note:** Do not delete a database if that database was created by credential 
and if that credential is still in use.

**ibmcloud dbaas database-delete** *resource_name* *database*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster resource.       |
| *database* | The name of the database to delete. |


### ibmcloud dbaas database-list
{: #db_list}

This command lists all the databases on the given cluster.

**ibmcloud dbaas database-list** *resource_name*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster       |

## Database User commands
{: #user_cmds}

### ibmcloud dbaas user-create
{: #user_create}

This command creates a database user.

***For MongoDB:***

**ibmcloud dbaas user-create** *resource_name* *auth_db.username* *password* [*db_name* [*db_name* [...]]]

***For PostgreSQL:***

**ibmcloud dbaas user-create** *resource_name* *username* *password* [*db_name* [*db_name* [...]]]

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*     |  The name of the cluster resource.        |
| *auth_db.username* | Specific to MongoDB: The authentication database name and user name, separated by a period, to be assigned to the database user being created. |
| *username* | Specific to PostgreSQL: The user name to be assigned to the database user being created. |
| *password*    |  The login password to be assigned to the user.      |
| *db_name*    |  Optional; this specifies a database for which the user will have read and write access.      |


### ibmcloud dbaas user-delete
{: #user_delete}

This command deletes a database user.

**Note:** Do not delete a database user if that database user was created by credential 
and if that credential is still in use.

***For MongoDB:***

**ibmcloud dbaas user-delete** *resource_name* *auth_db.username*

***For PostgreSQL:***

**ibmcloud dbaas user-delete** *resource_name* *username*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster resource.      |
| *auth_db.username* | Specific to MongoDB: The authentication database name and user name, separated by a period, of the database user being deleted. |
| *username* | Specific to PostgreSQL: The user name of the database user being deleted. |


### ibmcloud dbaas user-list
{: #user_list}

This command lists all the database users.

**ibmcloud dbaas user-list** *resource_name*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster resource.      |



### ibmcloud dbaas user-show
{: #user_show}

This command shows details about a database user.

***For MongoDB:***

**ibmcloud dbaas user-show** *resource_name* *auth_db.username*

***For PostgreSQL:***

**ibmcloud dbaas user-show** *resource_name* *username*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster resource.      |
| *auth_db.username* | Specific to MongoDB: The authentication database name and user name, separated by a period, of the database user being shown. |
| *username* | Specific to PostgreSQL: The user name of the database user being shown. |



## Instance commands
{: #instance_cmds}

**Note:** To use any of the instance commands listed here, you need to know the *instance_id*. 
To obtain an *instance_id*, first use this **ibmcloud** command to list
the service instance resource group names under your account: 

**ibmcloud resource service-instances**

Then enter one of the resulting *resource_names* in the following command to obtain the associated *instance_ids*: 

**ibmcloud dbaas cluster-show** *resource_name*


### ibmcloud dbaas instance-restart
{: #instance_restart}

This command restarts a running instance.

**ibmcloud dbaas instance-restart** *resource_name* *instance_id*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster resource.       |
| *instance_id* | The ID of the instance. |


### ibmcloud dbaas instance-start
{: #instance_start}

This command starts a stopped instance.

**ibmcloud dbaas instance-start** *resource_name* *instance_id*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster resource.      |
| *instance_id*    |  The ID of the instance.      |


### ibmcloud dbaas instance-stop
{: #instance_stop}

This command stops an instance (a replication member of the cluster).

**ibmcloud dbaas instance-stop** *resource_name* *instance_id*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*     |  The name of the cluster resource.        |
| *instance_id* | The ID of the instance. |


## Log commands
{: log_cmds}

### ibmcloud dbaas log-get
{: #log_get}

This command downloads a log file from an instance.

**ibmcloud dbaas log-get** *resource_name* *instance_id* *filename*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*    |  The name of the cluster resource.      |
| *instance_id*    |  The ID of the instance.      |
| *filename*    |  The name of the log file to download. **Note:** To determine the file name of the log file you want to download, use the [ibmcloud dbaas log-list](#log_list) command.  |


### ibmcloud dbaas log-list
{: #log_list}

This command lists all the log files on an instance. You can use any of the listed file names as input to the [ibmcloud dbaas log-get](#log_get) command.

**ibmcloud dbaas log-list** *resource_name* *instance_id*

**Command options**:

| Parameter        |  Description                  |
| :--------------- |  :--------------------------- |
| *resource_name*     |  The name of the cluster resource.        |
| *instance_id* | The ID of the instance. |


