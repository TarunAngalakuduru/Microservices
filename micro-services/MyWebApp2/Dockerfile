# Use the official .NET SDK image as a build environment
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env

# Set the working directory
WORKDIR /app

# Copy the .csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy the main source code and build the application
COPY . ./
RUN dotnet publish -c Release -o out

# Build the runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app

# Copy the published files from the build environment
COPY --from=build-env /app/out .

# Expose the port the app will run on
EXPOSE 8000

# Define the command to run your app
CMD ["dotnet", "MyWebApp.dll"]
