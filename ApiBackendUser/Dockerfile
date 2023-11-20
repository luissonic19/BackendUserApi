#FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8-windowsservercore-ltsc2019 AS build
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
ARG source
WORKDIR /inetpub/wwwroot
EXPOSE 80
EXPOSE 5024

COPY ./:./
RUN dotnet restore

COPY . .
RUN dotnet publish -c realise -o out

FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /webapp
COPY --from=build /webapp/out .
ENTRYPOINT ["dotnet","ApiBackendUser.dll"]
