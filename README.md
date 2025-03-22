#!/bin/bash

# Update package list and install dependencies
sudo apt update && sudo apt install -y apt-transport-https ca-certificates gnupg curl

# Add Google Cloud SDK key
curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg

# Add Google Cloud SDK repository
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | sudo tee /etc/apt/sources.list.d/google-cloud-sdk.list

# Update package list again
sudo apt update

# Install Google Cloud CLI
sudo apt install -y google-cloud-cli

# Verify installation
gcloud --version
