# Atlassian JIRA GOD Docker container

A docker image with both JIRA Service Desk and JIRA Software preinstalled, along with some additional plugins.

Additional plugins:

* Exocet
* Created On Transition by Bob Swift
* Project Configurator
* Refined Theme

## Usage

``` powershell
 docker run `
    --detach `
    --restart unless-stopped `
    --publish 5080:8080 `
    paulness15/docker-jira-all-software:latest
```

## Manual setup required on the first launch

Run through the install routine for `JIRA server edition` and `ServiceDesk server edition` after installing you will arrive at the Welcome to JIRA page.

You must next generate licence keys / free trials for JIRA Software and the plugins here.

JIRA Software
`http://localhost:5080/plugins/servlet/applications/versions-licenses`

Plugins
`http://localhost:5080/plugins/servlet/upm`

Ensure that you update all plugins, but there is no need to update JIRA Software.

## Backing up and restoring JIRA

## Backup

To backup the entire JIRA instance visit the backup administration webpage
`http://localhost:5080/secure/admin/XmlBackup!default.jspa`

Create a backup file
`backup_01.zip`

This will be saved to this location in the Docker container
`/var/atlassian/jira/export/backup_example_01.zip`

## Restore

To restore we can attach a bash terminal to the running container and move the backup file into the import folder. Move file from `/var/atlassian/jira/export/backup_example_01.zip` to `/var/atlassian/jira/import/backup_example_01.zip` using the following commands

Open a terminal and run the following commands:

Find the running container id

``` bash
docker ps
```

In my case it was `582a8ca3b15d`
``` bash
docker exec -it 582a8ca3b15d /bin/bash
mv /var/atlassian/jira/export/backup_example_01.zip /var/atlassian/jira/import/
```

Restore the file `backup_example_01.zip` using the website UI
`http://localhost:5080/secure/admin/XmlRestore!default.jspa`
