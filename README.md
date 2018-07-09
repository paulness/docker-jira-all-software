# Atlassian JIRA GOD Docker container

A docker image with both JIRA Service Desk and JIRA Software preinstalled, along with some additional plugins.

Additional plugins:

* Exocet
* Jira Misc Workflow Extensions
* Project Configurator

## Usage

``` powershell
 docker run `
    --detach `
    --restart unless-stopped `
    --publish 5090:8080 `
    paulness15/jira-god-docker:latest
```

## Manual setup required on the first launch

You must generate licence keys / free trials for JIRA Software and the plugins here.

Plugins
`http://localhost:5090/plugins/servlet/upm`

JIRA Software
`http://localhost:5090/plugins/servlet/applications/versions-licenses`