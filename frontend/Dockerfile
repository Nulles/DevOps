FROM ubuntu:latest
RUN apt-get update && apt-get install -y wget git && apt-get clean && rm -rf /var/lib/apt/lists/*
RUN wget https://download.oracle.com/java/20/archive/jdk-20_linux-x64_bin.deb
RUN apt-get update
RUN apt-get install ca-certificates curl gnupg lsb-release -y
RUN apt install ./jdk-20_linux-x64_bin.deb -y
RUN git clone https://github.com/Nulles/frontend2.git /frontend
RUN apt update
RUN apt install default-jdk -y
RUN cd frontend && ls && chmod +x /frontend/gradlew && /frontend/gradlew build "-Pvaadin.productionMode"
WORKDIR /app
COPY . /app
CMD ["java", "-jar", "/frontend/build/libs/frontend-0.0.1-SNAPSHOT.jar"]