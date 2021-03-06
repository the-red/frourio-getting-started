# GitHub Actions Secrets
Add following secrets.

* API_ORIGIN: API origin. e.g. `https://api.my-frourio-app.example`
* API_BASE_PATH: API basepath. e.g. `/api`
* Optional GH_PAGES_BASE_PATH: Client hosting basepath.
  * If omitted, GitHub repository name will be used. This is because GitHub hosts Pages at github-username.github.io/repository-name with default settings.
  * You can also use custom domain. When doing so, it is needed to use that basename. Set this `/` to host your client from root routing.

# Deploy to AWS Lambda
At least, you should prepare following for deploying to AWS Lambda.

* Lambda function to respond to user requests.
  * Set this Lambda's name to GitHub Actions Secrets LAMBDA_FUNCTION_NAME_SERVER
* Lambda function to run migrations.
  * Set this Lambda's name to GitHub Actions Secrets LAMBDA_FUNCTION_NAME_MIGRATION
  * NOTE: Recommended to set longer time limit.
* Amazon S3 to upload deployment artifacts like built bundle scripts and node_modules.
  * Set this S3's bucket name to GitHub Actions Secrets S3_BUCKET
  * Optional: To specify the S3 key prefix, also add S3_PREFIX to secrets. e.g. ``eployments/`
  * To elaborate, the key `${S3_BUCKET}/${S3_PREFIX}deployment_server.zip` is used to store the data.
