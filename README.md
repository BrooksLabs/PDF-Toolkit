
# HRWinFormsApp — WinForms .NET 8 (Option B: Enhanced Template)

This is a ready-to-build WinForms project targeting **.NET 8** with modern **Dependency Injection**, **Serilog logging**, a **typed settings service**, and an example **async background worker**.

## Structure

```
WinForms_OptionB/
  HRWinFormsApp.sln
  src/HRWinFormsApp/
    HRWinFormsApp.csproj
    Program.cs
    appsettings.json
    Services/
      AppSettings.cs
      ISettingsService.cs
      SettingsService.cs
      IBackgroundWorker.cs
      BackgroundWorkerService.cs
    Forms/
      MainForm.cs
      MainForm.Designer.cs
      AboutForm.cs
      AboutForm.Designer.cs
    Assets/
      (place icons/resources here)
    Properties/
```

## Build & Run

1. Open the solution in **Visual Studio 2022+** or run from CLI:
   ```bash
   dotnet restore
   dotnet build
   dotnet run --project src/HRWinFormsApp/HRWinFormsApp.csproj
   ```
2. Logs are written to `Logs/app-<date>.log` in the working directory.
3. Update `appsettings.json` to change the app name, environment, or theme.

## Notes
- The `ApplicationConfiguration.Initialize()` replacement ensures high DPI, visual styles, and compatible text rendering.
- DI registers services and forms; `MainForm` is resolved from the container.
- `BackgroundWorkerService` showcases safe async work with `IProgress<int>` posting back to the UI thread.
- `AboutForm` demonstrates consuming settings via DI.

## Customize
- Add icons to `Assets/` and set via `Form.Icon` or project properties.
- Add more services and register them in `Program.cs`.
- Switch logging sinks by adjusting the Serilog configuration in `Program.cs`.
