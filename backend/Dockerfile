# ========================== BUILD STAGE ==========================
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

# Copy toàn bộ mã nguồn vào container
COPY . .

# Restore từ file chính xác
RUN dotnet restore backend/GreenDrive.csproj

# Build và publish
RUN dotnet publish backend/GreenDrive.csproj -c Release -o /app/publish

# ========================== RUNTIME STAGE ==========================
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "GreenDrive.dll"]
