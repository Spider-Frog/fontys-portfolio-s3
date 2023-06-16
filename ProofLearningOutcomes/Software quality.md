# Software quality
*You use software **tooling and methodology** that continuously monitors and improve the software quality during software development.*

To maintain software quality within my project, I have employed several methods:

## Integration tests

For the Backend API, I implemented integration testing. Initially, there were challenges in setting it up due to the asynchronous nature of Python's async/await system. However, I persevered and successfully configured the testing environment. Each test begins by making a call to the database to set up the necessary testing environment and then proceeds to test the endpoint or GraphQL query. You can refer to the code snippet below:

<img src="https://github.com/Spider-Frog/fontys-portfolio-s3/blob/main/ProofLearningOutcomes/Images/integration_tests_code.png?raw=true" alt="Integration tests code" width="50%" height="50%" />

The screenshot provided showcases an example of successful integration tests for the GraphQL queries related to companies.<img src="https://github.com/Spider-Frog/fontys-portfolio-s3/blob/main/ProofLearningOutcomes/Images/integration_tests_passed.png?raw=true" alt="Integration tests passed" width="50%" height="50%" />


## Component tests

For the frontend, I implemented component testing to ensure that the components I developed properly mount on the page. This testing approach helps validate the behavior and rendering of individual components. You can refer to the code snippet below:

<img src="https://github.com/Spider-Frog/fontys-portfolio-s3/blob/main/ProofLearningOutcomes/Images/component_tests_code.png?raw=true" alt="Component tests code" width="50%" height="50%" />

## CI

To automate the testing process, I integrated Continuous Integration (CI) into my project. This means that whenever code is pushed to the main or development branches, all tests are automatically executed. This practice ensures that the application undergoes thorough testing before being deployed to production. By catching potential issues early, CI helps maintain the stability and reliability of the application.

With these testing methods in place, I have implemented a comprehensive quality assurance strategy to ensure that my software meets the expected standards before deployment.
For more information about CI/CD click [here](https://github.com/Spider-Frog/fontys-portfolio-s3/blob/main/ProofLearningOutcomes/CI-CD.md)