---
layout: post
title: AWS Lambda Functions with DynamoDB and APIGateway
date: '2017-09-28T11:31:00.003-10:00'
author: Christopher Slade
tags:
    - AWS Lambda
    - Technology
modified_time: '2017-09-28T11:31:54.772-10:00'
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-3256867729931253421
blogger_orig_url: https://www.christopherslade.com/2017/09/aws-lambda-functions-with-dynamodb-and.html
redirect_from: /2017/09/aws-lambda-functions-with-dynamodb-and.html
---


I had a hard time gathering all the information that I needed to be able to deploy a simple API to AWS. I didn't just want to create things in the AWS console because I cannot script it. Scripting allows me to redeploy my work with very little effort.

So, to automate deployment, I can see 2 options. One option is to create a Python script using the Boto3 library. The script would create the DynamoDBs, the lambda functions, and setup the API Gateway. The other options was using CloudFormation. CloudFormation allows organization to automate their deployment. However, CloudFormation is a lot of work and takes a lot of time to learn.

So, I was told about [handel](http://handel.readthedocs.io/). Handel runs on top of CloudFormation and simplifies the deployment setup.  All you need to do is setup an handel.yml file that will generate the CloudFormation template. Of course, since handel is less complex, you do lose some of the functionality of CloudFormation.

You can see all of the setup in this GitHub [repository](https://github.com/crslade/FirstDynamo)

It get it to work, I just installed node.js on my machine. Then install handel using npm (according to the handel docs). I also had to setup an account configuration file. The docs say it is hard to configure,  but you should be able to find all of the values you need in the console. You can find the account id in the IAM, and the VPC information in the VPC area. Just look in the sidebar for Your VPC's, and subnets. Once you click on them you should see ids (vpc-XXXX, subnet-XXXXXX). Add them into your config file. For the subnets add all of your subnets into the public, private and data subnets. You can find the ssh_bastion_sq in security groups. You don't need the last 2 lines.

After that I wrote the handel.yml file. This is where I described DynamoDB I wanted to create and connected it to an API Gateway. I described the API Gateway using a swagger.yml file. (I suggest YAML over JSON because it is easier to type.) The swagger file will contain all of your paths, and link each path up to a lambda function. You can also describe your API parameters and responses. Check out the swagger.yml file for an example.

Then you can deploy it by running the command handel -c <path to account config> -e dev -v 1.

If you notice, I added security to my API, so that I can limit who calls my API. Without security, anyone can call your API, (and rake up your bill). I went with simple API_KEYS. I didn't find a way for handel to set that up, so I had to do it in the AWS console. Under API gateway, on the sidebar you can find API_KEYS. Create a key. Then you have to create a usage plan. I limited API calls to 1/second while testing. I can't imagine me being able to send more that one request per second. Finally you have to add the plan onto your API stage. 

You will see that the swagger documents puts security on the API paths, with a security definition section below.

To test it, use curl:

    curl -H "x-api-key: generated-api-key" -d '{"device": "curl", "lat":"1.1", "lon":"2.2"}' https://eeohj10ccd.execute-api.us-west-2.amazonaws.com/dev/location

Another thing that took me some time was errors. I started to play with API Gateway integrations. However, since you have a lambda function, it can return what needs to be returned. Look in the python code for the error handling.
