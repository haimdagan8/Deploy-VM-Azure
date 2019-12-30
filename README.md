# Deploy VM Azure #

### Requirements ###

1. Ansible Installed.
2. Python-pip installed.
3. Azure python libraries installed ('pip install ansible[azure]')

### How to run ###

1. You need to setup your azure credentials in your OS, you can do it with several options :
1a. First option, set the following environment variables:
    AZURE_CLIENT_ID=<service_principal_client_id>
	AZURE_SECRET=<service_principal_password>
	AZURE_SUBSCRIPTION_ID=<azure_subscription_id>
	AZURE_TENANT=<azure_tenant_id>

1b. Second option ,configure azure-credentials.yml with your own credentials in the variables section and run it with this following command : 'ansible playbook azure-credentials.yml'

1c. Third option ,you can also do it with web UI login with this following command : 'az login'

2. After the credentials configured ,you can configure the Deploy.yml with your own requirements and after that you can run it and deploy your vm on azure with the following command : 'ansible playbook Deploy.yml'

3. Enjoy and start building :)

### Description ###
# azure-credentials.yml #
I have used the copy module in order to create the credentials file with text content and it will also create the credentials file if it is not exists. This is one of the ways to setup the credentials for the Ansible automation to be working because it needs the credentials to perform actions and to know where to do them.

# Deploy.yml #
I have created resource group because every resource needs to be attached to resource group and after this creation ,I created the virtual network and the subnet for the resource group.
After the resource group configurations ,I created the VM configurations which includes Pubilc IP, Network security group which will have the rules for the ports that will be allowed for traffic (In this senario ,I allowed port 22 to be accessed.) ,Virtual network interface card which will be a network adapter to the virtual network of the resource group in which it will intaract with the other resources within the resource group and for the internet gateway ,and finally creating the VM which is configured as Ubuntu 18.04 LTS with size of the VM ,administrator username and password which I configured and network interfaces ,and after that the VM will be created.