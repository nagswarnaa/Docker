# Docker Commands 
Writing a Dockerfile involves understanding a set of commands and directives that define the environment and the steps needed to create and run a Docker image. Here’s a list of commonly used Dockerfile commands with brief explanations:

### Common Dockerfile Commands

1. **FROM**:
   - **Syntax**: `FROM <image>[:<tag>]`
   - **Purpose**: Specifies the base image to use for the Docker image.
   - **Example**: `FROM openjdk:11-jdk-slim`

2. **WORKDIR**:
   - **Syntax**: `WORKDIR <path>`
   - **Purpose**: Sets the working directory inside the container.
   - **Example**: `WORKDIR /usr/src/app`

3. **COPY**:
   - **Syntax**: `COPY <src> <dest>`
   - **Purpose**: Copies files or directories from the host file system into the container.
   - **Example**: `COPY . .`

4. **RUN**:
   - **Syntax**: `RUN <command>`
   - **Purpose**: Executes a command in the shell during the image build process.
   - **Example**: `RUN javac InteractiveProgram.java`

5. **CMD**:
   - **Syntax**: `CMD ["executable", "param1", "param2"]`
   - **Purpose**: Specifies the command to run within the container when it starts.
   - **Example**: `CMD ["java", "InteractiveProgram"]`

6. **ENV**:
   - **Syntax**: `ENV <key>=<value>`
   - **Purpose**: Sets an environment variable.
   - **Example**: `ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk`

7. **EXPOSE**:
   - **Syntax**: `EXPOSE <port>`
   - **Purpose**: Informs Docker that the container listens on the specified network ports at runtime.
   - **Example**: `EXPOSE 8080`

8. **ARG**:
   - **Syntax**: `ARG <name>[=<default value>]`
   - **Purpose**: Defines a build-time variable.
   - **Example**: `ARG VERSION=1.0`

9. **ENTRYPOINT**:
   - **Syntax**: `ENTRYPOINT ["executable", "param1", "param2"]`
   - **Purpose**: Configures a container to run as an executable.
   - **Example**: `ENTRYPOINT ["java", "-jar", "/usr/src/app/myapp.jar"]`

10. **VOLUME**:
    - **Syntax**: `VOLUME ["/data"]`
    - **Purpose**: Creates a mount point with the specified path and marks it as holding externally mounted volumes from the host or other containers.
    - **Example**: `VOLUME ["/var/log/myapp"]`

11. **USER**:
    - **Syntax**: `USER <username or UID>`
    - **Purpose**: Sets the user name or UID to use when running the image and for any `RUN`, `CMD`, and `ENTRYPOINT` instructions that follow it in the Dockerfile.
    - **Example**: `USER appuser`

12. **LABEL**:
    - **Syntax**: `LABEL <key>=<value>`
    - **Purpose**: Adds metadata to an image.
    - **Example**: `LABEL version="1.0"`

13. **ONBUILD**:
    - **Syntax**: `ONBUILD <command>`
    - **Purpose**: Adds a trigger instruction to the image that will be executed when the image is used as a base for another build.
    - **Example**: `ONBUILD RUN apt-get update`

### Example Dockerfile

Here's a complete example Dockerfile for the Java program from earlier:

```Dockerfile
# Use an official OpenJDK JDK runtime as a parent image
FROM openjdk:11-jdk-slim

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Compile the Java program
RUN javac InteractiveProgram.java

# Run the program
CMD ["java", "InteractiveProgram"]
```

### Docker Commands for Managing Dockerfiles

1. **Building an Image**:
   - **Command**: `docker build -t <image_name> .`
   - **Example**: `docker build -t java-interactive-program .`

2. **Running a Container**:
   - **Command**: `docker run <options> <image_name>`
   - **Example**: `docker run -it java-interactive-program`

3. **Listing Images**:
   - **Command**: `docker images`

4. **Removing an Image**:
   - **Command**: `docker rmi <image_name>`
   - **Example**: `docker rmi java-interactive-program`

5. **Viewing Container Logs**:
   - **Command**: `docker logs <container_id>`

These commands and instructions should help you write and manage Dockerfiles effectively.
