# Covalent GCP Serverless
This repository is a Covalent Serverless Application deployed on Google Cloud Platform. This wrapper will assist developers who want to utilize Covalent data without any server setup needed (serverless).

## GCP Service
[Cloud Functions](https://cloud.google.com/functions) - Service for create function to interact with [Covalent API](https://www.covalenthq.com/docs/api).

### Sample Service URL
[DEMO](https://us-central1-vibrant-mind-316215.cloudfunctions.net/covalent?path=/chains)

### How to setup
- Go to [Documentation](https://cloud.google.com/functions/docs/quickstart-nodejs)

- First of all, you need to [enable the APIs](https://console.cloud.google.com/flows/enableapi?apiid=cloudfunctions,cloudbuild.googleapis.com&redirect=https://cloud.google.com/functions/docs/quickstart-nodejs).

- To create a function, [open the Functions Overview page](https://console.cloud.google.com/functions/list)
  <br>
  Remark: Make sure that the project for which you enabled Cloud Functions is selected.

- Click `CREATE FUNCTION` Button

- Enter your Cloud Function configuration
  - In this example, we use `FUNCTION_NAME = covalent`
  - Select your region
  - Select Trigger type: `HTTP`
  - Select Authentication: `Allow unauthenticated invocations`
  - Click `SAVE` Button

- Setup Runtime environment variables
  - Open `RUNTIME, BUILD AND CONNECTIONS SETTINGS`
  - Select `RUNTIME` tab
  - Click `+ ADD VARIABLE`

    ```
    API_HOST = https://api.covalenthq.com/v1/
    API_KEY = {YOUR_COVALENT_API_KEY}
    ```

- Click `NEXT` Button

- Next, go to project directory

- Install dependencies
  ```
  npm install
  ```

- Next, zip all files and folders inside project directory

- Now come back to Google Cloud console, at Step 2: Code
  - Set `Entry point = handler`
  - Select Source code: `ZIP Upload`
  - Upload `.zip` file
  - Select Stage bucket

- Click `DEPLOY` Button

- After deploy project successfully, you will find `API endpoint` from `Trigger URL` inside your project at TRIGGER tab.

- How to use your API on Google Cloud Platform
  ```
  GET {API endpoint}?path={COVALENT_API_PATH}&param1=value1&param2=value2&...
  ```
