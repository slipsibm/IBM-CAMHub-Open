#  prereq-downloader.sh
This script can be used to download installation prerequisites for an offline deployment of IBM Cloud Automation Manager Content Runtime. For more information on usage and how to use this script, visit
[IBM Cloud Automation Manager Knowledge Center](https://www.ibm.com/support/knowledgecenter/SS2L37/content/content-runtime-offline-installation.html).

### Usage :
```
cd IBM-CAMHub-Open/bin/prereqDownloader/
./prereq-downloader.sh <platform> <platform_version> <optional: release>
```
- `platform` is the Linux distribution where the Content Runtime instance will be created. Valid options are `ubuntu`, `rhel` or `redhat`, and `centos`.

- `platform_version` is the version of this distribution. Valid inputs include `14.04` and `16.04` for Ubuntu and `7` for Red Hat and CentOS.

- `release` sets the version of products to be downloaded (available releases: `1.0` and `2.0`). If no `release` is provided, the latest release will be selected automatically. Details on these product versions can be found below.

#### Example
If a Content Runtime will be created in a VM running Ubuntu 16.04 and using the latest release
```bash
./prereq-downloader.sh ubuntu 16.04
```

### Notes :
- An installation of Docker is REQUIRED on the machine where the script is executed
- The versions of software to be downloaded can be confirmed under the "releases" folder.

### Output :
The following files are prerequisites for an offline Content Runtime installation, they have been placed in a folder named `prereqs_<platform>_<platform_version>_<release>` based on the parameters provided on execution.

camc-pattern-manager
- Docker image for IBM Cloud Automation Manager Content Runtime Pattern Manager

camc-sw-repo
- Docker image for the IBM Cloud Automation Manager Content Runtime software repository

chef.(deb,rpm)
- Platform specific Chef server package

chef-clients
- Folder that contains chef client installation binaries that will be stored in the Software Repository for later use

docker.(deb,rpm)
- Platform specific Docker package

docker-compose
- docker-compose binary

IBM-CAMHub-Open_advanced_content_runtime.tar
- Contains the Content Runtime Terraform templates that can be imported into GitLab or Github Enterprise (GHE). The loadContentRuntimeTemplates.sh script can be used to load the Content Runtime templates when the templates are not stored in GitLab or GHE

IBM-CAMHub-Open.tar
- Contains the Chef cookbooks that are used by the middleware terraform templates.

IBM-CAMHub-Open_templates.tar
- Contains the CAM Middleware, Integration and Starterpack templates. These can be placed in GitLab, GHE or manually loaded into Cloud Automation Manager.

## Product versions included
### Release 1.0

| Product   |      Version      |
|----------|:-------------:|
| chef server | 12.11.1 |
| chef client | 12.17.44 |
| docker | 17.09.0 |
| docker-compose | 1.17.0 |
| camc-sw-repo | 1.0-current |
| camc-pattern-manager | 1.0-current |
| advanced_content_runtime | 2.1 |
| cookbooks | 1.0 |
| middleware | 1.0 |
| starter | 1.0 |

#### Note
Release 1.0 should be used exclusively on environments that require Chef client version 12. This product is **no longer supported**, thus it is discouraged.

### Release 2.0

| Product   |      Version      |
|----------|:-------------:|
| chef server | 12.17.33 |
| chef client | 14.0.190 |
| docker | 17.09.0 |
| docker-compose | 1.17.1 |
| camc-sw-repo | 2.0-current |
| camc-pattern-manager | 2.0-current |
| advanced_content_runtime | 2.2 |
| cookbooks | 2.0 |
| middleware | 2.0 |
| starter | 2.0 |
