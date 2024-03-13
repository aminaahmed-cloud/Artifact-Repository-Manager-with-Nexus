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



<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

