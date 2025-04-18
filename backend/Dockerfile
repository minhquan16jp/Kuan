FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY . .
RUN dotnet restore GreenDrive.csproj
RUN dotnet build GreenDrive.csproj -c Release -o /app/build

FROM build AS publish GreenDrive.csproj
RUN dotnet publish GreenDrive.csproj -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .

ENTRYPOINT ["dotnet", "GreenDrive.dll"]
