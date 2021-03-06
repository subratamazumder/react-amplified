![GitHub](https://img.shields.io/github/license/subratamazumder/react-amplified?style=for-the-badge)
## React App Using AWS Amplify

POC to understand how to work with AWS Managed GraphQL service i.e., [AWS AppSync](https://aws.amazon.com/appsync/)

This project has been bootstrapped with [Create React App](https://github.com/facebook/create-react-app) and [AWS Amplify](https://aws.amazon.com/amplify/)

Detail instruction can be found here on [AWS Amplify Docs](https://docs.amplify.aws/start/getting-started/setup/q/integration/react)

## Output of Key Setup Steps
### Add API
![AddTodo](doc/cli-add-api.png)
### Add Auth
![AddTodo](doc/cli-add-auth.png)
### Add Hosting
![AddTodo](doc/cli-add-hosting.png)
## Demo
### Test GraphQL Todo API
```console
curl -i -X POST -H "Content-Type: application/json" \
-H "x-api-key: ******<replace-with-urs>******" \
    -d '{
	"query": "query listTodos { listTodos {   items {     id    description   name }  }}",
	"variables": null,
	"operationName": "listTodos"
}' \
    https://****<replace-with-urs>****.appsync-api.us-east-1.amazonaws.com/graphql
```

```console
HTTP/2 200
content-type: application/json;charset=UTF-8
content-length: 385
date: Sun, 20 Sep 2020 12:59:55 GMT
x-amzn-requestid: a04ba281-f73c-4cef-ba99-14de24a50e01
x-amzn-trace-id: Root=1-5f67524a-9ef51196a9bdbebaebedf99a
x-cache: Miss from cloudfront
via: 1.1 15397caaa3c9e02a2f3a5395f6725740.cloudfront.net (CloudFront)
x-amz-cf-pop: BLR50-C3
x-amz-cf-id: jH5FRFQhMuh6g-OnV0dc35uW4aJow0nRj_YrQ01VmY8lbknjfnwgmA==

{
	"data": {
		"listTodos": {
			"items": [{
				"id": "5067cb64-0308-4b8c-b845-f349f45a497d",
				"description": "It's time to go to bed",
				"name": "Sleep Now"
			}, {
				"id": "373db66d-f9e4-4a5b-8673-efce9e2c21a8",
				"description": "Cognito needs to be configured",
				"name": "Add Auth module"
			}, {
				"id": "692c3f04-0428-4712-b9b7-7e1899224765",
				"description": "Build a serverless API with Amplify and GraphQL",
				"name": "Learn AWS"
			}]
		}
	}
}
```
### Run Demo
#### In Local (without auth)
- `npm start` (to test with local mock `amplify mock api` first )


##### Add a new ToDo

![AddTodo](doc/add-todo.png)

##### View All ToDo(s)

![ViewTodo](doc/view-todo.png)

##### GraphQL ToDo API

![GraphQLAPI](doc/graphql-api.png)

##### DynampDB ToDo Table

![DynamoDB](doc/dynamo-table.png)

### Via S3 Website
- `amplify add auth` (ignore if alredy done)
- `amplify add hosting` (ignore if alredy done)
- `amplify publish`
- `npm install -g serve && serve -s build` (to test local with build version) 

##### Sign In Page

![AddTodo](doc/sign-in-empty.png)

##### Create New Account Page

![AddTodo](doc/create-new-account.png)

##### Verification code to complete registration

![AddTodo](doc/verification-code.png)

##### New User Created in Cognito

![AddTodo](doc/cognito-pool.png)

##### Sign with new user

![AddTodo](doc/sign-in.png)

##### Secure Home Page

![AddTodo](doc/secure-home-page.png)

## Issues faced

After adding hosting by `amplify add hosting` when `amplify publish` was run below error occured
```
npm WARN build `npm build` called with no arguments. Did you mean to `npm run-script build`?
frontend build command exited with code 0
Publish started for S3AndCloudFront

Cannot find the distribution folder.
Distribution folder is currently set as:
  /Users/subratamazumder/workspace/react-amplified/build

Cannot find the distribution folder.
Error: Cannot find the distribution folder.
    at Object.scan (/usr/local/lib/node_modules/@aws-amplify/cli/node_modules/amplify-category-hosting/lib/S3AndCloudFront/helpers/file-scanner.js:38:11)
```

This seems to be a bug, fix is to run `npm run build` to create missing `build` directory.
I have raise this as a [bug](https://github.com/aws-amplify/amplify-cli/issues/5363). 
## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
