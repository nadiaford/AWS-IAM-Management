# AWS IAM Management

**Disclaimer: The links mentioned within this project are unavailable.**

In this project, I simulated creating user groups, users, and setting permissions and policies. I demonstrated how policies are used to safeguard the organization's network. 

## 1. Set Up EC2 Instances

Tags are labels that help AWS account users identify and manage resources. Tags are useful for grouping, mass management, and applying security policies.

The tag I’ve used on my EC2 instances is called `Env`. The values I’ve assigned to my instances are `Production` and `Management`. These represent the two different environments we are using to build the app.

![Set Up EC2 Instances 1](https://i.imgur.com/mNPMTNh.png)
![Set Up EC2 Instances 2](https://i.imgur.com/bkvPIGe.png)

## 2. Add Policies

IAM Policies are rules that allow or deny users/resources permissions to perform certain actions on my AWS Account's resources.

![Set Up EC2 Instances 3](https://i.imgur.com/fP1YWCH.png)


For this project, I set up a policy using the JSON editor.

![Add Policies JSON](https://i.imgur.com/me4DZSl.png)

I created a policy that allows all EC2-related actions on all EC2 instances that have the `Env` tag set to `development`. However, it denies the ability to create and delete tags for **ALL** EC2 instances.

The `Effect`, `Action`, and `Resource` attributes of a JSON policy mean:
- **Effect**: `Allow` or `Deny`
- **Action**: The specific actions we want to allow or deny.
- **Resource**: The specific resource or group of resources in my AWS Account that this policy will apply to.

## 3. Create an AWS Account Alias

An account alias is a unique name for an AWS Account that can be used instead of the account ID to sign in to the AWS Management Console.

![Create AWS Account Alias 2](https://i.imgur.com/ZjYWfev.png)

Creating an account alias took me less than a minute.

Now, my new AWS console sign-in URL is: `https://app-alias-nadia.signin.aws.amazon.com/console`

## 4. Create IAM Users and User Groups

IAM users are logins/people who have access to my AWS Account, and these users are created by me using the AWS IAM service. I can designate my users' access to the AWS Account's resources/services.

![Create IAM Users and User Groups 1](https://i.imgur.com/76DJYxq.png)

IAM user groups are used for managing users' permissions at a macro level. They act similarly to folders when it comes to mass assigning permissions and policies.

![Create IAM Users and User Groups 2](https://i.imgur.com/OCHupc5.png)

![Create IAM Users and User Groups 3](https://i.imgur.com/QD4J2Jr.png)

I attached the policy I created to this user group, meaning all users added to this group will automatically inherit the group's access permissions.

Users can be invited to the account in two ways:
1. By sharing an email invitation with instructions.
2. By sending a `.csv` file containing login credentials.

![Create IAM Users and User Groups 4](https://i.imgur.com/Ef7GYvW.png)

## 5. Test User's Access

![Test User's Access 1](https://i.imgur.com/UUpr3h1.png)

Once I logged in as my IAM user, I noticed that the user did not have access to portions of the dashboard, which were labeled "Access Denied." This was due to the lack of permissions assigned to the user.

I tested my JSON IAM policy by attempting to stop the `Production-Permission` and `Development-Permission` instances.

- When I tried to stop the production instance, it displayed an error banner stating that I didn't have permission to stop the instance.

![Test User's Access 2](https://i.imgur.com/GNpg6Nt.png)

- Next, when I tried to stop the development instance, it successfully stopped the instance because it was allowed within the JSON policy.

  ![Test User's Access 3](https://i.imgur.com/1HDmVe6.png)

## Summary

This project demonstrated the effective management of AWS IAM by creating user groups and users, and by setting up precise policies to control access to EC2 instances based on environment tags. By implementing these strategies, I ensured that the organization's network is safeguarded through controlled permissions and streamlined resource management. The testing phase validated that the policies correctly enforce access restrictions, ensuring that users have appropriate permissions aligned with their roles.
