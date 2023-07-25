---
title: "Your CI/CD pipeline on AWS - Part 2"
datePublished: Tue Jul 25 2023 13:08:25 GMT+0000 (Coordinated Universal Time)
cuid: clkibbpfh000a0ajubkv687z6
slug: your-cicd-pipeline-on-aws-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690290475244/47944723-eca4-4f72-a4de-c16dadc5d3f2.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

## What is CodeBuild?

AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers.

### Read about the Buildspec file for Codebuild.

A `buildspec.yml` file is used in AWS CodeBuild to define the build and deployment phases for your project. It provides instructions to CodeBuild on how to build, test, and deploy your application. Below is a sample `buildspec.yml` file that you can use as a starting point for your project. Please note that you might need to customize it based on your specific project requirements and build process.

```yaml
version: 0.2

phases:
  install:
    runtime-versions:
      nodejs: 14 # Change this to the desired Node.js version
    commands:
      - npm install # Replace with your package manager and build commands

  pre_build:
    commands:
      - echo "Running pre-build tasks..." # Add any pre-build tasks here

  build:
    commands:
      - echo "Building the application..." # Replace with your build commands
      - npm run build # Example: For Node.js projects using npm

  post_build:
    commands:
      - echo "Running post-build tasks..." # Add any post-build tasks here
      - npm test # Replace with your testing command if applicable

artifacts:
  files:
    - '**/*' # Include all files in the build output
```

In this example, the `buildspec.yml` file is written in YAML format and contains the following phases:

1. **Install Phase:**
    
    * This phase installs any necessary dependencies for the build. In this example, it installs Node.js 14 and runs `npm install` to install the project's dependencies. Customize this phase based on your project's requirements.
        
2. **Pre-Build Phase:**
    
    * This phase can include any pre-build tasks that you want to execute before the actual build process. You can add additional commands here if needed.
        
3. **Build Phase:**
    
    * This phase contains the build commands for your project. In this example, it runs `npm run build`, assuming it's a Node.js project using npm. Adjust the build commands based on your specific project setup.
        
4. **Post-Build Phase:**
    
    * This phase can include any post-build tasks that need to be performed after the build. For example, running tests or additional steps.
        
5. **Artifacts:**
    
    * The `artifacts` section specifies which files should be included in the build output. The example includes all files `**/*`, but you can customize it to include only specific files or directories.
        

Remember to adjust the `buildspec.yml` file according to your project's specific build process, runtime, and deployment requirements. Once you have customized the file, commit it to your CodeCommit repository alongside your project code. CodeBuild will automatically use this file when you start a build for your project.

---

# **Task-01 :**

* ### create a simple index.html file in CodeCommit Repository
    
* ### you have to build the index.html using the nginx server
    

**<mark>Step1:-</mark>**

* We have already created the Repo in the CodeCommit (demo-app) so we will be using the same repo.
    
* There are two ways either directly create a file from the demo-app repository on the AWS console or make an index.html file locally and then push it to the CodeCommit, in my case I will go with creating a file locally and then push it to the CodeCommit repo.
    
* "Create file" and name it `index.html` on your local system.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690046210702/7d0adb3c-c486-4856-9e50-efc82974f484.png align="center")

* Commit the changes to the repository with a meaningful commit message.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690046456654/af7779ff-3e8e-4576-a352-49a189211e5a.png align="center")

* Verify Changes in CodeCommit.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690046620169/17a148f9-dcd4-4960-bc20-fb144eada4d1.png align="center")

---

# **Task-02 :**

* ### Add buildspec.yaml file to CodeCommit Repository and complete the build process.
    

**<mark>Step2:-</mark>**

* In the root directory of your project, create a `buildspec.yml` file.
    

```yaml
version: 0.2

phases:
  install:
    commands:
      - echo Installing NGINX
      - sudo apt-get update
      - sudo apt-get install nginx -y
  build:
    commands:
      - echo Build started on 'date'
      - cp index.html /var/www/html/
  post_build:
    commands:
      - echo Configuring NGINX

artifacts:
    files:
      - /var/www/html/index.html
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047006172/626fd19e-7020-4270-bb07-0e37ea2156d9.png align="center")

* **<mark>Step 3:</mark>**
    
* Commit the Buildspec.yml file to the CodeCommit repository along with the `index.html` file.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047241692/005fa053-f6db-42d9-9bd9-0bfdbd685c3c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047258555/ae085f47-9826-461f-b544-1745567764cd.png align="center")

**<mark>Step 4:-</mark>**

Start a CodeBuild Project

* Now, go to the AWS Management Console and navigate to the CodeBuild service.
    
* Click on "Create build project."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047381523/08d04c65-cf2a-4dc0-8dd3-90511813af33.png align="center")

* Configure the build project with your desired settings, including the CodeCommit repository source and other build configurations.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047465967/94139798-cb03-421f-862e-d45076af68f9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047508010/8747d283-e2dd-4c16-9c4b-87e3099a92ca.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047597525/6978c37f-8c54-47a8-85d5-343dab66b5f2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047624700/7e2906d2-03d1-48ae-bd9f-411bdbc938e8.png align="center")

* In the "Buildspec" section, choose "Use a buildspec file".
    

**<mark>Note:-</mark>**<mark>Buildspec name</mark> *\-* By default, CodeBuild looks for a file named buildspec.yml in the source code root directory. If your buildspec file uses a different name or location, enter its path from the source root here (for example, buildspec-two.yml or configuration/buildspec.yml).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047656037/ce4398de-84ae-4ad1-aef9-f069cd328120.png align="center")

* At last, Create build project.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047775988/9e84a096-3f8f-4469-9c89-54aa47389916.png align="center")

**<mark>Step 5:-</mark>**

Start a Build

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047957168/52d16908-76f8-4227-ba1b-9e405863660c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690048038390/23fc0a27-5041-4156-a498-fb59b73859ef.png align="center")

During the build process, Nginx will be installed, and the `index.html` file will be copied to the Nginx root directory. The resulting build artifacts will include the `index.html` file, which you can use for deployment or further processing as needed.

### **To add artifacts to a CodeBuild project and store them in an S3 bucket.**

**<mark>Step 1:-</mark>**

* First, create a S3 bucket and provide public access.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690048599062/8dce0884-2469-4692-8c5a-ffcb3f19fd83.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690048646385/0370e672-6b76-4d3c-9053-68d63fbb86cc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690048776643/eee99891-826c-4755-9648-e0ade8b845a9.png align="center")

* After this go back to "Edit Artifacts".
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690049001972/75bc0949-c0c9-4262-965f-419ed24a18b5.png align="center")

* At last click on "**Update Artifacts**" and start the "**Build again**" so that all our files get stored in the S3 bucket.
    
* After the build process is complete, the artifacts will be uploaded to the specified S3 bucket location.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690049599769/58ca38d7-665f-4f57-9fc2-3c0d8b0db34a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690049567588/1e88cde1-8bb3-47c1-9bda-d9fbc4fb947f.png align="center")

* Click on the 'index.html' file and click on the "**Open button**" next to the Download button.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690050405092/06349964-2d09-4951-b16b-36c099a2908b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690050503822/e51b18e5-6192-4b27-b53e-1009b9f8d312.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**