# File-Permissions-in-Linux
## Project description
The research team needed to update file permissions for files and directories in the projects directory reflect the correct levels of authorization. Maintaining proper authorization levels helps to keep systems and information secure and reflects the principle of least privilege. I needed to use Linux commands to manage file permissions in the `projects` directory to ensure that the correct permissions were set for files and directories, including hidden files.
## Check file and directory details
The following code demonstrates my process for auditing the existing permissions for a set directory. 

<img src="https://i.imgur.com/6TtuTtZ.png" alt="Linux bash shell"/>

I used the `ls -la` command to list all files and directories in the projects directory, including any hidden files along with their current permissions.
Describe the permissions string
The permissions string begins with either a `-` or a `d` indicating if the item is a file or a directory. The next 3 characters indicate permissions for the user, with `r` indicating reading permissions, `w` indicating writing permissions, and `x` indicating execution permissions. A `-` indicates the absence of permissions. The following set of 3 characters reflects the permissions for the group, and the last 3 characters represent the permissions for other users.

For example, the permissions set for the projects directory are `drwxr-xr-x`. 
`d` signifies that this is a directory. 
`rwx` shows the permissions for the user. The user has read, write, and execute privileges
`r-x` shows the permissions for the group. The group has read and execute privileges.
`r-x` shows the permissions for other users. Other users have read and execute privileges.

## Change file permissions
The organization determined that other users should not be allowed to write to files in this directory. Permissions need to be changed for `project_k.txt` to remove other writing permissions.

The file `project_m.txt` is restricted and should not be readable or writable by the group or other users. Permissions need to be changed for `project_m.txt` to remove group reading permissions.

The following code demonstrates how I used Linux commands to change the permissions:

<img src="https://imgur.com/0MPzpjc.png" alt="Linux bash shell"/>

`chmod` changes file permissions and requires two arguments—the permissions that need to be changed and the name of the file or directory that these changes need to be made to. Here `o-w` and `g-r` are indicating to remove writing permissions from other users and reading permissions from the group, respectively. 
## Change file permissions on a hidden file
`.project_x.txt` is a hidden file that has been archived and should not be written to by anyone. The user and group should still be able to read this file. Currently the user has reading and writing permissions and the group has only writing permissions. This needs to be updated to remove writing permissions from the user and group, and provide the group with reading permissions.

<img src="https://imgur.com/aIwxL9o.png" alt="Linux bash shell"/> 

## Change directory permissions
The organization determined that only the `researcher2` user should be allowed to access the drafts directory and its contents. Permissions need to be updated to remove execute privileges from the group.

The following code demonstrates how I used Linux commands to change the permissions:

<img src="https://imgur.com/Hop9aHZ.png" alt="Linux bash shell"/> 

## Summary
I reviewed and changed multiple permissions in order to ensure appropriate access for files and directories in the projects directory. I used `ls -la` to review current permissions against those outlined by my organization. I then used `chmod` in order to make changes to file permissions to align with the permissions laid out by my organization. By ensuring that only the necessary permissions are in place, we are able to better safeguard data through the principle of least privilege.
