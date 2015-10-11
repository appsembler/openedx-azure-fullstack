# Open edX Fullstack on Azure

This is an Azure template to create an Ubuntu VM and provision the Open edX fullstack. Open edX fullstack is a single server configuration of all applications 

You can learn more about Open edX and fullstack here:
- https://open.edx.org
- https://github.com/edx/edx-platform

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftkeemon%2Fopenedx-azure-fullstack%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

This template will complete quickly, but the full Open edX install usually takes > 1 hour. To follow along with the progress, ssh into the VM and `tail -f /var/log/azure/openedx-fullstack-install.log`

# Getting started with Open edX fullstack
After the install has successfully completed, Supervisor will automatically start LMS (the student facing site) on port 80 and Studio (the course authoing site) on port 18010. Both ports have already been made accessible, so you can simply visit them by opening a browser and navigating to:
 - LMS: http://YOUR_INSTANCES_DNS_NAME.cloudapp.azure.com 
 - Studio: http://YOUR_INSTANCES_DNS_NAME.cloudapp.azure.com:18010

# Customizing Open edX fullstack
Many Open edX features can be configured by creating and/or editing the file in `/edx/app/edx_ansible/server-vars.yml`. 

After you have added your customizations, save your file, then run:
```
/edx/bin/update edx-platform YOUR_EDX_PLATFORMS_BRANCH_NAME
```

A sample server-vars.yml file has been added to this repo to change the site's title to: "Open edX on Azure."

# Customizing Open edX's design
A method for changing the design of Open edX without forking the entire edx-platform repo has been developed by Stanford. You can read more about [configuring an Open edX theme](https://github.com/edx/edx-platform/wiki/Stanford-Theming) and can find the [edx-theme repo](https://github.com/Stanford-Online/edx-theme). 

For more info, check the [Open edX Github Wiki on managing fullstack](https://github.com/edx/configuration/wiki/edX-Managing-the-Full-Stack)