## Overview

The emailing portion of the webpage is utilizes the API and a lambda function. This piece is needed for the webpage to send an email over to Ed Happ via the information entered into the `Contact Us` page.

## Lambda

The lambda function that powers the `Contact Us` email can be found under the lambda functions service. The name of the function is `emailfwd` and is written in Python 3.6 for easy editing from one of our students if needed. Under the `designer` properties, you can see that this function has access to the s3 bucket, cloudwatch, API gateway, and the amazon Simple Email Service (SES).

This lambda function is built in a way that the only piece that would need adjusting from future team members would be the email on line 9 under the variable `SENDER`. **If this email were to change then it would need to be verified which I will go into greater detail down below.** The email body is written in basic HTML and can be adjusted as future team members and Ed see fit. Currently it sends the information that the user input into the webform as a bulleted list.

#### Walkthough of the Code

1) Sender and Reciever of the email are input through lines 9-29
2) SMTP keys are entered in. These are talked about in the next portion.
3) Lines 34-67 include the email body, subject, to, and from. These would be the lines that would need to be modified in the future.
4) Lines 68-83 include a basic try and except to email the information out. When testing the lambda function after modifications are made, this bit of code will let you know if the email either sent (Showing `Email Sent!`) or caught an error (showing `Error: <ERROR MESSAGE>`).

## Simple Email Services

The simple email service (SES) is used to generate SMTP keys which are input into the AWS lambda function and verify additional email addresses if they are needed for the project. In order to add new email addresses first navigate to SES in the aws console. After select `Email Addresses`. Here you can enter a new email address you would like to use which will then get sent a verification email needed in order for it to be used. Additional information can be found at https://docs.aws.amazon.com/ses/latest/DeveloperGuide/verify-email-addresses-procedure.html. 

## API Gateway

Navigate to the `API Gateway`. The API gateway allows informaiton to pass from the s3 bucket into the open web. 

The API I have created for the time being is under the `emailfwd-API`. If anything changes with the API Gateway being used for the AWS Lambda then it will need to be reset with in the Lambda function itself and routed through the new API/endpoint. The endpoint that is used for the email out function is `emailfwd`. The authorizationis through AWS_IAM which, under the lambda function, is authorized to send a POST through this endpoint.