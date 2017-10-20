FROM microsoft/nanoserver:latest
LABEL maintainer="me@david-obrien.net"
ARG downloadUriGrafana=https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-4.5.2.windows-x64.zip
RUN powershell -command "Invoke-WebRequest -Uri $env:downloadUriGrafana -Method Get -OutFile .\grafana.zip -Verbose"
RUN powershell -command "Expand-Archive .\grafana.zip -DestinationPath ."
ADD dashboards c:/grafanadashboards
ADD start-grafana.ps1 start-grafana.ps1
WORKDIR grafana-4.5.2/bin
EXPOSE 3000
ENTRYPOINT ["powershell", "-file", "c:/start-grafana.ps1"]