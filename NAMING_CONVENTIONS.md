# Naming conventions - Classes, Methods, Properties

- BactrianCamelCase for classes
- The class name is a noun, method names are verbs
- BactrianCamelCase for public properties
- For constants which are initialised at class construction, use public readonly
- Use dromedaryCase for variables
- Plain names for protected and private attributes (no underscores)
- Use this.variable to discriminate variable names, e.g. in the constructor
- Place properties at the top of the class
- Prefer immutable properties over mutable state
- Avoid boolean parameters at the end of an argument list
  - TODO example, reasoning
- Avoid optional parameters
  - TODO example, reasoning
- Validate parameters at the start of a method to reduce nesting and improve readability
  - TODO example, reasoning

```C#
public class ExampleClass
{
    public string Property { get; set; }
    public readonly string Name;
    protected readonly string information;
    private readonly string secret;

    public ExampleClass(string name, string information, string secret)
    {
        Name = name;
        this.information = information;
        this.secret = secret;
    }
}
```

Interfaces - prefix with a capital 'I', BactrianCamelCase the next words, even if the first word starts with I

```C#
public interface IImplicit
{
    string DoSomething();
}
```
