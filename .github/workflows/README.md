# Project Pipeline

This repository contains a GitHub Actions pipeline for building and releasing executables for your project.

## Pipeline Overview

The pipeline is triggered on every push to the `main` branch. It performs the following steps:

1. **Checkout code**: Retrieves the latest code from the repository.

2. **Set up Node.js**: Configures the environment with the specified Node.js version.

3. **Install dependencies**: Installs the project dependencies using npm.

4. **Modify package.json**: Modifies the `package.json` file to include the necessary configuration for building executables.

5. **Create placeholder executable**: Creates a placeholder executable file (`index.js`) for testing purposes.

6. **Build executables**: Uses the `npx pkg` command to build executables for different platforms (`node12-linux-x64`, `node12-win-x64`, `node12-macos-x64`).

7. **Create Release**: Creates a GitHub release using the `actions/create-release` action. The release is tagged with a specified version number and includes a release description.

8. **Upload executables**: Uses the `actions/upload-release-asset` action to upload the built executables as release assets. The assets are attached to the created GitHub release.

-The pipeline includes a step to install the required JavaScript package using npm.

-It uses the pkg command to create standalone executables from the TypeScript binary. Alternatively, you can use nexe by modifying the relevant step.

-The pkg command is executed with the appropriate targets (node12-linux-x64, node12-win-x64, node12-macos-x64) to create executables for multiple platforms.

-The pipeline uses the actions/create-release and actions/upload-release-asset actions to create a GitHub release and upload the generated executables as artifacts.
