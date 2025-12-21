# API Service

## Overview

This is the API Service project, responsible for handling HTTP requests and responses.

## Requirements

* .NET 6.0
* C# 10.0

## Features

* Handles HTTP requests
* Supports GET, POST, PUT, DELETE, and PATCH methods
* Returns JSON responses

## Installation

1. Clone the repository using Git
2. Install the required .NET 6.0 runtime and SDK
3. Run `dotnet restore` to restore dependencies
4. Run `dotnet run` to start the service

## Configuration

The service uses the `appsettings.json` file for configuration. The default settings are:

```json
{
  "ServerAddress": "http://localhost:5000",
  "DatabaseConnection": "Server=myServerAddress;Database=myDataBase;User Id=myUsername;Password=myPassword;"
}
```

## Error Handling

The service uses a custom `ExceptionHandler` class to handle and log exceptions.

```csharp
public class ExceptionHandler : IExceptionHandler
{
    public void Handle(Exception exception)
    {
        // Log the exception
        // Send notifications to administrators
    }
}
```

## API Endpoints

### GET /users

* Returns a list of users

```csharp
[HttpGet]
public IActionResult GetUsers()
{
    var users = _userRepository.GetUsers();
    return Ok(users);
}
```

### POST /users

* Creates a new user

```csharp
[HttpPost]
public IActionResult CreateUser([FromBody] CreateUserRequest request)
{
    var user = _userRepository.CreateUser(request);
    return CreatedAtAction(nameof(GetUser), new { id = user.Id }, user);
}
```

## Running Tests

The service includes unit tests and integration tests. Run `dotnet test` to execute them.

## Contributing

Contributions are welcome! Please fork the repository, make changes, and submit a pull request.

## License

This project is licensed under the MIT License.