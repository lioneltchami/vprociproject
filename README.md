# From Code to Deployment - A Complete CICD journey for Java Apps using Jenkins, Nexus, Sonarqube, AWS ECR & ECS

This is a dynamic CI/CD project focused on enhancing the development process of a Java application. Employing diverse methodologies, I used tools and technologies to ensure seamless integration and continuous delivery. Notable elements of this project included integrating Jenkins, SonarQube, Nexus Repository, and more, optimizing the development workflow and ensuring top-notch code quality.

Noteworthy Achievements: Orchestrated the setup and configuration of Jenkins, streamlining the build and deployment process. Implemented SonarQube for code analysis, significantly improving code quality and maintainability. Established a robust Nexus Repository to efficiently manage artifact storage and versioning. Introduced a distinctive approach by integrating AWS Developer Tools such as CodeCommit, CodeArtifact, and CodeBuild. This integration facilitated secure and scalable development workflows in the cloud environment.

![CICD](https://miro.medium.com/v2/resize:fit:786/format:webp/0*n8m1Hqrg40oobuEV.png)

The project not only accelerated the deployment process but also elevated the overall code quality, leading to a more productive and collaborative environment

You can see the different parts of the project on the following branches:

1. CI using jenkins and more: ci-jenkins
2. CI/CD using jenkins and more: ci-jenkins
3. CI/CD using AWS Developer Tools and more: prod

### Prerequisites
- AWS Account
- GitHub account
- Jenkins
- Nexus
- SonarQube
- Slack

### Technologies 
- Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- MySQL

### Database
Here, we used Mysql DB 

**MSQL DB** Installation Steps for Linux Ubuntu 18.04:
- sudo apt-get update
- sudo apt-get install mysql-server

Then look for the file :
- **/src/main/resources/accountsdb**
- accountsdb.sql file is a mysql dump file.we have to import this dump to mysql db server
- > mysql -u <user_name> -p accounts < accountsdb.sql

## Intro To our Toolset

🌐 **AWS Account**: Our cloud powerhouse! 🏢 AWS (Amazon Web Services) provides the infrastructure for deploying, scaling, and managing our application in the cloud. With AWS, we'll have a reliable and flexible environment to run our CI/CD processes and deliver our app to the world! 🌍💻

🐙 **GitHub Account:** Our coding playground! 🚀 GitHub is where we'll host our Java application's source code, enabling collaboration, version control, and seamless integration with other DevOps tools. Get ready to explore the wonders of collaboration and open-source development! 🤝💻

🏗️ Jenkins: Our master orchestrator! 🎯 Jenkins will take the lead in automating our CI/CD **pipeline**. It'll handle tasks like building, testing, and deploying our Java app, freeing us up to focus on what we love—coding like pros! 💻🚀

📦 **Nexus**: Our artifact manager! 🌟 Nexus helps us store and organize our project's build artifacts. From dependencies to binaries, Nexus ensures everything is in its place, making our CI/CD pipeline super efficient and reliable! 🛠️🏢

🔍 **SonarQube**: Our code quality watchdog! 🚦 SonarQube will keep a close eye on our Java code, checking for bugs, vulnerabilities, and maintaining top-notch code quality. With SonarQube's insights, we'll polish our code to perfection! ✨🐞

💬 **Slack**: Our communication hub! 📢 Slack brings the team together, making it easy to share updates, celebrate wins, and handle any hiccups along the way. It's our go-to platform for staying connected and building a collaborative DevOps dream team! 🤗💬

Get ready to rock this CI/CD adventure! 🎉 Together, we'll automate, innovate, and create an impressive Java application that shines brightly in our tech galaxy! 🌌💫 Let's fire up those keyboards and make our DevOps dreams come true! 💪🔥


