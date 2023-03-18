[DRAFT]

**THIS IS A CONTINUATION OF THE [ACTIVE DIRECTORY SIMULATION TUTORIAL](https://github.com/Cham0i/AD-creation-Azure)**

# Active Directory File Sharing

Configuring file sharing over a domain network with the appropriate users and permissions

## Making a Security Group (optional)

In the previous tutorial we used Organizational Units to seperate our users from each other based on their roles. Although we organized our users into their respective folders, the network does not assign different permission based on which organizational unit they are in. Groups are. There are two groups we can use in our network. Security Groups, which deal with users' permissions, and Distribution Groups, which deal with the email lists users' are in. We are going to add a new security group called "teachers" to further distinguish permission past our default "domain users" and "domain admins" security groups.

To do this we must go to Active Directory Users and Computers

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/1.png)

Right Click on empty space and click **new>group**. Then type your group name and use group type "security"

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/2.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/3.png)

We made a user called Mrs. Johnson in our previous tutorial which we will add to our new "teachers" security group by right clicking on our user and left clicking on "properties"

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/4.png)

Under "members of" tab and by clicking "add..." we will be able to add Mrs. Johnson to our new security group by typing "teachers" into the text box and searching for it ("check names"); it should find our security group. We will select the group and press "ok" 

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/5.png)

Your user should be added to the security group as shown below

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/6.png)

## Creating folders to share

We can choose to share certain files with certain people by assigning permissions to a folder. It is adviced to create our folders under "C:" or as close to our core directories as possible. This makes finding a folder much easier when it gets shared. To make a file right click on empty space and under "new" create a new "folder".

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/7.png)

Continuing our school example, we will create the following 3 folders:

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/8.png)

In order to test our permissions later, we are going to create text files within each folder to represent any files which a user may or may not have access to. Right click in open space and under "new" create a text file.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/9.png)

Now to actually set permissions. Rich click on a folder and go to "properties". 

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/10.png)

Under "sharing" tab click "share..."

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/11.png)

Since we are going to set up this folder to only be accessable to admins. We are going to look up the group "Domain Admins" by typing it in the text bar and clicking "add".

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/12.png)

Now all "Domain Admins" should be able to read this folder. Yet we want admins to also have the ability to change files in this folder, so by clicking the arrow we can change the permission level to be both read and write.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/13.png)

Clicking "share" will implement our changes and the next thing you should see is the directory path of the folder you shared. Normally you would take note of this path so that the person you want to share the folder can locate the file within our domain. However, since we made our folders withing "C:" our folders should be easy to find. 

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/14.png)

We are going to repeat this process with our "Joe's grades" folder; giving read/write permissions to the "teachers" security group and read permissions to a user named "Joe". 

**DISCLAIMER:** The problem with lumping all teachers into one security group, is that anyone under the security group "teacher", will have read/write perms to view and change Joe's grades. This is not a perfect system for our scenario since it's possible that Joe's biology teacher could tamper with the grades that Joe's english teacher gave him. It is also possible that ANY teacher within the school domain, wheather or not they know Joe, could tamper with Joe's grades. Creating niche security groups (or better yet, individually giving certain users permissions) is a much more tidous, yet secure way to assign permissions. This is also why we assinged read permissions to "Joe",the user, instead of "Domain Users". We wouldn't want some random student lurking into Joe's gradebook.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/15.png)

And with the "Newsletter" folder, every user in our domain will have read permissions.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/16.png)

## Accessing and Testing our Shared Files

### Joe ("Domain Users" group)

We are going to log out from our DC VM and login to our Client VM using the Joe (student) account. Next we open our file explorer and look up "\\dc". DC is the name of the VM where the folders were created. If the VM you used to created and share the folders is different replace it with your VM's name.

"\\[Your_VM's_Name_Here]"

Suppose you didn't take my advice in creating the folders under "C:". To find the folders that were shared you would have to use the address that was displayed after you clicked "Share". The address would look something like this: [insert example here]

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/17.png)

Fortunately, you heed my warning, and you should have something like this.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/18.png)

Lets test our permissions. As Joe we shouldn't be able to access our "Admins only" folder.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/19.png)

We should be able to read the "Newsletter"

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/20.png)

Yet, if we try to modify it...

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/21.png)

We shouldn't be able to make changes to the file. Meaning we don't have write permissions.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/22.png)

We should have access to view Joe's Grade folder, but if we try to change it (by deleting it in this case)...

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/23.png)

We can't (as Joe).

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/24.png)

### Mrs. Johnson ("Teachers" Security Group)

Lets log out and log back in; this time as Mrs. Johnson. We should still have no access to the admin folder.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/25.png)

But we should have the ability to modify files within "Joe's Grades".

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/26.png)

Whoops! Sorry Joe.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/27.png)

Lastly, we should be able to read the "Newsletter" folder, but unable to modify it.

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/28.png)


