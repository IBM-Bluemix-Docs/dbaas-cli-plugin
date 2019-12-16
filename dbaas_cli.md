---

copyright:
  years: 2018, 2019
lastupdated: "2019-12-16"

keywords: commands, cluster resource, CLI plugin

subcollection: dbaas-cli-plugin

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} CLI plug-in
{: #dbaas_cli_plugin}

Use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_full}} CLI plug-in to show information about your cluster, databases, users, and nodes, and to list and download log files.
{:shortdesc}

## Prerequisites
{: #prerequisites_dbaas_cli_plugin}

- Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started). {{site.data.keyword.cloud_notm}} CLI requires Java SDK 1.7.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`. In the terminal, you are notified when updates to the `ibmcloud` CLI and plug-ins are available. Be sure to keep your CLI up-to-date so that you can use all the available commands and flags.

- Install the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} CLI plug-in. See [Installing the {site.data.keyword.ihsdbaas_mongodb_full}} CLI plug-in](/docs/services/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-install-dbaas-cli-plugin) or [Installing the {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin) for detailed instructions. If you want to view the current version of your {{site.data.keyword.ihsdbaas_full}}
CLI plug-in, run `ibmcloud plugin show dbaas-cli`.

## CLI plug-in usage command
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

This command displays a list of DBaaS commands.

```
ibmcloud help dbaas
```
{: pre}

## Cluster command
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

This command shows the details of the specified cluster, including information about each replica member.  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster resource. To find the resource name, use the {{site.data.keyword.cloud_notm}} command `ibmcloud resource service-instances`.

## Database command
{: #db_cmds}

### `ibmcloud dbaas databases-list`
{: #db_list}

This command lists all the databases on the given cluster.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster resource.

## Database User commands
{: #user_cmds}

### `ibmcloud dbaas users-list`
{: #user_list}

This command lists all the database users.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster resource.

### `ibmcloud dbaas user-show`
{: #user_show}

This command shows details about a database user.

**For {{site.data.keyword.mongodb}}**

```
ibmcloud dbaas user-show <resource_name> <auth_db.username>
```
{: pre}

**For {{site.data.keyword.postgresql}}**

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster resource.

- *auth_db.username*

  Specific to {{site.data.keyword.mongodb}}: The authentication database name and user name, separated by a period, of the database user being shown.

- *username*

  Specific to {{site.data.keyword.postgresql}}: The user name of the database user being shown.

## Node command
{: #node_cmds}

To view the information about each node, use the [`cluster_show`](#cluster_show) command.

## Log commands
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

This command downloads a log file from a node.

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster resource.

- *instance_id*

  The ID of the node.

- *filename*

  The name of the log file to download. To determine the file name of the log file you want to download, use the [ibmcloud dbaas logs-list](#log_list) command.

### `ibmcloud dbaas logs-list`
{: #log_list}

This command lists all the log files on a node. You can use any of the listed file names as input to the [ibmcloud dbaas log-get](#log_get) command.

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster resource.

- *instance_id*

  The ID of the node.
