
# Linux File Permissions



## Description
The research team within our organization must revise the file permissions for specific files and directories located in the `projects` directory. The current permissions do not align with the appropriate level of authorization. Verifying and adjusting these permissions is crucial for maintaining the security of our system. To accomplish this, I undertook the following actions:

## Check File and Directory Details
The following demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.


![App Screenshot](https://i.imgur.com/wfYzAFF.jpg)

The first step was to explore the permissions of the  `projects`  directory and all the files it contains:
- I navigated to the `projects` directory using the command `cd`  with the directory of `projects`.
- To list all the contents and their permissions I used the command  `ls -l` which shows the contents of the file. 

The current permissions for the directory `d`  are as follows: 
- The owner type user has full permissions.
- The owner type group can only execute.
- And the owner type other has no permissions as indicated by all the hyphens (`-`).

The current permissions for the file named “`project_k.txt`” are as follows:
- All the types of owners have the same permissions which are read (`r`) and write (`w`).

The current permissions for the file named “`project_m.txt`” are as follows:
- The owner type user has read (`r`) and write (`w`) permissions.
- The owner type group only has  read (`r`) permissions.
- And the owner type other has no permissions indicated my all the hyphens (`-`).

The current permissions for the file named “`project_r.txt`” are as follows:
- The owner types user and group both have read (`r`) and write (`w`) permissions.
- The owner type other only has read (`r`) permissions.

The current permissions for the file named “`project_t.txt`” are as follows:
- The owner types user and group both have read (`r`) and write (`w`) permissions.
- The owner type other only has read (`r`) permissions.


To show any hidden files I used the syntax `ls -la`. 

![App Screenshot](https://i.imgur.com/RcAPBu6.jpg)


## Describing the Permissions String

![App Screenshot](https://i.imgur.com/wfYzAFF.jpg)

The 10-character string can be deconstructed to determine who is authorized to access the
file and their specific permissions. The characters and what they represent are as follows:

- A directory with full permissions for all owners types would be `drwxrwxrwx`.
- Where the 1st character indicates the file type, the `d` indicates that its a directory, however when it is a hyphen (`-`) it's a regular file.
- The **2nd-4th** characters indicate the different types of permissions which are read (`r`), write (`w`), and execute (`x`) for the user. When there is a hyphen (`-`) that indicates that this permission is not granted for the user.
- The **5th-7th** characters indicate the different types of permissions which are read (`r`), write (`w`), and execute (`x`) for the group. When there is a hyphen (`-`) that indicates that this permission is not granted for the group.
- The **8th-10th** characters indicate the different types of permissions which are read (`r`), write (`w`), and execute (`x`) for the owner type. When there is a hyphen (`-`) that indicates that this permission is not granted for the user.

## Change File Permissions

The organization wanted to change the permissions for the file named “`project_k.txt`” so that the owner type other, doesn't have write permissions. 

To do that I used the command `chmod` followed by removing the write permissions from other indicated by `o-w` also to add the name of the file at the end to indicate from which file I wanted to change the permissions. 

![App Screenshot](https://i.imgur.com/qLjq6Zp.jpg)

To confirm the change we can use the command `ls -l` which does confirm that the correct changes have been made.

## Change File Permissions on a Hidden File

The organization also wanted to change the permissions for the hidden file named “`.project_x.txt`”. To change it so that both the user and group owner types only have read permissions. 

I first checked the current permissions using the command `ls -la` to reveal the file permissions of the hidden files. 


![App Screenshot](https://i.imgur.com/kdn6NXR.jpg)

To change the permissions so that both the user and group owner types only have read permissions I use the command `chmod u-w, g-w, g+r .project_x.txt`. 

![App Screenshot](https://i.imgur.com/cRGQ0JS.jpg)

The `u`  represents the user owner type, while the `g` represents the group owner type to change the permissions so that both user and group only have read permissions, we must first remove write permissions from the user indicated by `-w` and remove write permissions and add read permissions to group indicated by `-w` and `+r`.

Finally to confirm the correct changes have been made we use the `ls -la` command to show the permissions on the hidden files. 


## Change Directory Permissions

The organization also requests to make some changes so that only `researcher2` has access to the `drafts` file. This means that no one other than  `researcher2` should have execute permissions.

I used the command `chmod g-x drafts`  where `g` represents the owner type group and `-x` indicated to remove execute permissions, you must also add to the end `drafts` to make sure that it is the correct file you want to change the permissions on.


![App Screenshot](https://i.imgur.com/dO0gM5V.jpg)
## Summary

I adjusted various permissions to align with the desired level of authorization set by my organization for files and directories within the `projects` directory. Initially, I employed the `ls -la` command to inspect the directory's existing permissions, guiding my subsequent actions. Subsequently, I utilized the `chmod` command multiple times to modify the permissions on both files and directories.
