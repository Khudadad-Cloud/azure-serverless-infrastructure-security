#!/bin/bash

# Create Azure Key Vault
echo "Creating Azure Key Vault..."

az keyvault create \
    --resource-group "$RESOURCE_GROUP" \
    --name "$KEYVAULT_NAME" \
    --location "$LOCATION" \
    --enable-rbac-authorization true \
    --enable-soft-delete true \
    --enable-purge-protection true
