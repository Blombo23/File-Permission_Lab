<h1>File permissions in Linux</h1>
 
<h2>Description</h2>
The research team at my organization needs to update the file permissions for certain files and directories within the <b>projects</b> directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks:
<br />


<h2>Check file and directory details</h2>
The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.
<img src="https://imgur.com/2p7r2BM.png" height="80%" width="80%" alt="File permission"/>
The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the <b>projects</b> directory. I used the <b>ls</b>  command with the <b>-la</b>  option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named <b>draft</b>, one hidden file named <b>.project_x.txt</b> , and five other project files. The 10-character string in the first column represents the permissions set on each file or directory.

<h2>Describe the permissions string</h2>
The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:
<br />
- <b>1st character: </b> This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.
<br />
- <b>2nd-4th characters:</b> These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.
<br />
- <b>5th-7th characters: </b> These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.
<br />
- <b>8th-10th characters: </b> These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.
<br />
<br />
For example, the file permissions for <b>project_t.txt</b> are <b>-rw-rw-r--</b> . Since the first character is a hyphen (-), this indicates that <b>project_t.txt</b> is a file, not a directory. The second, fifth, and eighth characters are all <b>r</b>, which indicates that user, group, and other all have read permissions. The third and sixth characters are <b>w</b>, which indicates that only the user and group have write permissions. No one has execute permissions for <b>project_t.txt</b>.

<h2>Change file permissions</h2>
The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined <b>project_k.txt</b>  must have the write access removed for other.
<img src="https://imgur.com/9YAwkSC.png" height="80%" width="80%" alt="Change file permissions"/>
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The <b>chmod</b> command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the <b>project_t.txt</b> file. After this, I used <b>ls -la</b> to review the updates I made.


<h2>Change file permissions on a hidden file</h2>
The research team at my organization recently archived <b>project_t.txt</b> They do not want anyone to have write access to this project, but the user and group should have read access. 
<br />
<br />
The following code demonstrates how I used Linux commands to change the permissions:

<img src="https://imgur.com/OFAMqzM.png" height="80%" width="80%" alt="Change file permissions on a hidden file"/>

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know <b>.project_t.txt</b> is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with <b>u-w</b>. Then, I removed write permissions from the group with <b>g-w</b>, and added read permissions to the group with <b>g+r</b>. 


<h2>Change directory permissions</h2>
My organization only wants the <b>researcher2</b> user to have access to the <b>drafts</b> directory and its contents. This means that no one other than <b>researcher2</b> should have execute permissions.
<br />
<br />
The following code demonstrates how I used Linux commands to change the permissions:

<img src="https://imgur.com/iSJMUoX.png" height="80%" width="80%" alt="Change directory permissions"/>

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I previously determined that the group had execute permissions, so I used the <b>chmod</b> command to remove them. The  <b>researcher2</b> user already had execute permissions, so they did not need to be added.

<h2>Summary</h2>
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the <b>projects</b> directory. The first step in this was using <b>ls -la</b>  to check the permissions for the directory. This informed my decisions in the following steps. I then used the <b>chmod</b> command multiple times to change the permissions on files and directories.

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
