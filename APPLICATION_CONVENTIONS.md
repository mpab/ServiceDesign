# Conventions and Standards for Applications, APIs, Services, Libraries

| Project/Assembly | Description | IIS Folder Name | Internal Website | External Website |
| ------ | ------ | ------ | ------ | ------ |
| ApplicationUi | The user interface for the application | [env-]application.net/ApplicationUi | application.net | application.com |
| ApplicationApi | The API for the application, if more than one protocol is used, it should be encoded in the name. This exposes an IPC interface connection to clients | [env-]application.net/ApplicationApi | application_api.net  application_api.net/api/ application_api.net/swagger | application_api.com application_api.com/api/ |

---

| Project/Assembly | Description |
| ------ | ------ |
| ApplicationDtos | A Data Transfer Objects library shared between the Application and UI |
| ApplicationProxy | Client libraries/wrappers for accessing the API services. This defines the API interfaces and for many protocols (HTTP, MQ) is equivalent to an interface library |
| ApplicationDatabase | Database project for the application |
| ApplicationConsole | A command-line executable application |
| ApplicationDaemon | An executable process which is hosted as a Windows service or a Unix Daemon. This is distinct from an Api which exposes an interface |
| ApplicationLibrary | Library project for the application, may be used by the Api, Console or Daemon|
| ApplicationUiLibrary | Library project for the application User Interface, do not share between the Application and UI |

---

Data Model - DB and Dtos (across the wire)

Three options for naming:

<span style="color:green">Recommended</span>

__Naming conventions for API methods__

Follow the pattern <Type><Operation><Request/Response>
This is to discriminate the operations for each request/response pair

```csharp
ReportGetResponse Get(ReportGetRequest request); // separates the models DB from wire models, and makes request and response pair explicit

// mapping:
// DB      MAP     DTO
Report     <=>     ReportGetResponse
```

<span style="color:orange">Not recommended</span>

```csharp
ReportDto Get(ReportGetDto request); // separates out the DB from the DTO, but puts a noisy DTO 'handle' in the name
```

<span style="color:red">Strongly discouraged</span>

```csharp
Report Get(ReportRequest request); // mixing of wire and DB models in 'Report', use of DB Report and DTO ReportRequest
```
