# Automated CI/CD Pipeline using Jenkins on AWS EC2

A Jenkins pipeline on AWS EC2 that automatically clones, builds, tests and deploys a Java web application whenever code is pushed to GitHub.

**Application:** Spring PetClinic (open source), forked from https://github.com/spring-projects/spring-petclinic
**My work:** the CI/CD pipeline and the AWS EC2 setup. The application code is not mine.

## Flow
GitHub push -> Webhook -> Jenkins (EC2) -> Clone -> Build -> Test -> Deploy

## Tools Used
AWS EC2 (t3.small, Ubuntu), Jenkins, GitHub Webhooks, Maven, Java, Linux, Shell

## Pipeline Stages
1. **Clone:** pulls the code from GitHub (main branch)
2. **Build:** `mvn clean package -DskipTests`
3. **Test:** (write what your Test stage runs)
4. **Deploy:** (write how the app is deployed, running on port 8081)

## Setup Steps
1. Launched an EC2 instance and opened ports 22, 8080 (Jenkins) and 8081 (application) in the Security Group
2. Installed Jenkins and created a pipeline job
3. Added a GitHub webhook pointing to `http://<ec2-ip>:8080/github-webhook/`
4. Enabled the "GitHub hook trigger for GITScm polling" option in the Jenkins job

## Challenges and Fixes
- **Not enough memory:** upgraded the instance from t3.micro to t3.small
- **Disk space full, pipeline stuck:** cleaned up storage
- **Port problems:** fixed the Security Group rules
- **Ubuntu version change** for compatibility

## Result
Pushed a change to the welcome page on GitHub. Jenkins started the pipeline automatically and the updated page went live.

## Screenshots
(add after uploading the images to a `screenshots/` folder)
