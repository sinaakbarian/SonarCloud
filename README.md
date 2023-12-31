# SonarCloud Integration

SonarCloud is an online tool designed to analyze code quality and assist in improving overall software quality. It performs analysis on code for issues such as code smells, vulnerabilities, and bugs. The following steps guide you through the process of integrating SonarCloud into your project.

## Usage

1. **Login to SonarCloud:**
   - Access SonarCloud by logging in to your account.

2. **Configuration:**
   - After logging in, configure your SonarCloud settings.

3. **GitHub Action Setup:**
   - Search for "sonarcloud-github-action" on Google.
   - Update the `sonar-project.properties` file with the following values, obtained from SonarCloud:
     ```properties
     sonar.organization=<replace with your SonarCloud organization key>
     sonar.projectKey=<replace with the key generated when setting up the project on SonarCloud>
     ```
   
4. **GitHub Action Workflow:**
   - Add the following YAML configuration to your project's GitHub Actions workflow file (e.g., `workflows/sonarcloud.yml`):
     ```yaml
     jobs:
       sonarcloud:
         runs-on: ubuntu-latest
         steps:
         - uses: actions/checkout@v3
         
         - name: SonarCloud Scan
           uses: sonarsource/sonarcloud-github-action@master
           env:
             GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
             SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
     ```

5. **Run the Project:**
   - With the SonarCloud integration in place, your project is now ready for analysis and improvement.

For more details and advanced configuration options, refer to the [SonarCloud Documentation](https://docs.sonarsource.com/sonarcloud/?_gl=1*1t70p4v*_gcl_au*MjEzNjA1OTA4OC4xNzAxNDY0NDI3*_ga*MzkyNDA3NTYwLjE3MDE0NjQ0Mjc.*_ga_9JZ0GZ5TC6*MTcwMTQ2NDQyNi4xLjAuMTcwMTQ2NDQyNi42MC4wLjA.).


