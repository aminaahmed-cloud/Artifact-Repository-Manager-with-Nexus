</details>
You and other teams in 2 different projects in your company see that they have many different small projects, including the NodeJS application you built in the previous step, the java-gradle helper application and so on. You discuss and decide it would be a good idea to be able to keep all these app artifacts in 1 place, where each team can keep their app artifacts and can access them when they need.

So they ask you to setup Nexus in the company and create repositories for 2 different projects.

******

<details>
<summary> Install Nexus on a server </summary>
 <br />

**steps:**

create a droplet on the server to install Nexus on:

<img src="https://i.imgur.com/xjp2OqM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/MfBPAFF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/PMWTtY5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/GrysRLx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/MhgFjjx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

download the latest verion from sonatype
`
wget https://download.sonatype.com/nexus/3/nexus-3.66.0-02-mac.tgz
`
untar the file nexus-3.66.0-02-mac.tgz
`
tar -zxvf nexus-3.66.0-02-mac.tgz
`
Then create a new user:

<img src="https://i.imgur.com/hVF8Nzl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Give permission to the new user to run Nexus: 
change permission to nexus user
`
chown -R nexus:nexus
`
<img src="https://i.imgur.com/P9m9K5i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

save the user configuration to a file to access nexus
`
vim nexus-3.66.0-02/bin/nexus.rc
`
switch from root to nexus

`
Su - Nexus
`
then start Nexus

<img src="https://i.imgur.com/dHV7ndT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/sodeCmp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

open port 8081 on the firewall to access:


<img src="https://i.imgur.com/1gLAHC8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


</details>

******

<details>
<summary> Create npm hosted repository </summary>
 <br />

**steps**


## Create npm Hosted Repository with a New Blob Store

1. **Create a New Blob Store:**

   - Log in to Nexus Repository Manager.
   - Navigate to "Repositories" in the sidebar.
   - Click on "Blob Stores" and then "Create blob store".
   - Enter a name for your new blob store and configure the necessary details.


<img src="https://i.imgur.com/8ESGdcI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

2. **Create a New npm Hosted Repository:**
   
   - Still under "Repositories", click on "Repositories" and then "Create repository".
   - Select "npm (proxy)", then click "Next".
   - Fill in the following details:
     - Name: Enter a name for your new npm hosted repository.
     - Blob Store: Choose the blob store you created in the previous step.
     - Version Policy: Choose the version policy that suits your requirements.
     - Layout Policy: Choose the layout policy (npm, npm (group), etc.).
   - Click "Create repository"

<img src="https://i.imgur.com/MmvZ13H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/EexwOYR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</details>

******

<details>
<summary> Create user for team 1 </summary>
 <br />

**steps**

1. **Log in to Nexus Repository Manager:**
   - Open your web browser and navigate to the Nexus Repository Manager web interface.

2. **Access Security Settings:**
   - Once logged in, click on the "Security" tab in the top navigation bar.

3. **Create User:**
   - In the "Security" section, click on "Users" in the sidebar.
   - Click on the "Create User" button.

4. **Fill in User Details:**
   - Enter the details for the new user, including:
     - Username: Choose a username for the user (e.g., `team1`).
     - First Name and Last Name: Optionally, provide the user's full name.
     - Email: Enter the user's email address.
     - Password: Set a secure password for the user.
     - Status: Ensure the status is set to "Active".

5. **Assign Roles:**
   - In the "Roles" section, assign appropriate roles to the user. For accessing an npm repository, you may want to assign roles like "nx-repository-view-npm-*" for read-only access or "nx-repository-admin-npm-*" for administrative access to npm repositories. You can also assign custom roles if needed.

6. **Save User:**
   - Click the "Create User" button to save the new user.
     
<img src="https://i.imgur.com/fzyP2oZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/cdQGcCB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


</details>

******

<details>
<summary>  Build and publish npm tar </summary>
 <br />


## Steps

1. **Prepare Your Node.js Application:**
   - Ensure your Node.js application is properly configured and ready for publication. This typically involves having a `package.json` file with necessary metadata and dependencies.

2. **Build the Package:**
   - Navigate to the root directory of your Node.js application in the terminal.
   - Run the following command to build your package:

     ```
     npm pack
     ```

   This command will generate a tarball file (`.tgz`) containing your Node.js application and its dependencies.

   <img src="https://i.imgur.com/dGsdXFr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


4. **Publish the Tarball to Nexus npm Repository:**
   - Once the tarball is generated, use the following command to publish it to the npm repository hosted in Nexus Repository Manager:

     ```
     npm publish --registry={npm-repo-url-in-nexus} {path/to/your/package.tgz}
     ```
<img src="https://i.imgur.com/mJUiP3o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


   Replace `{npm-repo-url-in-nexus}` with the URL of your npm repository in Nexus Repository Manager, and `{path/to/your/package.tgz}` with the path to the generated tarball file.




<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

