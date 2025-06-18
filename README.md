
<p><span style="color: #0000ff;"><strong>SonarQube</strong></span></p>
<ul>
<li><details><summary><strong> About SonarQube</strong></summary>
<ul>
<li>SonarQube is an open-source platform developed by Sonar Source for continuous inspection of code quality, static code analysis and code coverage of source code. it detects&nbsp;</li>
<li>It performs on source code where as OWASP-Dependency check performs on artifact/executable of application.</li>
<li>Once the test cases has been performed then sonarqube uses its report to analys the code.&nbsp; In java project test cases report stored in jacoco (java code coverage), Nodejs uses istanbul.</li>
<li><details><summary><strong>Code Quality Check</strong>:</summary>
<ul>
<li>In code quality check it finds bugs, vulnerability, codesmell, code duplication, technical debt in the soure code.&nbsp;</li>
<li>Bugs: Errors in the code where application behave badly or piece of code does not work properly.</li>
<li>Vulnerability: Weak section in the code which could be potential that outsider can hack or make it harm to application or source code.</li>
<li>Codesmell: There could be potential issues in the future.</li>
<li>code Duplication: repeated code has been written in the source code. Instead of writing identical code, developers can write function and use it in source code.</li>
<li>Technical Debt: To fix the above issues, developers required time and it will be calcuated and produce the required time.</li>
</ul>
</details></li>
<li><details><summary><strong>Code Coverage</strong>:</summary>
<ul>
<li>When developers write code for test cases it checks the functionality of code. if there are X lines in the code and developers wrote 10 test cases to check the functionality which covers 80% of lines which meas code coverage is 80%, to achieve 100% developers need to write more test cases to cover the missing lines.&nbsp;</li>
</ul>
</details></li>
<li><details><summary><strong>Versions</strong>: Two versions</summary>
<ul>
<li>Community Edition: It&nbsp;is free of cost but have restriction where it can only perfrom master/main branch and fixed number of lines it can cover in source code.&nbsp; multiple branches and unrestricted code lines can be achieved by using developers edition or installing plugins in community edition.</li>
<li>Developers Edition: It can perform on all branches and cover most source code lines as per package.</li>
</ul>
</details></li>
<li><details open=""><summary><strong>Package</strong>:&nbsp;</summary>
<ul>
<li>Sonar Scanner: It&nbsp;is a tool which perform both code quality and code coverage.&nbsp; It will generate a report and will be uploaded to sonar server.</li>
<li>Sonar Server:&nbsp;it will have report which sonar scanner generated.</li>
</ul>
</details></li>
</details>
<li><details><summary><strong> Installation</strong></summary>
<ul>
<li><details><summary>Ubuntu</summary>
<ul>
<li>Create 2 Ubuntu VMs, ,</li>
<li>First vm install JDK, jenkins
<ul>
<li>$sudo apt update</li>
<li>$sudo apt install openjdk-17-jre-headless -y</li>
<li>for jenkins installation: go to jenkins.ip/doc/book/installing/linux, copy the long term release command,</li>
<li>create a script: open a file $vi jenkins.sh and paste the code.&nbsp; make this file executable $sudo chmod +x jenkins.sh , run the file ./jenkins.sh</li>
<li>in browser http://ip:8080</li>
</ul>
</li>
<li>second vm install JDK, docker, sonarqube
<ul>
<li>Docker Install: sonarqube installation can be done with various ways,&nbsp; create a docker container and install sonarqube using image.
<ul>
<li>$sudo apt update</li>
<li>$sudo apt install docker.io -y&nbsp;</li>
<li>$docker pull hello-world (permission denied,&nbsp;by default only root user has permission to run docker commands,&nbsp; to give permission to other users enter the following command,</li>
</ul>
</li>
<li>Assing Permission to other user
<ul>
<li>$sudo chmod 666 /var/run/docker.sock</li>
</ul>
</li>
<li>SonarQube Install: docker is installed, in order to create a docker container an image is required.&nbsp;&nbsp;
<ul>
<li>$docker run -d --name sonar -p 9000:<span style="color: #ff0000;">9000</span>&nbsp;sonarqube:lts-community (-d = run in detach mode, -p = port, 9000 entered twice, one for VM and one for container (docker is installed in a VM)</li>
<li>To get the image of sonarqube go to hub.docker.com, official images and search sonarqube and take docker official image/tags and copy the link.</li>
<li><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar1.jpg" alt="" width="513" height="256" /></li>
</ul>
</li>
<li>sonarqube will be installed in a container, check container
<ul>
<li>$docker container ls</li>
<li>$docker exec -it container_ID /bin/bash (to go to container)</li>
</ul>
</li>
<li>Access Sonarqube:
<ul>
<li>open browser <a href="http://ip:9000">http://ip:9000</a>&nbsp;(default user=admin, password =admin)</li>
</ul>
</li>
</ul>
</li>
<li><strong>Community Branch Plugin</strong>: sonarqube community edition have limitation, a developer has developed a plugin which will allow to run sonarqube without limitation, like running on all branches and no limit on code lines coverage.
<ul>
<li>in google search : community branch plugin sonarqube or go to this url:&nbsp;<a href="https://github.com/mc1arke/sonarqube-community-branch-plugin?tab=readme-ov-file">https://github.com/mc1arke/sonarqube-community-branch-plugin?tab=readme-ov-file</a>&nbsp;
<ul>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar5.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar5.jpg" alt="" width="288" height="186" /></a></li>
<li>Copy the plugin JAR file to the&nbsp;<code>extensions/plugins/</code>&nbsp;directory of your SonarQube instance</li>
<li>Add&nbsp;<code>-javaagent:./extensions/plugins/sonarqube-community-branch-plugin-${version}.jar=web</code>&nbsp;to the&nbsp;<code>sonar.web.javaAdditionalOpts</code>&nbsp;property in your Sonarqube installation's&nbsp;<code>conf/sonar.properties</code>&nbsp;file, e.g.&nbsp;<code>sonar.web.javaAdditionalOpts=-javaagent:./extensions/plugins/sonarqube-community-branch-plugin-${version}.jar=web</code>&nbsp;where ${version} is the version of the plugin being worked with. e.g&nbsp;<code>1.8.0</code></li>
<li>Add&nbsp;<code>-javaagent:./extensions/plugins/sonarqube-community-branch-plugin-${version}.jar=ce</code>&nbsp;to the&nbsp;<code>sonar.ce.javaAdditionalOpts</code>&nbsp;property in your Sonarqube installation's&nbsp;<code>conf/sonar.properties</code>&nbsp;file, e.g.&nbsp;<code>sonar.ce.javaAdditionalOpts=-javaagent:./extensions/plugins/sonarqube-community-branch-plugin-${version}.jar=ce</code></li>
<li>Start Sonarqube, and accept the warning about using third-party plugins</li>
<li>copy .jar file and paste it in extensions/plugins folder</li>
<li>To get the jar file click on releases in the right hand side of url and select version of sonarqube.&nbsp;&nbsp;</li>
<li><a title="sonarqube community brach plugin" href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar6.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar6.jpg" alt="" width="364" height="199" /></a></li>
<li>right click and copy link address</li>
<li>Go to docker and get into docker container&nbsp;</li>
<li>$docker container ls (it will display container details)</li>
<li>$docker exec -it container_ID /bin/bash</li>
<li>$cd /extensions/plugins and download the jar file</li>
<li>$wget paste the above copied link address.</li>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar7.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar7.jpg" alt="" width="540" height="89" /></a></li>
<li>after downloaded, exit from container.</li>
<li>$docker restart container_ID</li>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar8.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar8.jpg" alt="" width="523" height="167" /></a></li>
<li>go to sonarqube server/administration/marketplace / installed plugins</li>
</ul>
</li>
<li>or sonarqube with the above plugin can be installed by downloading docker image from the below repository.</li>
<li>Docker image with the above plugin can be downloaded from repository:&nbsp;<a href="https://hub.docker.com/r/mc1arke/sonarqube-with-community-branch-plugin">https://hub.docker.com/r/mc1arke/sonarqube-with-community-branch-plugin</a>&nbsp;</li>
</ul>
</li>
</ul>
</details></li>
<li><details><summary>Windows</summary>
<ul>
<li>Download the Docker Desktop installer from the Docker website.</li>
<li>Run the installer and follow the setup instructions.</li>
</ul>
</details></li>
<li><details><summary>AWS Linux</summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>Mac O/S</summary>
<ul>
<li>Download Docker Desktop for Mac from the Docker website.</li>
<li>Install Docker Desktop by dragging it to the Applications folder.</li>
</ul>
</details></li>
<li><details><summary>Install Docker&nbsp;</summary>
<ul>
<li>$sudo apt install docker.io -y&nbsp;</li>
<li>$docker pull hello-world</li>
<li>$sudo chmod 666 /var/run/docker.sock (Assign permission to other users to access docker)</li>
</ul>
</details></li>
<li><details><summary>Install sonarqube in docker container</summary>
<ul>
<li>$docker run -d --name sonarqube -p 9000:9000 sonarqube:lts-community
<ul>
<li><code>-d</code>: Run the container in detached mode.</li>
<li><code>--name sonarqube</code>: Assign a name to the container (you can use any name).</li>
<li><code>-p 9000:9000</code>: port map 9000 for host and container (sonarqube installed in a container which is inside a host(docker).</li>
</ul>
</li>
<li>Access:&nbsp;<a href="http://localhost/ip:9000">http://localhost/ip:9000</a>
<ul>
<li>user: admin</li>
<li>Password: admin</li>
</ul>
</li>
</ul>
</details></li>
<li><details><summary>Install sonarqube with distribution Zip file</summary>
<ul>
<li>
<p># SonarQube Installation</p>
<p># Switch back to the ubuntu user<br />sudo -i</p>
<p># Install the 'unzip' package<br />apt install unzip</p>
<p># Add a new user named 'sonarqube'<br />adduser sonarqube</p>
<p># Switch to the 'sonarqube' user<br />sudo su sonarqube</p>
<p># Download SonarQube distribution zip file<br />wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.4.0.54424.zip</p>
<p># Unzip the downloaded file<br />unzip sonarqube-9.4.0.54424.zip</p>
<p># Set permissions for the SonarQube directory<br />chmod -R 755 /home/sonarqube/sonarqube-9.4.0.54424</p>
<p># Change ownership of the SonarQube directory<br />chown -R sonarqube:sonarqube /home/sonarqube/sonarqube-9.4.0.54424</p>
<p># Change to the SonarQube binary directory<br />cd sonarqube-9.4.0.54424/bin/linux-x86-64/</p>
<p># Start the SonarQube server<br />./sonar.sh start</p>
</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>Integration with Jenkins </summary>
<ul>
<li>After You setup Sonarqube then next install plugin sonar scanner plugin in jenkins and configure it in Manage Jenkins /Tools.</li>
<li>SonarQube Scanner: select and install</li>
<li>Eclipse Temurin Installer ( To keep different versions of tools)</li>
<li><strong>Configure sonar Scanner plugins</strong>
<ul>
<li>Go to Manage Jenkins\Tools</li>
<li>SonarScanner for MS Build Installations:It is used for MS Build Projects and for all other use sonar qube scanner installaiton.</li>
<li>Sonar Qube Scanner Installation:
<ul>
<li>Add installer:</li>
<li>Name: sonar-scanner</li>
<li>Version: latest&nbsp;</li>
</ul>
</li>
<li>Maven: configure if Maven is not installed in ubuntu&nbsp;</li>
</ul>
</li>
<li><strong>Sonar Server Configuration</strong>
<ul>
<li>Manage Jenkins /System /SonarQube Servers</li>
<li>Add SonarQube</li>
<li>Name = sonar</li>
<li>Server URL = <a href="http://ip:9000">http://ip:9000</a></li>
<li>Server Authentication token:</li>
<li>Add</li>
<li>Generate token:
<ul>
<li>Go to sonarqube server URL\adinistration\security\user\ click on update tokens or you can go to manage jenkins\credentials</li>
<li>Enter name = sonar-token, generate and copy token</li>
</ul>
</li>
<li>In add section enter the following:
<ul>
<li>Domain: global credentials.</li>
<li>Kind: secret text</li>
<li>scope:&nbsp; (global, jenkins,nodes, items, all child items)</li>
<li>secret : paste token</li>
<li>ID: sonar-token</li>
<li>DescriptionL sonar-token</li>
</ul>
</li>
<li>click add and select sonar-token.</li>
</ul>
</li>
<li>code</li>
</ul>
</details></li>
</ul>
</details></li>
<li><details><summary><strong> Configuration/Settings</strong></summary>
<ul>
<li><details><summary>Home Page</summary>
<ul>
<li><a title="Home Page" href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar2.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar2.jpg" alt="" width="240" height="151" /></a></li>
<li></li>
</ul>
</details></li>
<li><details><summary>Projects:</summary>
<ul>
<li>From Azure Devops:</li>
<li>From Bitbucket Server:&nbsp;</li>
<li>From Bitbucket cloud:&nbsp;</li>
<li>From Github:</li>
<li>From Gitlab:&nbsp;</li>
</ul>
</details></li>
<li><details><summary>Issues:</summary>
<ul>
<li>when perform code analysis, bugs, vulnerability etc will be displayed here.</li>
</ul>
</details></li>
<li><details><summary>Rules</summary>
<ul>
<li>different rules are setup for every programming language.&nbsp;&nbsp;</li>
<li>Group of rules for every language which is used to analyse code.&nbsp; copy and create custom rule.&nbsp;&nbsp;</li>
<li>Here you can include/exclude any rule which is not needed to be analysed.</li>
</ul>
</details></li>
<li><details><summary>Quality Profiles</summary>
<ul>
<li>rules of different language are available.</li>
</ul>
</details></li>
<li><details><summary>Quality Gates</summary>
<ul>
<li>Here you can define the criteria of quality of code,</li>
</ul>
</details></li>
<li><details><summary>Administration:</summary>
<ul>
<li>Configuration:
<ul>
<li>General settings: smtp configuration,&nbsp;
<ul>
<li>Authentication: github, gitlab, bigbucket</li>
<li>Devops platform integration: Github, bigbucket, azure devops, Gitlab</li>
<li>JaCoCo: It is defined code (in java: under &lt;properties&gt; xxxx &lt;/properties&gt;, test case results are stored in jacoco.exec)</li>
<li>Languages: java, ruby, python, list of suffixes.&nbsp;&nbsp;</li>
</ul>
</li>
<li>Encryption:</li>
<li>Webhooks:&nbsp;</li>
</ul>
</li>
<li>Security:
<ul>
<li>Users: create new user, activate/deactivate, generate tokens.</li>
<li>Groups:
<ul>
<li>Sonar-Administrators: Administrator group</li>
<li>Sonar-users: every authenticated user automatically belongs to this group.</li>
</ul>
</li>
<li>Global Permissions:
<ul>
<li>Grant and revoke permissions to make changes at the global level.</li>
<li>These permissions include editing Quality Profiles, executing analysis, and performing global system administration</li>
</ul>
</li>
<li>Permission Templates: create custom template.</li>
</ul>
</li>
<li>Projects:
<ul>
<li>Management:&nbsp;</li>
<li>Background task: When you run analysis, its status can be check here.</li>
</ul>
</li>
<li>System:
<ul>
<li>current status: up/down,</li>
<li>Detailed information of sonarqube.</li>
<li>Download system information and logs.</li>
</ul>
</li>
<li>Marketplace:
<ul>
<li>Version: current version installed and any available versions.&nbsp;</li>
<li>Plugins:installed and new plugins can be install.</li>
</ul>
</li>
</ul>
</details></li>
</ul>
</details></li>
<li><details><summary><strong> Settings in POM.XML file</strong>:&nbsp;</summary>
<ul>
<li><details><summary>Enable Code Coverage with JaCoCo, Add below items in POM.xml</summary>
<ul>
<li>Before Writing Pipeline Make sure below content is added in your pom.xml to get the code coverage.</li>
<li>&lt;properties&gt;<br /> &lt;!-- JaCoCo Properties --&gt;<br /> &lt;jacoco.version&gt;0.8.7&lt;/jacoco.version&gt;<br /> &lt;sonar.java.coveragePlugin&gt;jacoco&lt;/sonar.java.coveragePlugin&gt;<br /> &lt;sonar.dynamicAnalysis&gt;reuseReports&lt;/sonar.dynamicAnalysis&gt;<br /> &lt;sonar.jacoco.reportPath&gt;${project.basedir}/../target/jacoco.exec&lt;/sonar.jacoco.reportPath&gt;<br /> &lt;sonar.language&gt;java&lt;/sonar.language&gt;<br />&lt;/properties&gt;</li>
<li>
<p dir="auto">These properties are used to configure various aspects of the build process and the behavior of the tools involved, such as Java version, JaCoCo version (a code coverage tool), and SonarQube analysis settings.</p>
<p dir="auto">Here's an explanation of each property:</p>
<p dir="auto">&lt;java.version&gt;11&lt;/java.version&gt;: Specifies that the project is configured to use Java version 11.</p>
<p dir="auto">&lt;jacoco.version&gt;0.8.7&lt;/jacoco.version&gt;: Specifies the version of the JaCoCo code coverage tool to be used in the project. In this case, version 0.8.7 is specified.</p>
<p dir="auto">&lt;sonar.java.coveragePlugin&gt;jacoco&lt;/sonar.java.coveragePlugin&gt;: Specifies that JaCoCo will be used as the coverage plugin for SonarQube. This means that JaCoCo will be responsible for generating code coverage reports that SonarQube will use for analysis.</p>
<p dir="auto">&lt;sonar.dynamicAnalysis&gt;reuseReports&lt;/sonar.dynamicAnalysis&gt;: Indicates that SonarQube should reuse existing reports generated during the build process, rather than performing its own dynamic analysis.</p>
<p dir="auto">&lt;sonar.jacoco.reportPath&gt;${project.basedir}/../target/jacoco.exec&lt;/sonar.jacoco.reportPath&gt;: Specifies the path to the JaCoCo coverage report file. This file is typically generated during the build process and contains information about code coverage.</p>
<p dir="auto">&lt;sonar.language&gt;java&lt;/sonar.language&gt;: Indicates that the project's primary language is Java. This is used by SonarQube to properly analyze the code.</p>
</li>
<li>
<pre>&lt;<span class="pl-ent">dependency</span>&gt;
    &lt;<span class="pl-ent">groupId</span>&gt;org.jacoco&lt;/<span class="pl-ent">groupId</span>&gt; 
    &lt;<span class="pl-ent">artifactId</span>&gt;jacoco-maven-plugin&lt;/<span class="pl-ent">artifactId</span>&gt;
    &lt;<span class="pl-ent">version</span>&gt;0.8.7&lt;/<span class="pl-ent">version</span>&gt;
&lt;/<span class="pl-ent">dependency</span>&gt;</pre>
</li>
<li>
<pre>&lt;<span class="pl-ent">plugin</span>&gt;
    &lt;<span class="pl-ent">groupId</span>&gt;org.jacoco&lt;/<span class="pl-ent">groupId</span>&gt;
    &lt;<span class="pl-ent">artifactId</span>&gt;jacoco-maven-plugin&lt;/<span class="pl-ent">artifactId</span>&gt;
    &lt;<span class="pl-ent">version</span>&gt;${jacoco.version}&lt;/<span class="pl-ent">version</span>&gt;
    &lt;<span class="pl-ent">executions</span>&gt;
        &lt;<span class="pl-ent">execution</span>&gt;
            &lt;<span class="pl-ent">id</span>&gt;jacoco-initialize&lt;/<span class="pl-ent">id</span>&gt;
            &lt;<span class="pl-ent">goals</span>&gt;
                &lt;<span class="pl-ent">goal</span>&gt;prepare-agent&lt;/<span class="pl-ent">goal</span>&gt;
            &lt;/<span class="pl-ent">goals</span>&gt;
        &lt;/<span class="pl-ent">execution</span>&gt;
        &lt;<span class="pl-ent">execution</span>&gt;
            &lt;<span class="pl-ent">id</span>&gt;jacoco-site&lt;/<span class="pl-ent">id</span>&gt;
            &lt;<span class="pl-ent">phase</span>&gt;package&lt;/<span class="pl-ent">phase</span>&gt;
            &lt;<span class="pl-ent">goals</span>&gt;
                &lt;<span class="pl-ent">goal</span>&gt;report&lt;/<span class="pl-ent">goal</span>&gt;
            &lt;/<span class="pl-ent">goals</span>&gt;
        &lt;/<span class="pl-ent">execution</span>&gt;
    &lt;/<span class="pl-ent">executions</span>&gt;
&lt;/<span class="pl-ent">plugin</span>&gt;</pre>
</li>
</ul>
</details></li>
</ul>
</details></li>
<li><details><summary><strong>Sonar Analysis using Maven </strong></summary>
<ul>
<li>Step1: Set up Sonar Qube Server
<ul>
<li>Install and set up a SonarQube server either locally or using a cloud-based solution like SonarCloud.</li>
<li>Install Ubuntu, Install JDK, Install Docker, Install sonarqube in container using image.</li>
</ul>
</li>
<li>Step 2: Configure Sonarqube in Your Project.
<ul>
<li>In your project's root directory, create or update the&nbsp;<code>pom.xml</code>&nbsp;file to include the SonarQube plugin configuration. Add the following plugin to the&nbsp;<code>&lt;build&gt;</code>&nbsp;section:</li>
<li>
<pre>&lt;<span class="pl-ent">plugins</span>&gt;
    &lt;<span class="pl-ent">plugin</span>&gt;
        &lt;<span class="pl-ent">groupId</span>&gt;org.sonarsource.scanner.maven&lt;/<span class="pl-ent">groupId</span>&gt;
        &lt;<span class="pl-ent">artifactId</span>&gt;sonar-maven-plugin&lt;/<span class="pl-ent">artifactId</span>&gt;
        &lt;<span class="pl-ent">version</span>&gt;3.9.0.2155&lt;/<span class="pl-ent">version</span>&gt; <span class="pl-c">&lt;!-- Replace with the latest version --&gt;</span>
    &lt;/<span class="pl-ent">plugin</span>&gt;
&lt;/<span class="pl-ent">plugins</span>&gt;</pre>
</li>
<li>Define the SonarQube properties in your&nbsp;<code>pom.xml</code>&nbsp;to specify the SonarQube server URL, project key, project name, and project version. Add the following properties inside the&nbsp;<code>&lt;properties&gt;</code>&nbsp;section:</li>
<li>
<pre>&lt;<span class="pl-ent">properties</span>&gt;
    &lt;<span class="pl-ent">sonar</span>.host.url&gt;http://your-sonarqube-server-url&lt;/<span class="pl-ent">sonar</span>.host.url&gt;
    &lt;<span class="pl-ent">sonar</span>.projectKey&gt;unique-project-key&lt;/<span class="pl-ent">sonar</span>.projectKey&gt;
    &lt;<span class="pl-ent">sonar</span>.projectName&gt;Your Project Name&lt;/<span class="pl-ent">sonar</span>.projectName&gt;
    &lt;<span class="pl-ent">sonar</span>.projectVersion&gt;1.0&lt;/<span class="pl-ent">sonar</span>.projectVersion&gt;
&lt;/<span class="pl-ent">properties</span>&gt;</pre>
</li>
</ul>
</li>
<li>Step 3: Generate SonarQube Token
<ul>
<li>Log in to your SonarQube server.</li>
<li>Navigate to "My Account" or "User Settings."</li>
<li>Generate a new token for your analysis.</li>
</ul>
</li>
<li>Step 4: Integrate SonarQube Token.
<ul>
<li>In your project's&nbsp;<code>pom.xml</code>, add the SonarQube token as a property:</li>
<li>
<pre>&lt;<span class="pl-ent">properties</span>&gt;
    &lt;<span class="pl-ent">sonar</span>.login&gt;your-sonarqube-token&lt;/<span class="pl-ent">sonar</span>.login&gt;
&lt;/<span class="pl-ent">properties</span>&gt;</pre>
</li>
</ul>
</li>
<li>Step 5: Run the Analysis
<ul>
<li>Open a terminal or command prompt.</li>
<li>Navigate to your project's root directory.</li>
<li>Run the following Maven command to perform the SonarQube analysis:</li>
<li>mvn clean verify sonar:sonar
<ul>
<li>The&nbsp;<code>clean</code>&nbsp;phase ensures a clean build.</li>
<li>The&nbsp;<code>verify</code>&nbsp;phase compiles and tests your code.</li>
<li>The&nbsp;<code>sonar:sonar</code>&nbsp;goal triggers the SonarQube analysis.</li>
</ul>
</li>
</ul>
</li>
<li>Step 6:<strong>&nbsp;</strong>Review the Analysis Results.
<ul>
<li>After the analysis is complete, open your web browser and navigate to your SonarQube server's URL.</li>
<li>Log in to your SonarQube account.</li>
<li>You will see your project listed with the analysis results, including code quality metrics, issues, and more.</li>
</ul>
</li>
<li>Step 7:&nbsp;Address Issues and Repeat.
<ul>
<li>Review the issues and code quality metrics reported by SonarQube.</li>
<li>Make necessary code changes to address the reported issues.</li>
<li>Repeat the analysis steps to ensure improvements and monitor code quality over time.</li>
</ul>
</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary><strong>SonarQube for NodeJs</strong></summary>
<ul>
<li>To enable code coverage analysis for a Node.js-based application in SonarQube, you'll typically use a combination of tools to generate coverage reports and the SonarScanner to integrate those reports with SonarQube. Here are the general steps:</li>
<li>Pre-Requisite:
<ul>
<li>
<p dir="auto"><strong>Install SonarQube:</strong></p>
<ul dir="auto">
<li>Make sure you have SonarQube installed and running.</li>
</ul>
</li>
<li>
<p dir="auto"><strong>Install SonarScanner:</strong></p>
<ul dir="auto">
<li>Install the SonarScanner tool on your machine. You can find instructions in the official SonarScanner documentation.</li>
</ul>
</li>
<li>
<p dir="auto"><strong>Setup Node.js Project:</strong></p>
<ul dir="auto">
<li>Ensure your Node.js project uses a testing framework that supports coverage reporting, such as Mocha, Jest, or Istanbul.</li>
</ul>
</li>
</ul>
</li>
<li>Step 1:&nbsp;Install Coverage Reporting Tool:
<ul>
<li>Install a code coverage tool for your Node.js project. For example, you can use Istanbul, which is commonly used for this purpose. Install it as a development dependency:</li>
<li>npm install --save-dev nyc</li>
</ul>
</li>
<li>Step 2: Run Tests with Coverage:
<ul>
<li>Modify your test script in&nbsp;<code>package.json</code>&nbsp;to include coverage. For example, if you're using Mocha and Istanbul, your script might look like this:
<ul>
<li>
<pre><span class="pl-ent">"scripts"</span>: {
  <span class="pl-ent">"test"</span>: <span class="pl-s"><span class="pl-pds">"</span>nyc mocha<span class="pl-pds">"</span></span>
}</pre>
</li>
</ul>
</li>
<li>Then, run your tests with coverage:
<ul>
<li>
<pre>npm <span class="pl-c1">test</span></pre>
<pre>&nbsp;</pre>
</li>
</ul>
</li>
</ul>
</li>
<li>Step 3: Generate SonarQube Compatible Report:
<ul>
<li>Convert the coverage report generated by your tool into a format compatible with SonarQube. For Istanbul, you can use the istanbul-sonarqube-instrumenter:
<ul>
<li>npm install --save-dev istanbul-sonarqube-instrumenter</li>
</ul>
</li>
<li>After running your tests, use the instrumenter to generate the SonarQube-compatible report:
<ul>
<li>nyc report --reporter=lcov<br />istanbul-sonarqube-instrumenter</li>
</ul>
</li>
</ul>
</li>
<li>Step 4: Run Sonar Scanner:
<ul>
<li>Use the SonarScanner to analyze your project and send the coverage report to SonarQube. Modify your&nbsp;<code>sonar-project.properties</code>&nbsp;file accordingly:
<ul>
<li>
<pre><span class="pl-k">sonar.projectKey</span>=my-project
<span class="pl-k">sonar.projectName</span>=My Project
<span class="pl-k">sonar.sources</span>=src
<span class="pl-k">sonar.tests</span>=test
<span class="pl-k">sonar.javascript.lcov.reportPaths</span>=coverage/lcov-report/*.lcov</pre>
</li>
</ul>
</li>
<li>run Sonar Scanner:
<ul>
<li>sonar-scanner</li>
</ul>
</li>
</ul>
</li>
<li>Step 5: View Results in SonarQube
<ul>
<li>Open your SonarQube dashboard to view the analysis results, including code coverage metrics.</li>
</ul>
</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary><strong>SonarQube Arguments</strong></summary>
<ul>
<li>SonarQube provides a set of analysis parameters that you can use to configure and customize the behavior of the static code analysis. These parameters can be specified when running the analysis using the&nbsp;<code>sonar-scanner</code>&nbsp;command or when integrating SonarQube with your build tools. The available parameters may vary depending on the version of SonarQube and the analysis context. Below are some common SonarQube analysis parameters along with examples.</li>
<li>Project Configuration:
<ul>
<li><code>-Dsonar.projectKey</code>: Unique identifier for your project.
<ul>
<li>sonar-scanner -Dsonar.projectKey=my-project</li>
</ul>
</li>
<li><code>-Dsonar.projectName</code>: Name of your project.
<ul>
<li>
<pre>sonar-scanner -Dsonar.projectName=<span class="pl-s"><span class="pl-pds">"</span>My Project<span class="pl-pds">"</span></span></pre>
<pre>&nbsp;</pre>
</li>
</ul>
</li>
</ul>
</li>
<li>Source Code and Language Settings:
<ul>
<li><code>-Dsonar.sources</code>: Comma-separated list of directories containing source code.
<ul>
<li>sonar-scanner -Dsonar.sources=src</li>
</ul>
</li>
<li><code>-Dsonar.language</code>: Specify the main language of your project.
<ul>
<li>sonar-scanner -Dsonar.language=java</li>
</ul>
</li>
</ul>
</li>
<li>Analysis Scope:
<ul>
<li><code>-Dsonar.inclusions</code>&nbsp;/&nbsp;<code>-Dsonar.exclusions</code>: Include or exclude specific files from analysis.
<ul>
<li>
<pre>sonar-scanner -Dsonar.inclusions=<span class="pl-s"><span class="pl-pds">"</span>src/**/*.java<span class="pl-pds">"</span></span> -Dsonar.exclusions=<span class="pl-s"><span class="pl-pds">"</span>src/test/**/*<span class="pl-pds">"</span></span></pre>
</li>
</ul>
</li>
</ul>
</li>
<li>SonarQube Server Configuration:
<ul>
<li><code>-Dsonar.host.url</code>: URL of the SonarQube server.
<ul>
<li>sonar-scanner -Dsonar.host.url=http://localhost:9000</li>
</ul>
</li>
<li><code>-Dsonar.login</code>&nbsp;/&nbsp;<code>-Dsonar.password</code>: Authentication credentials for connecting to the SonarQube server.
<ul>
<li>sonar-scanner -Dsonar.login=myUsername -Dsonar.password=myPassword</li>
</ul>
</li>
</ul>
</li>
<li>Quality Gate Configuration:
<ul>
<li><code>-Dsonar.qualitygate.wait</code>: Wait for the SonarQube server to complete the analysis and return the quality gate status.
<ul>
<li>sonar-scanner -Dsonar.qualitygate.wait=true</li>
</ul>
</li>
</ul>
</li>
<li>Project Version and Branch:
<ul>
<li><code>-Dsonar.projectVersion</code>: Version of your project.
<ul>
<li>sonar-scanner -Dsonar.projectVersion=1.0</li>
</ul>
</li>
<li><code>-Dsonar.branch.name</code>: Specify the branch name if analyzing a specific branch.
<ul>
<li>sonar-scanner -Dsonar.branch.name=feature-branch</li>
</ul>
</li>
</ul>
</li>
<li>Other Settings:
<ul>
<li><code>-Dsonar.links.scm</code>: Specify the link to your source code management system.
<ul>
<li>sonar-scanner -Dsonar.links.scm=https://github.com/my-organization/my-project</li>
</ul>
</li>
<li><code>-Dsonar.verbose</code>: Output more detailed logs during the analysis.
<ul>
<li>sonar-scanner -Dsonar.verbose=true</li>
</ul>
</li>
</ul>
</li>
</ul>
</details></li>
<li><details><summary><strong>Setting Up SonarQube with Jenkins Pipeline</strong></summary>
<ul>
<li>Step 1: Create a Ubuntu VM &amp; install JDK, Docker
<ul>
<li>$sudo apt update</li>
<li>$sudo apt install openjdk-17-jre-headless -y</li>
<li>$sudo apt install docker.io -y</li>
<li>sudo chmod 666 /var/run/docker.sock (Assing permission to other users)</li>
</ul>
</li>
<li>Step 2: Setup SonarQube LTS-Community Version
<ul>
<li>docker run -d --name sonar -p 9000:9000 sonarqube:lts-community</li>
<li>For community branch plugin Version of SonarQube:
<ul>
<li>docker run -d --name sonar -p 9000:9000 mc1arke/sonarqube-with-community-branch-plugin</li>
</ul>
</li>
</ul>
</li>
<li>Step 3: Install SonarQube Scanner Plugin &amp; Configure in Jenkins Tools:
<ul>
<li>After You setup Sonarqube then next install plugin sonar scanner plugin in jenkins and configure it in Manage Jenkins /Tools.</li>
<li>SonarQube Scanner: select and install</li>
<li>Eclipse Temurin Installer ( To keep different versions of tools)</li>
<li><strong>Configure sonar Scanner plugins</strong>
<ul>
<li>Go to Manage Jenkins\Tools</li>
<li>SonarScanner for MS Build Installations:It is used for MS Build Projects and for all other use sonar qube scanner installaiton.</li>
<li>Sonar Qube Scanner Installation:
<ul>
<li>Add installer:</li>
<li>Name: sonar-scanner</li>
<li>Version: latest&nbsp;</li>
</ul>
</li>
<li>Maven: configure if Maven is not installed in ubuntu&nbsp;</li>
</ul>
</li>
<li><strong>Sonar Server Configuration</strong>
<ul>
<li>Manage Jenkins /System /SonarQube Servers</li>
<li>Add SonarQube</li>
<li>Name = sonar</li>
<li>Server URL = <a href="http://ip:9000">http://ip:9000</a></li>
<li>Server Authentication token:</li>
<li>Add</li>
<li>Generate token:
<ul>
<li>Go to sonarqube server URL\adinistration\security\user\ click on update tokens or you can go to manage jenkins\credentials</li>
<li>Enter name = sonar-token, generate and copy token</li>
</ul>
</li>
<li>In add section enter the following:
<ul>
<li>Domain: global credentials.</li>
<li>Kind: secret text</li>
<li>scope:&nbsp; (global, jenkins,nodes, items, all child items)</li>
<li>secret : paste token</li>
<li>ID: sonar-token</li>
<li>DescriptionL sonar-token</li>
</ul>
</li>
<li>click add and select sonar-token.</li>
</ul>
</li>
</ul>
</li>
<li>Step 4: Configure Webhook in Sonar Qube
<ul>
<li>Before adding a quality gate in the pipeline, ensure a webhook is added in SonarQube:
<ul dir="auto">
<li>Go to Administration &gt; Configuration &gt; Webhook.</li>
<li>Add the following format:&nbsp;<code>JENKINS_URL/sonarqube-webhook/</code></li>
</ul>
</li>
</ul>
</li>
<li>Step 5: Jenkins Pipeline
<ul>
<li>
<pre>pipeline {
    agent any
    
    tools {
        maven <span class="pl-s"><span class="pl-pds">'</span>maven3<span class="pl-pds">'</span></span>
        jdk <span class="pl-s"><span class="pl-pds">'</span>jdk17<span class="pl-pds">'</span></span>
        sonar <span class="pl-s"><span class="pl-pds">'</span>sonar-scanner<span class="pl-pds">'</span></span> <span class="pl-c">// Ensure SonarQube scanner tool is configured</span>
    }
    
    environment {
        <span class="pl-c1">SCANNER_HOME</span><span class="pl-k">=</span> tool <span class="pl-s"><span class="pl-pds">'</span>sonar-scanner<span class="pl-pds">'</span></span>
    }

    stages {
        stage(<span class="pl-s"><span class="pl-pds">'</span>Git Checkout<span class="pl-pds">'</span></span>) {
            steps {
                git <span class="pl-s"><span class="pl-pds">'</span>https://github.com/jaiswaladi2468/BoardgameListingWebApp.git<span class="pl-pds">'</span></span>
            }
        }
        
        stage(<span class="pl-s"><span class="pl-pds">'</span>Compile<span class="pl-pds">'</span></span>) {
            steps {
                sh <span class="pl-s"><span class="pl-pds">"</span>mvn compile<span class="pl-pds">"</span></span>
            }
        }
        
        stage(<span class="pl-s"><span class="pl-pds">'</span>Test<span class="pl-pds">'</span></span>) {
            steps {
                sh <span class="pl-s"><span class="pl-pds">"</span>mvn test<span class="pl-pds">"</span></span>
            }
        }
        
        stage(<span class="pl-s"><span class="pl-pds">'</span>SonarQube Analysis<span class="pl-pds">'</span></span>) {
            steps {
                withSonarQubeEnv(<span class="pl-s"><span class="pl-pds">'</span>sonar-1<span class="pl-pds">'</span></span>) {
                    sh <span class="pl-s"><span class="pl-pds">'''</span> $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Boardgame -Dsonar.projectKey=Boardgame \</span>
<span class="pl-s">                    -Dsonar.branch.name=pre-master -Dsonar.java.binaries=target/classes <span class="pl-pds">'''</span></span>
                }
            }
        }
        
        stage(<span class="pl-s"><span class="pl-pds">'</span>Quality Gate Check<span class="pl-pds">'</span></span>) {
            steps {
                script {
                    waitForQualityGate <span class="pl-c1">abortPipeline</span>: <span class="pl-c1">false</span>, <span class="pl-c1">credentialsId</span>: <span class="pl-s"><span class="pl-pds">'</span>new-sonar-token<span class="pl-pds">'</span></span>
                }
            }
        }
        
        stage(<span class="pl-s"><span class="pl-pds">'</span>Build<span class="pl-pds">'</span></span>) {
            steps {
                sh <span class="pl-s"><span class="pl-pds">"</span>mvn package<span class="pl-pds">"</span></span>
            }
        }
    }
}</pre>
</li>
</ul>
</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>Project: Perform Code Analysis on BoardGameListingWebApp</summary>
<ul>
<li><details><summary>Installation</summary>
<ul>
<li>Create 2 VMs (ubuntu),</li>
<li>first vm install JDK, jenkins
<ul>
<li>$sudo apt update</li>
<li>$sudo apt install openjdk-17-jre-headless -y</li>
<li>for jenkins installation: go to jenkins.ip/doc/book/installing/linux, copy the long term release command,</li>
<li>create a script: open a file $vi jenkins.sh and paste the code.&nbsp; make this file executable $sudo chmod +x jenkins.sh , run the file ./jenkins.sh</li>
<li>in browser http://ip:8080</li>
</ul>
</li>
<li>second vm install JDK, docker
<ul>
<li>sonarqube installation can be done with various ways,&nbsp; create a docker container&nbsp;&nbsp;</li>
<li>$sudo apt update</li>
<li>$sudo apt install docker.io -y&nbsp;</li>
<li>$docker pull hello-world (permission denied,&nbsp;by default only root user has permission to run docker commands,&nbsp; to give permission to other users enter the following command,</li>
<li>$sudo chmod 666 /var/run/docker.sock</li>
<li>docker is installed, in order to create a docker container an image is required.&nbsp;&nbsp;</li>
<li>$docker run -d --name sonar -p 9000:9000&nbsp;sonarqube:lts-community (-d = run in detach mode, -p = port, 9000 entered twice, one for VM and one for container (docker is installed in a VM)</li>
<li>To get the image of sonarqube go to hub.docker.com, official images and search sonarqube and take docker official image/tags and copy the link.</li>
</ul>
</li>
<li></li>
</ul>
</details></li>
<li><details><summary>Install Plugins on Jenkins &amp; Perform code analysis</summary>
<ul>
<li>Authentication (username &amp; token) and URL</li>
<li>Required: Configure Sonarqube server to upload the result &amp; Scanner to perform analysis:&nbsp;</li>
<li>Manage Jenkins/Plugins/Available Plugins:&nbsp;
<ul>
<li>SonarQube Scanner: select and install</li>
<li>Eclipse Temurin Installer ( To keep different version of tools)</li>
</ul>
</li>
<li><strong>Configure sonar Scanner plugins</strong>
<ul>
<li>Go to Manage Jenkins\Tools</li>
<li>SonarScanner for MS Build Installations:It is used for MS Build Projects and for all other use sonar qube scanner installaiton.</li>
<li>Sonar Qube Scanner Installation:
<ul>
<li>Add installer:</li>
<li>Name: sonar-scanner</li>
<li>Version: latest&nbsp;</li>
</ul>
</li>
<li>Maven: configure if Maven is not installed in ubuntu&nbsp;</li>
</ul>
</li>
<li><strong>Sonar Server Configuration</strong>
<ul>
<li>Manage Jenkins /System /SonarQube Servers</li>
<li>Add SonarQube</li>
<li>Name = sonar</li>
<li>Server URL = <a href="http://ip:9000">http://ip:9000</a></li>
<li>Server Authentication token:</li>
<li>Add</li>
<li>Generate token:
<ul>
<li>Go to sonarqube server URL\adinistration\security\user\ click on update tokens or you can go to manage jenkins\credentials</li>
<li>Enter name = sonar-token, generate and copy token</li>
</ul>
</li>
<li>In add section enter the following:
<ul>
<li>Domain: global credentials.</li>
<li>Kind: secret text</li>
<li>scope:&nbsp; (global, jenkins,nodes, items, all child items)</li>
<li>secret : paste token</li>
<li>ID: sonar-token</li>
<li>DescriptionL sonar-token</li>
</ul>
</li>
<li>click add and select sonar-token.</li>
</ul>
</li>
<li><strong>Jenkins: create item (sonar-analysis)</strong>
<ul>
<li>Name = sonar-analysis, select pipeline.</li>
<li>Groovy Script: <a title="groovy script" href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar1.txt" target="_blank" rel="noopener">click here</a>&nbsp;(make sure there are some case sensitive in code)</li>
<li>click Build now</li>
<li>Pipeline has been successfully executed.</li>
</ul>
</li>
<li><strong>Check code Analysis in SonarQube Server</strong>:
<ul>
<li>Go to projects in sonarqube server. click BoardGame.</li>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar3.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar3.jpg" alt="" width="510" height="298" /></a></li>
<li>click on issues for more details.</li>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar4.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar4.jpg" alt="" width="508" height="328" /></a></li>
<li></li>
<li></li>
</ul>
</li>
</ul>
</details></li>
<li><details><summary>Perform Code Analysis on BoardGameListingWebApp with Community Branch Plugin</summary>
<ul>
<li>There are two ways: install community branch plugin on sonarqube server or use docker image with builtin community branch plugin.</li>
<li>Create 2 VMs (ubuntu),</li>
<li>first vm install JDK, jenkins
<ul>
<li>$sudo apt update</li>
<li>$sudo apt install openjdk-17-jre-headless -y</li>
<li>for jenkins installation: go to jenkins.ip/doc/book/installing/linux, copy the long term release command,</li>
<li>create a script: open a file $vi jenkins.sh and paste the code.&nbsp; make this file executable $sudo chmod +x jenkins.sh , run the file ./jenkins.sh</li>
<li>in browser http://ip:8080</li>
</ul>
</li>
<li>second vm install JDK, docker, sonarqube
<ul>
<li>sonarqube installation can be done with various ways,&nbsp; create a docker container&nbsp;&nbsp;</li>
<li>$sudo apt update</li>
<li>$sudo apt install docker.io -y&nbsp;</li>
<li>$docker pull hello-world (permission denied,&nbsp;by default only root user has permission to run docker commands,&nbsp; to give permission to other users enter the following command,</li>
<li>$sudo chmod 666 /var/run/docker.sock</li>
<li>docker is installed, in order to create a docker container an image is required.&nbsp;&nbsp;</li>
<li>$docker run -d --name sonar -p 9000:9000&nbsp;sonarqube:lts-community (-d = run in detach mode, -p = port, 9000 entered twice, one for VM and one for container (docker is installed in a VM)</li>
<li>To get the image of sonarqube go to hub.docker.com, official images and search sonarqube and take docker official image/tags and copy the link.</li>
<li><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar1.jpg" alt="" width="513" height="256" /></li>
<li>sonarqube will be installed in a container, check container $docker container ls</li>
<li>Access: open browser <a href="http://ip:9000">http://ip:9000</a>&nbsp;(default user=admin, password =admin)</li>
</ul>
</li>
<li><strong>Plugin: sonarqube community edition</strong> have limitation, a developer has developed a plugin which will allow to run sonarqube without limitation, like running on all branches and no limit on code lines coverage.
<ul>
<li>in google search : community branch plugin sonarqube or go to this url:&nbsp;<a href="https://github.com/mc1arke/sonarqube-community-branch-plugin?tab=readme-ov-file">https://github.com/mc1arke/sonarqube-community-branch-plugin?tab=readme-ov-file</a>&nbsp;
<ul>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar5.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar5.jpg" alt="" width="288" height="186" /></a></li>
<li>copy .jar file and paste it in extensions/plugins folder</li>
<li>To get the jar file click on releases in the right hand side of url and select version of sonarqube.&nbsp;&nbsp;</li>
<li><a title="sonarqube community brach plugin" href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar6.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar6.jpg" alt="" width="364" height="199" /></a></li>
<li>right click and copy link address</li>
<li>Go to docker and get into docker container&nbsp;</li>
<li>$docker container ls (it will display container details)</li>
<li>$docker exec -it container_ID /bin/bash</li>
<li>$cd /extensions/plugins and download the jar file</li>
<li>$wget paste the above copied link address.</li>
<li>sudo&nbsp;</li>
<li>after downloaded, exit from container.</li>
<li>$docker restart container_ID</li>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar8.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar8.jpg" alt="" width="523" height="167" /></a></li>
<li>go to sonarqube server/administration/marketplace / installed plugins</li>
</ul>
</li>
<li>or sonarqube with the above plugin can be installed by downloading docker image from the below repository.</li>
<li>Docker image with the above plugin can be downloaded from repository:&nbsp;<a href="https://hub.docker.com/r/mc1arke/sonarqube-with-community-branch-plugin">https://hub.docker.com/r/mc1arke/sonarqube-with-community-branch-plugin</a>&nbsp;
<ul>
<li>$docker run -d --name sonar -p 9000:9000 mc1arke/sonarqube-with-community-branch-plugin</li>
</ul>
</li>
</ul>
</li>
<li><strong>Jenkins: create item (sonar-analysis-branch)</strong>
<ul>
<li>Name = sonar-analysis, select pipeline.</li>
<li>Groovy Script: <a title="groovy script" href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar2.txt" target="_blank" rel="noopener">click here</a>&nbsp;(add this parameter for branch=&nbsp;-Dsonar.branch.name=pre-prod )</li>
<li>click Build now</li>
<li>Pipeline has been successfully executed on branch pre-prod.</li>
<li><a href="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar9.jpg" target="_blank" rel="noopener"><img src="https://stardistributors.co.uk/devops/devops_tools/sonarqube/sonar9.jpg" alt="" width="492" height="249" /></a></li>
</ul>
</li>
<li>code</li>
</ul>
</details></li>
<li><details open=""><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
</ul>
</details></li>
<li><details><summary> Title </summary>
<ul>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
<li><details><summary>code </summary>
<ul>
<li>code</li>
<li>code</li>
<li>code</li>
</ul>
</details></li>
</ul>
</details></li>
</ul>



## Step-1 : Setup Linux VM (Amazon Linux AMI)

1) Login into AWS Cloud account
2) Launch Linux VM using EC2 service   
     - AMI : Amazon Linux
     - Instance Type : t2.medium       
4) Connect to VM using MobaXterm

## Step-2 : Install Docker In Linux VM

```
sudo yum update -y 
sudo yum install docker -y
sudo service docker start
sudo usermod -aG docker ec2-user
exit
```
## Step-3 : Rress 'R' to restart the session (This is in MobaXterm)

## Step-4 :  Verify docker installation
```
docker -v
```
## Step-5 : Run SonarQube using docker image
```
docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube:lts-community
```

## Step-6: Enable 9000 port number in Security Group Inbound Rules & Access Sonar Server
```
 - URL : http://public-ip:9000/
```
