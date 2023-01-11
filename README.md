# Organizing AWS Organizations

I used an IaC tool (org-formation) to create AWS Organization, Organization Units (OUs), and respective Accounts in those OUs.

Org-Formation is a neat tool that lets you handle account Organization via code and not in the Management Console using a native service like Control Tower. Some of the benefits of using this like any other IaC tool is ease of scalability-- I can quickly add multiple OUs and/or accounts from the cli, Security, improved efficiency, among others.

Check out the [Official Org-formation documentation](https://github.com/org-formation/org-formation-cli).

### Steps I took to Implement Org-Formation in my AWS Account
1. I installed the org-formation tool using `npm i aws-organization-formation -g`. Of course, this is assuming `npm` is already installed on your device. If not, you'll have to install it. 
2. I initialized `org-formation` using the command `org-formation init organization.yml --region us-east-1`

&ensp; *If you get an error initializing org-formation, it is likely related to your credentials. i.e. your credentials in the `~/.aws/credentials` file  &ensp; have expired. To fix this, create a new admin user in the AWS Console and add that user to the Administrator group then reconfigure on your cli, `aws configure` with the new user’s Access Key ID & Secret Access Key.*
 
3. After making changes to your `organization.yml` file, use `org-formation update organization.yml` to update your Organization.
After an update, you should get an updated message in your terminal similar to this:

![image](https://user-images.githubusercontent.com/64602124/211725762-e7e1a4bc-4b3f-4f13-bd4a-bc2c93bb044e.png)


Upon completion, in the AWS Console, the AWS Organization Structure is created as shown:

![image](https://user-images.githubusercontent.com/64602124/211720675-3eca0a42-cb6c-4b6c-91bc-5ec68dda4fbd.png)
