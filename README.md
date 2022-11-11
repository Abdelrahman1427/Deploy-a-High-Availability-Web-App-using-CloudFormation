# Deploy-a-High-Availability-Web-App-using-CloudFormation

This project is for deploying a high availability web app using cloud formation

our output was a link for WebAppLBDNSName :

    http://my-se-webap-17t362b9ap3td-1910689758.us-east-1.elb.amazonaws.com/

1- Delete all stacks if there any

2- supporting material 

    git clone https://github.com/udacity/nd9991-c2-Infrastructure-as-Code-v1.git

3- vscode

    code nd9991-c2-Infrastructure-as-Code-v1/supporting_material

4- open servers.yml
    Remove line 59, 60
    Change ImageId in line 60 to be ami-0729e439b6769d6ab
    Change FromPort and ToPort in lines 36, 37 to 80
    Change WebAppTargetGroup Port in line 118  to 80
    Replace the UserData from line 53 to 56 with the following snippet
    
          #!/bin/bash
          apt-get update -y
          apt-get install apache2 -y
          systemctl start apache2.service
          cd /var/www/html
          echo "Udacity Demo Web Server Up and Running!" > index.html
          
5-

    ./create.sh my-network network.yml network-parameters.json
 
6- 

    ./create.sh my-servers servers.yml server-parameters.json

7- LoadBalancer DNS Name : CloudFormation -> servers stack -> output -> WebAppLBDNSName http://my-se-webap-17t362b9ap3td-1910689758.us-east-1.elb.amazonaws.com/


   Diagram:
   ![00-diagram](https://user-images.githubusercontent.com/95107008/201354328-7d6bd131-0bb4-4f55-ba01-c984e3c3946f.png)
   Network resources:![01](https://user-images.githubusercontent.com/95107008/201355435-a6914e84-2e1b-4a4d-b39a-5d72ce1b2d48.png)

   Network output:![02](https://user-images.githubusercontent.com/95107008/201355502-8de2706f-3ea7-4682-995d-85cbfecb9d96.png)

   Servers resources:![03](https://user-images.githubusercontent.com/95107008/201355524-f3bdeb4a-8787-450d-945f-cf2c303a5abb.png)

   WebAppLBDNSName: ![04](https://user-images.githubusercontent.com/95107008/201355543-ea817189-5383-4a15-ae1f-9c230a53f783.png)

   Output of high availability wep app application:![05](https://user-images.githubusercontent.com/95107008/201355564-1590a64b-388e-48c0-bbbb-ca50df0814ce.png)

