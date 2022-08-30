# swaggerSteps
## Swagger steps in .net core
- install Swashbuckle.AspNetCore package
- Add the Swagger generator to the services collection in Program.cs file

```
builder.Services.AddSwaggerGen(options =>
{
    options.SwaggerDoc("v1", new OpenApiInfo
    {
        Version = "v1",
        Title = "my title",
        Description = "",
        TermsOfService = new Uri("https://google.com.sa/"),
        Contact = new OpenApiContact
        {
            Name = "Example Contact",
            Url = new Uri("")
        },
        License = new OpenApiLicense
        {
            Name = "Example License",
            Url = new Uri("https://google.com.sa/")
        }
    });

    // using System.Reflection;
    var xmlFilename = $"{Assembly.GetExecutingAssembly().GetName().Name}.xml";
    options.IncludeXmlComments(Path.Combine(AppContext.BaseDirectory, xmlFilename));
});
```
- Enable the middleware for serving the generated JSON document and the Swagger UI, also in Program.cs:

```
app.UseSwagger();
app.UseSwaggerUI();
```
## Enable XML comments:
- Right-click the project in Solution Explorer and select Edit <project_name>.csproj
```
<PropertyGroup>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <NoWarn>$(NoWarn);1591</NoWarn>
</PropertyGroup>
```
- Add the following code to AddSwaggerGen service
```
 var xmlFilename = $"{Assembly.GetExecutingAssembly().GetName().Name}.xml";
 options.IncludeXmlComments(Path.Combine(AppContext.BaseDirectory, xmlFilename));
```
