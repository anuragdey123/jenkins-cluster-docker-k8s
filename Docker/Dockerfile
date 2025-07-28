FROM ubuntu:22.04

# Install Java, curl, git, sudo, systemctl (optional)
RUN apt-get update && \
    apt-get install -y openjdk-17-jdk curl gnupg git sudo wget systemctl

# Add Jenkins key and repo
RUN curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | tee \
    /usr/share/keyrings/jenkins-keyring.asc > /dev/null && \
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian binary/ | tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null

# Install Jenkins
RUN apt-get update && apt-get install -y jenkins

# Expose port
EXPOSE 8080

# Start Jenkins
CMD ["bash", "-c", "service jenkins start && tail -f /var/log/jenkins/jenkins.log"]
