# Write-up

### Analyze, choose, and justify the appropriate resource option for deploying the app.

I have chosen to deploy the article CMS application via an Azure App Service, as it provides a lightweight approach to publish and update new versions of the app. It is well integrated in the Git workflow and provides several advantages regarding costs, scalalability and availability (see the followng section for the comparsion with virtual machines).

#### Azure App Service

* **Costs**: A standard tier Linux app service running in the Germany West Central region costs about 64€ per month.

* **Scalability**: App services can scale vertically and horizontally within their app service plan. Up and downscaling of app services as well as load balancing between multiple instances is done automatically.

* **Availability**: With multiple VMs per app service and a mechanism called "Deployment Slots", updating the application or restarting individual OS versions of the VMs does not lead to a downtime.

* **Workflow**: The automatic deployment mechanisms enable a continuous integration and deployment approach. There is no need to manually fiddle wih SSH connections and low-level web server configurations.

#### Azure Virtual Machine

* **Costs**: A standard tier Linux virtual machine running in the Germany West Central region costs about 77€ per month.

* **Scalability**: To achieve vertical scaling, one can upgrade to a more powerful virtual machine. However, this is a manual process and requires to redeploy the application. Horizontal scaling is not supported out of the box.

* **Availability**: As the virtual machine needs to restart from time to time (e.g., for updates of the operating system), there occur some downtimes of the application.

* **Workflow**: The process of connecting to a virtual machine and to manually deploy new application releases is cumbersome and prone to errors.

### Assess app changes that would change your decision.

One possible changed requirement could be the required resource consumption. In case the number of users exceeds a certain threshold, Azure App Service plans cannot provide enough compute and memory resources anymore, to cover the according load. In this case I would check alternative deployment models like using Azure Virtual Machines or other services provided by Azure.
