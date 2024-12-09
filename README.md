# Manage-authorization

Activity overview
In this lab activity, you’ll use Linux commands to configure authorization.

Authorization is the concept of granting access to specific resources in a system. It's important because without authorization any user could access and modify all files belonging to other users or system files. This would certainly be a security risk.

In Linux, file and directory permissions are used to specify who has access to specific files and directories. You’ll explore file and directory permissions and change the ownership of a file and a directory to limit who can access them.

As a security analyst, setting appropriate access permissions is critical to protecting sensitive information and maintaining the overall security of a system.

Scenario
In this scenario, you must examine and manage the permissions on the files in the /home/researcher2/projects directory for the researcher2 user.

The researcher2 user is part of the research_team group.

You must check the permissions for all files in the directory, including any hidden files, to make sure that permissions align with the authorization that should be given. When it doesn't, you must change the permissions.

Here’s how you’ll do this task: First, you’ll check the user and group permissions for all files in the projects directory. Next, you’ll check whether any files have incorrect permissions and change the permissions as needed. Finally, you’ll check the permissions of the /home/researcher2/projects/drafts directory and modify these permissions to remove any unauthorized access.

Task 1. Check file and directory details
In this task, you must explore the permissions of the projects directory and the files it contains. The lab starts with /home/researcher2 as the current working directory. This is because you're changing permissions for files and directories belonging to the researcher2 user.

1. Navigate to the projects directory.
The command to complete this step:
```bash
cd projects
```

2. List the contents and permissions of the projects directory.
The command to complete this step:
```bash
ls -l
```

The permissions of the files in the projects directory are as follows:
```bash
total 20
drwx--x--- 2 researcher2 research_team 4096 Oct 14 18:40 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Oct 14 18:40 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Oct 14 18:40 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 14 18:40 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 14 18:40 project_t.txt
```

-The 1st character indicates the file type. The d indicates it’s a directory. When this character is a hyphen (-), it's a regular file.

-The 2nd-4th characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.

-The 5th-7th characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.

-The 8th-10th characters indicate the read (r), write (w), and execute (x) permissions for the owner type of other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.

The second block of text in the expanded directory listing is the user who owns the file. The third block of text is the group owner of the file.
![image](https://github.com/user-attachments/assets/2a33d9e6-6d54-4c1c-8dc0-ecf50940eed4)

Check whether any hidden files exist in the projects directory.
The command to complete this step:
```bash
ls -la
```
![image](https://github.com/user-attachments/assets/975ba678-226b-46a1-bdf6-763b5b097a05)

Task 2. Change file permissions
In this task, you must determine whether any files have incorrect permissions and then change the permissions as needed. This action will remove unauthorized access and strengthen security on the system.

None of the files should allow the other users to write to files.

1. Check whether any files in the projects directory have write permissions for the owner type of other.
The command to complete this step:
```bash
ls -l
```

2. Change the permissions of the file identified in the previous step so that the owner type of other doesn’t have write permissions.
```bash
chmod o-w project_k.txt
```
![image](https://github.com/user-attachments/assets/7c438cd8-d5e1-4a12-bb97-71d475115b69)

3. The file project_m.txt is a restricted file and should not be readable or writable by the group or other; only the user should have these permissions on this file. List the contents and permissions of the current directory and check if the group has read or write permissions.
The command to complete this step:
```bash
ls -l
```
4. Use the chmod command to change permissions of the project_m.txt file so that the group doesn’t have read or write permissions.
The command to complete this step:
```bash
chmod g-r project_m.txt
```
![image](https://github.com/user-attachments/assets/56822eb4-86ae-4438-9cfd-ebdb412fe66b)

Task 3. Change file permissions on a hidden file
In this task, you must determine if a hidden file has incorrect permissions and then change the permissions as needed. This action will further remove unauthorized access and strengthen security on the system.

The file .project_x.txt is a hidden file that has been archived and should not be written to by anyone. (The user and group should still be able to read this file.)

1. Check the permissions of the hidden file .project_x.txt and answer the question that follows.
The command to complete this step:
```bash
ls -la
```
2. Change the permissions of the file .project_x.txt so that both the user and the group can read, but not write to, the file.
The command to complete this step:
```bash
chmod u-w,g-w,g+r .project_x.txt
```
![image](https://github.com/user-attachments/assets/49ca80a4-3ca6-4918-874a-052ee672ecca)

Task 4. Change directory permissions
In this task, you must change the permissions of a directory. First, you’ll check the group permissions of the /home/researcher2/projects/drafts directory and then modify the permissions as required. (You should be in the projects directory while managing the permissions of its subdirectory drafts.)

Only the researcher2 user should be allowed to access the drafts directory and its contents. (This means that only researcher2 should have execute privileges.)

1. Check the permissions of the drafts directory and answer the following question.
The command to complete this step:
```bash
ls -l 
```
2. Remove the execute permission for the group from the drafts directory.
The command to complete this step:
```bash
chmod g-x drafts
```

![image](https://github.com/user-attachments/assets/8393ee1c-2238-4542-a7e5-942d7999b3d5)

Conclusion

You now have practical experience in using basic Linux Bash shell commands to

examine file and directory permissions,
change permissions on files, and
change permissions on directories.
This is an important milestone on your journey toward managing authorization in Linux!






