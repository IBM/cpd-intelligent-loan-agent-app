# Run locally

This document shows how to run the `intelligent-loan-agent` application on your local machine.

## Steps

1. [Clone the repo](#1-clone-the-repo)
1. [Configure `.env` with credentials](#2-configure-env-with-credentials)
1. [Run the application](#3-run-the-application)

## 1. Clone the repo

Use the following command to clone the ntelligent-loan-agent GitHub repository.

```bash
git clone https://github.com/IBM/cpd-intelligent-loan-agent-app
```

## 2. Configure `.env` with credentials

Once the workspace is uploaded, it is now time to let our application run locally and to do that we'll configure a simple text file with the environment variables we want to use. We begin by copying the [`env.sample`](https://github.com/IBM/cpd-intelligent-loan-agent-assets/blob/master/env.sample) file and naming it `.env`.

```bash
cp env.sample .env
```

First, edit the .env file and set the key-value pairs with values as shown below : 

* `AUTH_URL` -  enter auth url of Cloud Pak for Data instance under which the prediction model is deployed.
* `MODEL_URL` - paste in the URL to the machine learning model deployed using Watson Machine Learning. 
* `AUTH_USERNAME` - enter username to Cloud Pak for Data instance under which the prediction model is deployed.
* `AUTH_PASSWORD` -  enter the password to Cloud Pak for Data instance under which 
* `HOST` - enter *0.0.0.0*
* `PORT` - enter *5000*

### Example .env file

```bash
# Copy this file to .env.
# Edit the .env file with the required settings before starting the app.

# 1. Required: Provide your web service URL for scoring.
# E.g., MODEL_URL=https://<cluster_url>/v4/deployments/<deployment_space_guid>/predictions
MODEL_URL=https://zen1-cpd-zen1.aida-cpd3-dal10-b3c32x128-f2c6cdc6801be85fd188b09d006f13e3-0001.us-south.containers.appdomain.cloud/v4/deployments/578292c6-baae-4582-bf35-6e22491abcde/predictions


# 2. Required: fill in EITHER section A OR B below:

# ### A: Authentication using username and password
#   Fill in the authentication url, your Cloud Pak for Data username and  password.
#   Example:
#     AUTH_URL=<cluster_url>/v1/preauth/validateAuth
#     AUTH_USERNAME=my_username
#     AUTH_PASSWORD=super_complex_password
AUTH_URL=https://zen1-cpd-zen1.aida-cpd3-dal10-b3c32x128-f2c6cdc6801be85fd188b09d00abcde-0001.us-south.containers.appdomain.cloud/v1/preauth/validateAuth
AUTH_USERNAME=*****
AUTH_PASSWORD=******

# ### B: (advanced) Provide your bearer token.
#   Uncomment the "AUTH_TOKEN=" below and fill in your Bearer Token.
#   You can generate this token by following the lab instructions. This token should start with "Bearer ".
#   Note: that hese tokens will expire after a few hours so you'll need to generate a new one again later.
#   Example:
#       TOKEN=Bearer abCdwFghIjKLMnO1PqRsTuV2wWX3YzaBCDE4.fgH1r2... (and so on, tokens are long).
# AUTH_TOKEN=


# Optional: You can override the server's host and port here.
HOST=0.0.0.0
PORT=5000

```

## 3. Run the application

* The server requires Python 3.5 and above. It has been tested with Python 3.7.4.

* The general recommendation for Python development is to use a virtual environment ([venv](https://docs.python.org/3/tutorial/venv.html)). To install and initialize a virtual environment, use the `venv` module on Python 3:

Create the virtual environment using Python. Use one of the two commands depending on your Python version.
> Note: `python` may be named `python3` on your system.

```bash
python -m venv mytestenv
```

Now source the virtual environment. Use one of the two commands depending on your OS.

```bash
source mytestenv/bin/activate  # Mac or Linux
./mytestenv/Scripts/activate   # Windows PowerShell
```

> **TIP** :bulb: To terminate the virtual environment use the `deactivate` command.

1. Start the app by running:

```bash
pip install -r requirements.txt
python app.py
```

1. Launch a browser and navigate to [http://localhost:5000](http://localhost:5000)
1. Go back to the README to see an example of using the *Intelligent Loan Agent* web app.

[![return](https://raw.githubusercontent.com/IBM/pattern-utils/master/deploy-buttons/return.png)](../../README.md#sample-loan-submission)
