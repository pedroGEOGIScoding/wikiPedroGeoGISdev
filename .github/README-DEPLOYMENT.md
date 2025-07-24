# GitHub Pages Deployment Setup

This repository includes a GitHub Actions workflow that automatically deploys your Quarto website to GitHub Pages when you push commits to the `master` or `main` branch.

## Setup Instructions

### 1. Enable GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under **Source**, select **GitHub Actions**
4. Save the settings

### 2. Repository Permissions

The workflow is configured with the necessary permissions:

- `contents: read` - to read repository files
- `pages: write` - to deploy to GitHub Pages
- `id-token: write` - for authentication

### 3. Workflow Features

The workflow (`deploy-quarto.yml`) includes:

- **Triggers**: Runs on push to `master`/`main` branches and pull requests
- **Quarto Setup**: Installs the latest pre-release version of Quarto
- **Multi-language Support**: Sets up both R and Python environments
- **Dependency Management**: Automatically installs R and Python dependencies
- **Automatic Rendering**: Renders your Quarto project
- **GitHub Pages Deployment**: Deploys the rendered site to GitHub Pages

### 4. Dependencies

The workflow will automatically install:

- **R packages**: `rmarkdown`, `knitr` (or from `renv.lock` if present)
- **Python packages**: `jupyter`, `matplotlib`, `pandas`, `numpy` (or from `requirements.txt` if present)

### 5. Output

After successful deployment, your website will be available at:
`https://[your-username].github.io/[repository-name]`

## Customization

- To add more R dependencies, create an `renv.lock` file or modify the R installation step
- To add more Python dependencies, create a `requirements.txt` file
- The workflow uses Ubuntu latest and can be customized for different OS requirements

## Troubleshooting

- Check the **Actions** tab in your GitHub repository for build logs
- Ensure your `_quarto.yml` is properly configured
- Verify that all referenced files in your Quarto project exist
