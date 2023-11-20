FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8-windowsservercore-ltsc2019 AS build
ARG source
WORKDIR /inetpub/wwwroot
EXPOSE 80
EXPOSE 5024
COPY ${source:-obj/Docker/publish} ./
RUN dotnet restore

COPY . .
RUN dotnet publish -c Realise -o out

FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8-windowsservercore-ltsc2019
WORKDIR /webapp
COPY --from=build /webapp/out .
ENTRYPOINT ["dotnet","ApiBackendUser.dll"]
