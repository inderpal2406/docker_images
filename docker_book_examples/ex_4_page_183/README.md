## Description

- These dockerfiles are used to automate testing in a CI env using docker and jenkins.
- The dependencies required to run tests are installed in an image using a Dockerfile.
- This image is then built and a container is started from it, and the code to be tested is mounted as a docker volume inside this container.
- The tests are executed by running the testing command (here, `ruby spec`) as a primary process of the container.
- Then we attach to the container to view test results. These test results are also captured using ci-reporter gem which presents test results to jenkins in xml format.
- Then we capture exit code of the container (exit code will not be equal to 1 if test fail).
- Then we exit the jenkins job with container exit status.
- The source code mounted inside container is cloned from a github repo.
