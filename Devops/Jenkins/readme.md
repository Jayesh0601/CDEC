### jenkins installation (redhat)
....
# 1. Update system packages
sudo yum update -y

# 2. Install wget (needed to fetch the Jenkins repo file)
sudo yum install -y wget

# 3. Install Java 21 (Jenkins requires Java 17 or 21)
sudo yum install -y fontconfig java-21-openjdk

# 4. Add the Jenkins repo
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo

# 5. Import the Jenkins GPG key
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

# 6. Refresh package metadata
sudo yum upgrade -y

# 7. Install Jenkins
sudo yum install -y jenkins

# 8. Reload systemd and start Jenkins
sudo systemctl daemon-reload
sudo systemctl enable jenkins
sudo systemctl start jenkins

# 9. Check status
sudo systemctl status jenkins

# 10. Get the initial admin password
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
....

### Jenkins Installation(ubuntu)
````
sudo apt update
sudo apt install fontconfig openjdk-21-jre -y
java -version
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins -y

````
