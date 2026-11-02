#!/bin/bash

# Variables
RESOURCE_GROUP="rg-functionapp-project"
LOCATION="canadacentral"
VNET_NAME="vnet-functionapp"
ADDRESS_PREFIX="10.0.0.0/16"

APP_SUBNET="app-subnet"
APP_PREFIX="10.0.1.0/24"

STORAGE_SUBNET="storage-subnet"
STORAGE_PREFIX="10.0.3.0/24"

# Create Virtual Network and Application Subnet
echo "Creating Azure Virtual Network..."

az network vnet create \
    --resource-group "$RESOURCE_GROUP" \
    --name "$VNET_NAME" \
    --location "$LOCATION" \
    --address-prefixes "$ADDRESS_PREFIX" \
    --subnet-name "$APP_SUBNET" \
    --subnet-prefixes "$APP_PREFIX"

# Create Storage Subnet
echo "Creating Storage Subnet..."

az network vnet subnet create \
    --resource-group "$RESOURCE_GROUP" \
    --vnet-name "$VNET_NAME" \
    --name "$STORAGE_SUBNET" \
    --address-prefixes "$STORAGE_PREFIX"
    
