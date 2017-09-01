FROM microsoft/nanoserver:latest
LABEL maintainer="me@david-obrien.net"
ARG downloadUriGrafana=https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-4.4.2.windows-x64.zip
RUN powershell -command "Invoke-WebRequest -Uri $env:downloadUriGrafana -Method Get -OutFile .\grafana.zip"
RUN powershell -command "Expand-Archive .\grafana.zip -DestinationPath ."
WORKDIR grafana-4.4.2/bin
EXPOSE 3000
ENTRYPOINT ["grafana-server.exe"]