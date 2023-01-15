# MySQL Layer for AWS Lambda

This repository provides a makefile and Dockerfile for creating a MySQL layer for use in AWS Lambda. The layer contains the necessary MySQL dependencies for connecting to a MySQL database from within a Lambda function.

## Requirements
- Docker
- Make
- AWS CLI (if you want to publish the layer to your AWS account)

## Usage
1. Clone this repository
2. Edit the makefile and set the following variables:
   - `ZIP_FILE_NAME`: the name of the zip file that will be created for the layer
   - `DOCKER_IMAGE_NAME`: the name of the Docker image that will be created
   - `PYTHON_VERSION`: the version of Python that you want to use for the layer
   - `AWS_LAMBDA_IMAGE_NAME`: the name of the AWS Lambda image that will be used to build the layer
3. Run `make layer` to create the layer
4. Optionally, you can run `make archive` to create a zip file of the layer
5. Optionally, you can run `make unzip` to unzip the archive and check its content.
6. If you want to publish the layer to your AWS account, you can run `make publish_layer`

## Cleaning up
You can run `make clean` to remove all files created by this process.

## Additional features
- `make zip_size` : prints the size of the created zip file
- `make zip_contents` : prints the contents of the created zip file
- `make check_image` : prints the created Docker image
- `make publish_layer` : publishes the layer to your AWS account

## How it works
The makefile uses Docker to create a container with the necessary dependencies. The container is built using the specified AWS Lambda image, and the MySQL dependencies are installed into the `./python/lib/python${PYTHON_VERSION}/site-packages` directory. Once the container is built, the layer is created by zipping the contents of the site-packages directory.

## Note
- Make sure to update the `./python/lib/python${PYTHON_VERSION}/site-packages` directory with the required dependencies before creating the layer.
- This is a basic example, you may need to adjust the `Dockerfile` and `makefile` to match your use case.

## Contact
If you have any issues or questions, please open an issue or contact the repository owner.
