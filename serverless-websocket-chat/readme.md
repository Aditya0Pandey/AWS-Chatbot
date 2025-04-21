# 🛰️ AWS Serverless Real-Time Chat Application

A fully serverless, real-time chat application built using AWS services like **API Gateway (WebSocket API)**, **AWS Lambda**, and **Amazon DynamoDB**. The project is deployed and managed using **AWS SAM (Serverless Application Model)** and CloudFormation.

## 🔧 Technologies Used

- **Amazon API Gateway (WebSocket API)** – Manages real-time bidirectional communication.
- **AWS Lambda (Python)** – Handles backend logic for connect, disconnect, and messaging.
- **Amazon DynamoDB** – Stores connection IDs of active users.
- **AWS CloudFormation / SAM CLI** – Infrastructure as Code for easy deployment.

## ⚙️ How It Works

1. **User Connects:**  
   - API Gateway triggers the `$connect` route.
   - `OnConnectFunction` stores the connection ID in DynamoDB.

2. **User Sends a Message:**  
   - API Gateway triggers the `$default` route.
   - `OnDefaultFunction` reads the message and broadcasts it to all connected clients using their stored connection IDs.

3. **User Disconnects:**  
   - API Gateway triggers the `$disconnect` route.
   - `OnDisConnectFunction` removes the connection ID from DynamoDB.


## 🚀 Deployment Instructions (Using SAM CLI)

1. **Install AWS SAM CLI**  
   https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html

2. **Install Python 3.8 (if not already installed)**  
   Required for Lambda runtime.

3. **Build the project:**

   ```bash
   sam build

Deploy the app:

sam deploy --guided
