FROM microsoft/nanoserver:latest
LABEL maintainer="me@david-obrien.net"
ARG downloadUriGrafana=https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-4.5.2.windows-x64.zip
RUN powershell -command "Invoke-WebRequest -Uri $env:downloadUriGrafana -Method Get -OutFile .\grafana.zip -Verbose"
RUN powershell -command "Expand-Archive .\grafana.zip -DestinationPath ."
RUN powershell -command "Set-Content -Value '[Environment]::SetEnvironmentVariable("GF_database_host", $ENV:GRAFANA_BACKEND_SERVICE_HOST); Get-Variable -Verbose; & c:/grafana-4.5.2/bin/grafana-server.exe' -Path ./start-grafana.ps1 -Force -Verbose"
WORKDIR grafana-4.5.2/bin
EXPOSE 3000
ENTRYPOINT ["powershell", "-file", "c:/start-grafana.ps1"]