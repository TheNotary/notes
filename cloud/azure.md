# Azure

###### Getting credentials setup

https://www.terraform.io/docs/providers/azurerm/authenticating_via_service_principal.html

###### You need to populate these env values:
```
export CLIENT_ID=""
export CLIENT_SECRET=""
export TENANT_ID=""
export SUBSCRIPTION_ID=""
```

To get the first two values, run these commands:
```
az login  # this step takes you to a browser to login

# Get SUBSCRIPTION_ID
az account list | grep '"id":'

# Get TENANT_ID
az account list | grep '"tenantId":'
```


Then you'll need to create a Service Principal:
```
$  az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/${SUBSCRIPTION_ID}"
{
  "appId": "00000000-0000-0000-0000-000000000000",
  "displayName": "azure-cli-2018-03-12-14-18-11",
  "name": "http://azure-cli-2018-03-12-14-18-11",
  "password": "00000000-0000-0000-0000-000000000000",
  "tenant": "00000000-0000-0000-0000-000000000000"
}
```

Set the `password` field to be `CLIENT_SECRET` and `appId` to be `CLIENT_ID`.

```
az storage blob upload --container-name my-storage --name blobName --file ./azure.md
```


###### Test your Account
```
az login --service-principal -u $CLIENT_ID -p $CLIENT_SECRET --tenant $TENANT_ID
```



# Working with their Storage on CLI

https://docs.microsoft.com/en-us/azure/storage/common/storage-azure-cli

```
container_name=my-storage
az storage blob upload --container-name my-storage --name blobName --file ./azure.md --account-name $CLIENT_ID --account-key $CLIENT_SECRET
az storage blob list --container-name $container_name --output table --account-name $CLIENT_ID --account-key $CLIENT_SECRET
```

