# RaceDay - PROG6212 Part 3

A full-stack web application for the South African running, walking, and cycling community. This project consists of a RESTful API (`RaceDay.API`) and an ASP.NET Core MVC Web Application (`RaceDay.Web`) that consumes the API.

## Setup and Run Instructions

### Prerequisites
- Visual Studio 2022
- .NET 8.0 SDK
- SQL Server / SQL Server Management Studio
- Azure Storage Account (for Blob Storage)

### Local Setup
1. Clone the repository.
2. Open the solution in Visual Studio.
3. Update the `appsettings.json` in `RaceDay.API` with your SQL Server connection string and Azure Blob Storage connection string.
4. Open the Terminal and run `Update-Database` to create the database.
5. Set both `RaceDay.API` and `RaceDay.Web` as Startup Projects.
6. Press `F5` to run. The API will open in Swagger, and the Web App will open in a separate tab.

## Docker Instructions
To run the MVC application in a Docker container, use the following commands:
1. Navigate to the project directory.
2. Build the Docker image:
   `docker build -t raceday-web -f RaceDay.Web/Dockerfile .`
3. Run the container:
   `docker run -d -p 8080:80 --name raceday-web-container raceday-web`
4. Open your browser and go to `http://localhost:8080`.

## User Roles

### Organiser
- Create, edit, and delete events.
- Upload event banner images (stored in Azure Blob Storage).
- Create race categories (distance, entry fee, max participants).
- View total enrolments and capture race results.

### Participant
- Browse upcoming events and view categories.
- Enrol in events.
- View personal enrolment history and results.
- View and update profile (including profile picture).

## Azure Blob Storage
The API integrates with Azure Blob Storage to handle image uploads. When an Organiser uploads an event banner, the MVC app sends it to the API, which uploads it to Azure and returns the public URL to be saved in the database.

## CI/CD Pipeline
This project uses GitHub Actions to automatically build the solution and run all unit tests on every push to the `main` branch. 
*(Note: Add your screenshot of the green build here)*

## YouTube Demonstration
Watch the full demonstration of the application, Docker setup, and Blob Storage integration here:
https://youtu.be/5ChcshHE9cA
