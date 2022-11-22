# Overview

TL;DR
A simple Python GCP Cloud Function that pulls stock data from https://alpaca.markets and publishes results to Google Cloud Pubsub.

This project was built to demonstrate a straigh forward and low cost option for ingesting application data for analyics.

An example Alpaca API response is shown below. The cloud function selects the attributes and writes to a predefined PubSub topic.

```json
{
  "symbol": "GOOG",
  "trade": {
    "t": "2022-11-22T19:52:11.744989347Z",
    "x": "V",
    "p": 97.18,
    "s": 300,
    "c": ["@"],
    "i": 3171,
    "z": "C"
  }
}
```

# Setup

This project includes a yaml file for deployment to Google Cloud using Github Actions maintained here: https://github.com/google-github-actions/deploy-cloud-functions. The Github Action Workflow requires several _"Action Secrets"_ used to set environment variables during deployment. Set the following secrets in the repository before deployment.

| Action Secret  | Value                                                          |
| -------------- | -------------------------------------------------------------- |
| KEY_ID         | Alpaca API Key ID Issued _(authenticate to data source)_       |
| SECRET_KEY     | Alpaca API Secret Key ID                                       |
| PROJECT_ID     | GCP Project ID where Topic is deployed                         |
| TOPIC_ID       | GCP PubSub Topic                                               |
| GCP_PROJECT_ID | GCP Project ID where Function will be deployed                 |
| GCP_SA_KEY     | Service Account Key used to authenticate GitHub to GCP Project |
