# Use the official .NET 7 SDK image as a base image
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

# Set the working directory to /app
WORKDIR /app

# Copy the necessary files to the container
COPY . .

# Build the application
RUN dotnet publish -c Release -o out

# Build the runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime

# Set the working directory to /app
WORKDIR /app

# Copy the published files from the build image
COPY --from=build /app/out .

# Expose port 5000 for the application
EXPOSE 5000

# Command to run the application when the container starts
ENTRYPOINT ["dotnet", "MyWebApp.dll"]
