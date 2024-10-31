# Use the OpenJDK 21 image
FROM ubuntu:latest

# Update the package list and install necessary dependencies
RUN apt-get update && \
    apt-get install -y wget git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN wget https://download.oracle.com/java/20/latest/jdk-20_linux-x64_bin.deb
RUN apt install ./jdk-20_linux-x64_bin.deb

# Cloning frontend repository
RUN git clone https://github.com/Nulles/frontend2.git /frontend

# Build your application using Gradle
RUN cd frontend && chmod +x /frontend2/gradlew && /frontend2/gradlew build "-Pvaadin.productionMode"

# Set the working directory
WORKDIR /app

# Copy your application code into the container
COPY . /app

# Specify the command to run your application
CMD ["java", "-jar", "/frontend2/build/libs/Git-0.0.1-SNAPSHOT.jar"]