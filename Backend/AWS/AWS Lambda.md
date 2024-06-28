#### Lambda function
Run code without having to think about setting up servers.

An AWS Lambda function is a small, discrete unit of code that performs a specific task, executed in response to an event. It is part of AWS's serverless computing platform, which allows you to run code without provisioning or managing servers.


Note:
	In order to go setup your AWS lambda function, first `login to AWS` and then click on `services` and select `Lambda` which is under the `Compute` tab.



#### Handler
The handler is the entry point for a Lambda function. It is a specific method in your code that AWS Lambda calls to start execution.

The handler processes the input event, performs the necessary computations or logic, and returns a response or calls a callback function.
```js
export const handler = async (event, context, callback) => { 
	console.log("hello from aws labmda function"); 
};
```
##### event
The event object contains data that triggered the Lambda function. This can be input data from an AWS service (e.g., an S3 bucket event, DynamoDB stream record, API Gateway request) or custom event data passed by the invoker.

##### context
The context object provides information about the execution environment of the Lambda function, such as the function name, memory limit, log group, and request ID.

##### callback
The callback function is used to return a response back to the caller, or to signal the completion of the function execution. This is primarily used in Node.js runtime.