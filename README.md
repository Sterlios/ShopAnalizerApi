# .NET Backend Project Shop Analizer

This repositry is a project for analizing shops and their products. It is built using .NET and follows a layered architecture.

## Project Structure

```text
src/
├── Api/
├── Application/
├── Domain/
└── Infrastructure/

tests/
└── ...
```

Each layer is represented by a separate `.csproj` project.

## Architecture

The basic dependency structure is:

```text
        ┌─────────┐
        │   Api   │
        └────┬────┘
             │
             ▼
      ┌─────────────┐
      │ Application │
      └──────┬──────┘
             │
             ▼
       ┌─────────┐
       │ Domain  │
       └─────────┘

Infrastructure ──────► Domain
```

### Layers

| Layer            | Responsibility                                                                       |
| ---------------- | ------------------------------------------------------------------------------------ |
| `Api`            | HTTP API, controllers, authentication, authorization, and API configuration          |
| `Application`    | Use cases, application logic, DTOs, and application interfaces                       |
| `Domain`         | Domain entities, value objects, enums, and domain rules                              |
| `Infrastructure` | Database access, repositories, external services, and infrastructure implementations |

The exact contents of each layer may vary depending on the project.

---

# Project-Specific Configuration

After renaming the projects, configure the parts that are specific to the new application.

## Application Configuration

Check:

```text
src/Api/appsettings.json
src/Api/appsettings.Development.json
src/Api/appsettings.Local.json
```

Configure the values required by the new project, such as:

* database connection strings;
* external service URLs;
* authentication settings;
* Kafka configuration;
* Redis configuration;
* other environment-specific settings.

Do not commit passwords, API keys, tokens, or other secrets to the repository.

Use environment variables or an appropriate secret-management solution instead.

For Local environment use dotnet user-secrets

---

## Docker

If the template contains Docker configuration, check:

```text
Dockerfile
docker-compose.yml
.dockerignore
```

Update any project-specific values, such as:

* project names;
* assembly names;
* paths;
* ports;
* service names;
* environment variables.

---

## CI/CD

Check the GitHub CI configuration:

```text
github-ci.yml
```

Update any project-specific settings, such as:

* Docker image names;
* container registry paths;
* environment names;
* deployment configuration;
* project-specific variables.

---

# Verify the Project

After completing the renaming and configuration, restore the dependencies:

```bash
dotnet restore
```

Build the solution:

```bash
dotnet build
```

Run the tests:

```bash
dotnet test
```

If the project contains an API, run it:

```bash
dotnet run --project src/Api
```

Make sure the application starts successfully.

---