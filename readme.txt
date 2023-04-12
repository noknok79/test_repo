The procedure below should take effect without error. Your system must be running on a Powershell or Linux environment. The terraform application and Azure CLI must already be installed before being able to do the terraform deployment procedure to run.
 
  
The proceedure came from this link
https://learn.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-terraform


do the following...

terraform init
terraform plan -out main.tfplan
terraform apply main.tfplan


terraform output -raw tls_private_key > id_rsa
terraform output public_ip_address
ssh -i id_rsa azureuser@<public_ip_address>


If you encountered error regarding the permission try the below command
chmod 600 id_rsa

Pre-requisites:

set the your chosen tenant and subscription

to set specific tennant
az login --tenant <myTenantID>

to set specific subscription to use
az account set --subscription <subscription_id>

if you are finish and you want to delete/destroy the created resources
terraform plan -destroy -out main.destroy.tfplan



#Modify 12-13-2022
#updated .gitignore include destroy.tfplan 
Mark Villanueva
