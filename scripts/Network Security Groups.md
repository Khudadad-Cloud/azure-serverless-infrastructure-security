
#!/bin/bash

# Variables
RESOURCE_GROUP="rg-functionapp-project"
LOCATION="canadacentral"

VNET_NAME="vnet-functionapp"

APP_SUBNET="app-subnet"
STORAGE_SUBNET="storage-subnet"

APP_NSG="nsg-functionapp"
STORAGE_NSG="nsg-storage"

# Create Application NSG
echo "Creating Application Network Security Group..."

az network nsg create \
    --resource-group "$RESOURCE_GROUP" \
    --name "$APP_NSG" \
    --location "$LOCATION"

# Create Storage NSG
echo "Creating Storage Network Security Group..."

az network nsg create \
    --resource-group "$RESOURCE_GROUP" \
    --name "$STORAGE_NSG" \
    --location "$LOCATION"

# Add an inbound rule to allow HTTPS traffic
echo "Adding HTTPS inbound rule to Application NSG..."

az network nsg rule create \
    --resource-group "$RESOURCE_GROUP" \
    --nsg-name "$APP_NSG" \
    --name "Allow-HTTPS-Inbound" \
    --priority 100 \
    --direction Inbound \
    --access Allow \
    --protocol Tcp \
    --source-address-prefixes Internet \
    --source-port-ranges "*" \
    --destination-address-prefixes "*" \
    --destination-port-ranges 443

# Add a rule to deny inbound HTTP traffic
echo "Adding HTTP deny rule to Application NSG..."

az network nsg rule create \
    --resource-group "$RESOURCE_GROUP" \
    --nsg-name "$APP_NSG" \
    --name "Deny-HTTP-Inbound" \
    --priority 110 \
    --direction Inbound \
    --access Deny \
    --protocol Tcp \
    --source-address-prefixes Internet \
    --source-port-ranges "*" \
    --destination-address-prefixes "*" \
    --destination-port-ranges 80

# Associate Application NSG with Application Subnet
echo "Associating Application NSG with Application Subnet..."

az network vnet subnet update \
    --resource-group "$RESOURCE_GROUP" \
    --vnet-name "$VNET_NAME" \
    --name "$APP_SUBNET" \
    --network-security-group "$APP_NSG"

# Associate Storage NSG with Storage Subnet
echo "Associating Storage NSG with Storage Subnet..."

az network vnet subnet update \
    --resource-group "$RESOURCE_GROUP" \
    --vnet-name "$VNET_NAME" \
    --name "$STORAGE_SUBNET" \
    --network-security-group "$STORAGE_NSG"
