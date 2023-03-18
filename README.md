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

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/7.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/8.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/9.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/10.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/11.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/12.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/13.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/14.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/15.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/16.png)

## Accessing and Testing our Shared Files 

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/17.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/19.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/20.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/21.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/22.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/23.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/24.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/25.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/26.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/27.png)

![alt text](https://github.com/Cham0i/AD-File-Sharing/blob/main/Filesharing_pics/28.png)
