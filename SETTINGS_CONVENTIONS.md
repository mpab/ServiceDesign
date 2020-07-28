# App settings and other configuration files

## Convention

- Map configuration nodes to a POCO (Plain Old C# Object)
- The fully-qualified POCO namespace is the configuration node key
- Do not use default values
- Do not accept null values
- Do not accept empty strings
- If the configuration node is badly formed, fail (throw an exception)
- All POCO fields must be present in the configuration node

## Azure KeyVault integration

Convention: Local settings take priority over Azure KeyVault

- Read configuration files (configuration pattern )
  - If the configuration node is badly formed, fail (throw an exception)
- If configuration node is not present, read from Azure KeyVault
  - If the configuration node is badly formed, fail (throw an exception)
- AKV key is mapped to the POCO namespace (convert dots to dashes)

## Examples/Samples

POCO

```C#
namespace Application.Settings
{
    public class ConnectionStrings 
    {
        public string Reporting { get; set; }
    }
}
```

JSON

```json
{
  "Application.Settings.ConnectionStrings": {
    "Reporting": "server=.\\SQLEXPRESS;Database=Reporting;Integrated Security=true"
  }
}

```

TODO: AKV, map the POCO?

- Application-Settings-ConnectionStrings