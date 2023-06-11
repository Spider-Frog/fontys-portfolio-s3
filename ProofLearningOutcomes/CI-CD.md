# CI/CD
You **design and implement** a (semi)automated software release prcoess that matches the needs of the project context.

## What is CI/CD
<img src="https://github.com/Spider-Frog/fontys-portfolio-s3/blob/main/ProofLearningOutcomes/Images/CI-CD.png?raw=true" alt="CI/CD pipeline example" width="50%" height="50%" />

CI/CD is a software development practice that involves automating the integration, testing, and deployment of code changes, allowing for faster and more reliable releases.

## CI

For Continuous Integration (CI), I leveraged GitHub Actions to automate the process of testing and building my code. Whenever there was a push or merge on the main or dev branch of my repository, GitHub Actions would be triggered. These actions included running automated tests to ensure the compatibility and quality of the code changes. Additionally, the actions involved the build process, generating the necessary artifacts or executable files. By automating these tasks, I reduced the manual effort required for testing and building, ensuring that the codebase remained stable and reliable.

[**Example CI Workflow**](https://github.com/S3-Grocery-Market-Scraper/frontend/actions)

## CD

For Continuous Deployment (CD), I integrated Docker Hub into my CI/CD pipeline. After the CI phase was completed and the code changes were successfully tested and built, I configured the pipeline to push the built image to Docker Hub. Docker Hub served as a centralized repository for Docker images. By pushing the image to Docker Hub, my deployments were able to automatically pull the latest version of the image, simplifying the deployment process. This ensured that the deployments consistently used the most up-to-date version of the software, enabling rapid and reliable releases.

[**Example CD Workflow**](https://github.com/S3-Grocery-Market-Scraper/frontend/actions)

## Summary

In a nutshell, for CI, I utilized GitHub Actions to automate testing and building processes, while for CD, I integrated Docker Hub to automatically push the built image, facilitating seamless deployments and enabling the use of the latest version.