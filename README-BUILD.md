
# Compile Without Installing Software

You can compile **HRWinFormsApp** without installing anything locally using **GitHub Actions** or **Azure DevOps Pipelines**. Both options produce downloadable artifacts:

## Option 1: GitHub Actions
1. Create a new GitHub repository and push the contents of `WinForms_OptionB/` (root of this package).
2. Ensure your default branch is `main`.
3. The workflow at `.github/workflows/build.yml` will run automatically (or trigger manually via **Actions → Build WinForms .NET 8 → Run workflow**).
4. When it finishes, go to **Actions → the latest run → Artifacts** and download:
   - `hrwinformsapp-framework-dependent` (requires .NET 8 Desktop runtime to run),
   - `hrwinformsapp-self-contained-win-x64` (single-file exe, no runtime install).

## Option 2: Azure DevOps Pipelines
1. In your Azure DevOps project, create a new pipeline and point it to your repository.
2. Choose **Existing Azure Pipelines YAML file** and select `azure-pipelines.yml`.
3. Run the pipeline. Download artifacts from **Pipelines → the latest run → Artifacts (drop)**.

## Notes
- The self-contained build is larger but runs without installing the .NET runtime.
- If you need code signing for distribution inside your org, integrate a signing step in the pipeline.
- To change target architecture, edit `--runtime` (e.g., `win-x86`, `win-arm64`).
