---

copyright:

  years: 2015，2019

lastupdated: "2019-03-27"

keywords: federated ID, enterprise SSO, single sign-on ID, API key login, one-time passcode login

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Logging in with a federated ID
{: #federated_id}

As a federated user that uses a corporate or enterprise single sign-on ID, you can log in to {{site.data.keyword.Bluemix}} from the command-line interface (CLI) by using either a one-time passcode or an API key.
{: shortdesc}

## Using a one-time passcode
{: #onetime_passcode}

When you use the one-time passcode option to log in with a federated ID, you specify the single-sign on (SSO) parameter to get a one-time passcode, which you then enter at login.

Because a one-time passcode retrieves code from the {{site.data.keyword.Bluemix_notm}} console, it causes the use of a federated ID in your automation script to fail. Avoid trouble by using the API key option with an automated script.
{: tip}

### From the {{site.data.keyword.Bluemix_notm}} CLI
{: #login_cli}
1. Specify the `--sso` option with the `ibmcloud login` command.
2. Follow the URL in the prompt to get the one-time passcode.
3. Copy and paste the passcode value in the CLI as your input.

  ```
  ibmcloud login --sso
  API endpoint: https://cloud.ibm.com

  Get One Time Code from https://identity-2.us-south.iam.cloud.ibm.com/identity/passcode to proceed.
  Open the URL in the default browser? [Y/n]>
  One Time Code >
  Authenticating...
  OK

  ```

### From the Cloud Foundry CLI
{: #login_cf_cli}

1. Specify the `--sso` option with the `cf login` command.
2. Follow the URL in the prompt to get the one-time passcode.
3. Copy and paste the passcode value in the CLI as your input.

  ```
  cf login -a  https://api.us-south.cf.cloud.ibm.com --sso

  API endpoint: https://api.us-south.cf.cloud.ibm.com

  One Time Code (Get one at https://login.us-south.cf.cloud.ibm.com/UAALoginServerWAR/passcode)>
  Authenticating...
  OK

  ```

## Using an API key
{: #api_key}

The required API key is the {{site.data.keyword.Bluemix_notm}} API key that's used to authenticate with the {{site.data.keyword.Bluemix_notm}} platform, not the classic infrastructure API key or {{site.data.keyword.Bluemix_notm}} service API key.

1. Create an API key with the [`ibmcloud iam api-key-create` command](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_iam#ibmcloud_iam_api_key_create). Use the `-f` option to generate an API key file instead of showing the key in the command window:

   ```
   ibmcloud iam api-key-create NAME [-d DESCRIPTION] [-f, --file FILE]

   ```

2. Log in with the API key.

  You can use the API key with the {{site.data.keyword.Bluemix_notm}} CLI in any of the following ways:

    * Call the API key directly:

      ```
      ibmcloud login --apikey <api_key_string>

      ```

    * Call the API key with the key file:

      ```
      ibmcloud login --apikey @key_file_name

      ```

    * Set an environment variable. Additionally, you can also set an environment variable on your system. For example, IBMCLOUD_API_KEY=api_key_string, where `api_key_string` is the custom value of the API key. After the environment variable is set, you can simply specify `ibmcloud login` from the CLI.

   For Windows 10 PowerShell, you want to use `'@key_file_name'` with single quotes around the key file name.
   {: tip}

  To log in by using the Cloud Foundry CLI, specify `apikey` as the user name and the API key string as the password:

    ```
    cf login -a https://api.us-south.cf.cloud.ibm.com

    API endpoint: https://api.us-south.cf.cloud.ibm.com

    Email> apikey

    Password>
    Authenticating...
    OK

    ```
