# Build stage
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app

# Copy everything and restore
COPY . . 
RUN dotnet restore GreenDrive.csproj

# Build the project
RUN dotnet publish GreenDrive.csproj -c Release -o /out

# Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime
WORKDIR /app

# Copy published files from build stage
COPY --from=build /out .

# Start the app
ENTRYPOINT ["dotnet", "GreenDrive.dll"]
