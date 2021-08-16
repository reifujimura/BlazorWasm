# ASP[]().NET Core Blazor WebAssembly

This repository is ASP[]().NET Core Blazor WebAssembly app example.

## Shared

Define shared types and interfaces.

```cs
using System;

namespace BlazorWasm.Shared
{
    public class WeatherForecast
    {
        public DateTime Date { get; set; }

        public int TemperatureC { get; set; }

        public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);

        public string Summary { get; set; }
    }
}
```

## ASP[]().NET Core

Configure Blazor WebAssembly files provider.

```cs
namespace BlazorWasm.Server
{
    public class Startup
    {
        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            // ... //

            // Add
            app.UseBlazorFrameworkFiles();
            app.UseStaticFiles();

            // ... //

            app.UseEndpoints(endpoints =>
            {
                // ... //
                endpoints.MapFallbackToFile("index.html"); // Add fallback.
            });
        }
    }
}

```

## Blazor WebAssembly

Call ASP[]().NET Core API.

```cs
protected override async Task OnInitializedAsync()
{
    // Update to WebAPI endpoint.
    forecasts = await Http.GetFromJsonAsync<WeatherForecast[]>("weatherforecast");
}
```
