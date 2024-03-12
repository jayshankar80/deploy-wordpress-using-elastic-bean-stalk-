# deploy-wordpress-using-elastic-bean-stalk

Project 1 →Deploy wordpress website on AWS using elastic beanstalk

**Prerequisites →**

---------
**Launch RDS database →**

 Please follow the below steps  

    1. step 1 →Search RDS on aws console and then click on create database
    2. step 2 → choose standard create and then mysql engine
    3. step 3 →set your master name and password you could also autogenerate the password
    4. step 4 → give the name to your database in the additional configuration and remain everything as it is and click on create database it takes up to 3 to 4 minutes to configure everything

![image](https://github.com/jayshankar80/deploy-wordpress-using-elastic-bean-stalk-/assets/78995149/8a5fd05a-9dd4-4a0a-bc29-bc5140369454)



**Launch elastic beanstalk environment →**

  Please follow the below steps 


  1. step 1 →Search Elastic beanstalk on aws console and then click on create application
  2. step 2 →choose web server environment and then give name to your application
  3. step 3 →choose php from managed platform and then click next
  4. step 4 → In service role click create and use new service role and select aws-elasticbeanstalk-service-role from it
  5. step 5 →choose your ec2 keypair and your ec2 instance profile to ec2accessdemoapp (tyou can follow this page to create instance profile https://www.iguazio.com/docs/latest-release/cluster-mgmt/deployment/cloud/aws/howto/iam-role-n-instance-profile-create/)
  6. step 6 → In VPC choose default vpc and then select your instance subnet and database subnets
  7. select the default security group from the options and click next
  8. step 8 → in health reporting choose basic and untick the manged updates options
  9. step 9 → Now connect your database by adding environment properties
           RDS_HOSTNAME :  where to find →On the Connectivity & security tab on the Amazon RDS console: Endpoint.
           RDS_PORT : where to find →On the Connectivity & security tab on the Amazon RDS console: Port.
           RDS_DB_NAME : where to find →On the Configuration tab on the Amazon RDS console: DB Name.
           RDS_USERNAME : where to find →On the Configuration tab on the Amazon RDS console: Master username.

![image](https://github.com/jayshankar80/deploy-wordpress-using-elastic-bean-stalk-/assets/78995149/194d09ef-f36b-4823-a65f-b58a3db1e559)


  10. Step 10 → review your configuration and click on sumbit

**Note**  : It takes around 5 min to create your application , click on url provided by elastic beanstalk you will find a page like this


**Download Wordpress →**
  1. step 1 → go to your local system  terminal and create dir mkdir git run
  2. Step2 -> git clone https://github.com/jayshankar80/deploy-wordpress-using-elastic-bean-stalk-/tree/main/wordpress
  3. Step 3 -> zip ../your_folder_name.zip -r * .[^.]*

**Upload and deploy →**
 → Go to your elastic beanstalk console choose the environment you created above and select upload and deploy option choose your wordpress file that you just downloaded and click on deploy

**Note :** It also takes around 5 min to deploy the application, after it successful deployment click on url but it shows 404 ngnix not found

**to overcome this error →**

1. step 1 → go to your ec2 dashboard and choose the instance created by elastic beanstalk
2. step 2 → copy the public ip and take ssh of that machine from your terminal by running
3. step 3 → run the following commands
   sudo su
   cd /var/www/html/
   mv wordpress/* / var/www/html/

4. now again click on url you will find a web page where you wordpress application running


**Congratulations!!**
