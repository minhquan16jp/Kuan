# ================== Build stage ==================
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

# Copy code
COPY . .
RUN dotnet restore
RUN dotnet publish -c Release -o /app/publish

# ================== Runtime stage ==================
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .

EXPOSE 8080
ENTRYPOINT ["dotnet", "GreenDrive.dll"]
