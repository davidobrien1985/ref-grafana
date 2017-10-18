FROM microsoft/nanoserver:latest
LABEL maintainer="me@david-obrien.net"
ARG downloadUriGrafana=https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-4.5.2.windows-x64.zip
RUN powershell -command "Invoke-WebRequest -Uri $env:downloadUriGrafana -Method Get -OutFile .\grafana.zip -Verbose"
RUN powershell -command "Expand-Archive .\grafana.zip -DestinationPath ."
RUN powershell -command "Set-Content -Value '$Grafana_database_host = $env:GRAFANA_BACKEND_SERVICE_HOST; Start-Process c:/grafana-4.5.2/bin/grafana-server.exe' -Path ./start-grafana.ps1 -Force -Verbose"
WORKDIR grafana-4.5.2/bin
EXPOSE 3000
ENTRYPOINT ["powershell", "-file", "c:/grafana-4.5.2/bin/start-grafana.ps1"]