FROM microsoft/nanoserver:latest
LABEL maintainer="me@david-obrien.net"
ARG grafanaVersion="5.2.2"
ARG downloadUriGrafana=https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-5.2.2.windows-amd64.zip

RUN powershell -command "Invoke-WebRequest -Uri $env:downloadUriGrafana -Method Get -OutFile .\grafana.zip -Verbose"
RUN powershell -command "Expand-Archive .\grafana.zip -DestinationPath ."

ARG downloadUriAzureMetrics=https://grafana.com/api/plugins/grafana-azure-monitor-datasource/versions/0.0.7/download
RUN powershell -command "Invoke-WebRequest -Uri $env:downloadUriAzureMetrics -Method Get -OutFile .\azuremetrics.zip -Verbose"
RUN powershell -command "Expand-Archive .\azuremetrics.zip -DestinationPath c:/grafana-$($env:grafanaVersion)/data/plugins"

ADD dashboards c:/grafanadashboards
ADD start-grafana.ps1 start-grafana.ps1
WORKDIR grafana-5.2.2/bin
EXPOSE 3000
ENTRYPOINT ["powershell", "-file", "c:/start-grafana.ps1"]