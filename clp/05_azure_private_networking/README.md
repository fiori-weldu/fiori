# Azure Advance Networkign Learning Plan

| Topics                | Supplemental Materials                                       | Assignments                                                  |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Service Endpoints     | [YT Video](https://www.youtube.com/watch?v=q8s-zmHighs)      | -                                                            |
| Private Endpoints     | [YT Video](https://www.youtube.com/watch?v=lwLOGsZOV1w)      | [See Assignment](#1-service--private-endpoints)              |
| Private DNS Zones     | [See Supplemental Material](#1-private-dns-zones)            | [See Assignment](#2-private-dns-zones)                       |
| NAT Gateways          | [YT Video](https://youtu.be/AMr_IPk7wyk?si=ATlL73PjUbCy26-E) | [See Assignment](#3-nat-gateways)                            |
| Private Links         | [YT Video](https://www.youtube.com/watch?v=57ZwdztCx2w)      | -                                                            |
| P2S VPN Gateway       | [YT Video](https://www.youtube.com/watch?v=Z_YjuTt6CXw)      | [See Assignment](#4-p2s-vpn-gateways)                        |
| S2S VPN Gateway       | [YT Video](https://www.youtube.com/watch?v=i4Ph4n7v3WQ)      | -                                                            |
| Azure Load Balancer   | [YT Video](https://www.youtube.com/watch?v=wJvmXM81tEI)      | [See Assignment](#5-azure-load-balancers)                    |
| Azure App Gateway     | [YT Video](https://www.youtube.com/watch?v=DjNPHetdlQo)      | [See Assignment](#6-azure-application-gateway)               |
| Azure Traffic Manager | [YT Video](https://youtu.be/PfZPuBt50ps?si=W6x3ytYKFYSr8_ed) | [See Assignemnt](#7-azure-traffic-manager)                   |
| Azure Front Door      | [See Supplemental Material](#8-azure-front-door)             | [See Assignment](#8-azure-front-door-assignemnt)             |
| Azure APIM            | [See Supplemental Material](#9-azure-apim)                   | [See Assignment](#9-azure-api-management-service-assignemnt) |

## Supplemental Materials

### 1. Private DNS Zones
* [How DNS Works](https://www.youtube.com/watch?v=Ah7fYex6Ups)
* [DNS Records Explained](https://www.youtube.com/watch?v=HnUDtycXSNE)
* [Understanding DNS in Azure](https://www.youtube.com/watch?v=Hiohn35DIqA)
* [Mastering Azure Private DNS](https://www.youtube.com/watch?v=iz3MyO69YZU)

### 8. Azure Front Door
* [Microsoft Azure Front Door Deep Dive](https://youtu.be/DHiZbIks9i0?si=yUIeUp1dkIApMu96)
* [Azure Front Door FULL COURSE IN 2.5 HOURS](https://www.youtube.com/watch?v=gcnoH0CiWw0)

### 9. Azure APIM
* [Azure API Management Deep Dive](https://youtu.be/PXtFq5wmGt0?si=mo1SGdl8wKedVwqc)
* [The Ultimate Azure API Management Course](https://youtu.be/K-tYU8GOUt0?si=vjnF46oHoWPMaXrh)

## Assignments

### 1. Service & Private Endpoints
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Provision a PaaS resource (I recommend Azure KeyVault) that has networking settings to support IP whitelisting, service endpoints, and private endpoints. Allow public network access at first.
2. Provision a VM (cheapest one) in your custom VNet with a Public IP address.
3. Login to the VM, install Azure CLI on it, use Azure CLI to access some objects in your PaaS resource (password, file, data, etc). Access should be allowed.
4. Disable public network access to your PaaS resource. Try repeating the Step 3. Access should be rejected.
5. Add the public IP address to IP whitelist of your PaaS resource. Try repeating the Step 3. Access should be allowed. Remove the IP address from the whitelist.
6. Deploy a service endpoint to the subnet of your VM. Try repeating the Step 3. Access should be rejected, but the complaint should not be about the public IP address anymore.
7. Whitelist the above subnet in your PaaS resource. Try repeating the Step 3. Access should be allowed. Remove the subnet from the whitelist.
8. Create another subnet to your VNet. Deploy the private endpoint for your PaaS resource. Try repeating the Step 3. Access should be allowed.
9. Clean up the resources.

### 2. Private DNS Zones
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Provision Private DNS zone named <your_name>.org
2. Provision a Vnet with a single subnet.
3. Link your Private DNS zone to your VNet and enable VM auto-registration.
4. Provision two (cheapest) VMs into your subnet. One (VM1) with Public IP address, one without (VM2). Allow SSH/RDP for VM1.
5. Check the Recordsets in your Private DNS zone. Add an A record to map google.<your_name>.org FQDN to one of google.com pubic IPs (use dig/nslookup to find it).
6. Add a CNAME record to map facebook.<your_name>.org to facebook.com
7. SSH/RDP onto VM1. Jump over to VM2 using SSH/RDP and machine's private FQDN (not the IP address).
8. curl google.<your_name>.org, do you get some response from google.com?
9. curl facebook.<your_name>.org, do you get some response from facebook.com?
10. Clean up your Azure resources.

### 3. NAT Gateways
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Provision a VNet and Subnet. Provision two VMs into it. One with Public IP address, and one without.
2. Provision a PaaS resource that supports network access settings (Storage Account, KeyVault, Azure SQL DB, etc). Disable the public internet access to the resourse.
3. SSH/RDP onto the VM with public IP address. Use Azure CLI to attempt access to your PaaS resource.
4. From the first VM, SSH/RDP onto the VM without the public IP address. Use Azure CLI to attempt access to your PaaS resource.
5. Deploy a NAT gateway to the VMs subnet.
6. Whitelist the NAT gateway Outbound IP address in the PaaS resource network settings.
7. Repeat steps 3 and 4. Access should be allowed now.
8. Clean up the resources.

### 4. P2S VPN Gateways
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Provision a Vnet with single subnet.
2. Provision a (cheapest) VM with no Public IP address into your subnet. Don't open ports 22/3389 and 80.
3. Add a VPN Gateway subnet to your VNet.
4. Provision a VPN Gateway (VpnGw1 SKU) using the Gateway subnet in your VNet.
5. Generate root and client public and private certificates.
   * [Windows instructions](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-certificates-point-to-site)
   * [MacOS/Linux instructions](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-certificates-linux-openssl)
6. Configure a P2S VPN connection in your VPN gateway using the public root certificate. Use OpenSSL tunnel for Windows/Linux clients and/or IKEv2 tunnel for Windows/MacOS.
   * [End-to-end instructions](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-certificate-gateway)
7. Install and configure a VPN client on your machine.
   * [Windows Native VPN client](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-certificate-windows-native)
   * [Windows OpenVPN V3 client](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-certificate-windows-openvpn-client-version-3)
   * [MacOS Native VPN client](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-cert-mac)
   * [Linux OpenVPN client](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-certificate-openvpn-linux)
8. Connect to your VPN Gateway using your VPN client.
9. SSH/RDP to your VPN using its private IP address. Install a web-server (Nginx/Apache/IIS) on your VM.
10. Open your web-server main page from your laptop browser using its private IP address.
11. Clean up the resources.

### 5. Azure Load Balancers
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Prepare a VM image in an Image Gallery that automatically runs an API application when the VM starts.
   * Application should place some light CPU and memory load onto the VM and indicate which VM processed the request.
   * [Example Application](https://gitlab.com/BasiukTV/azure-sandbox/-/tree/main/apps/load_balancer/express_js/status_app)
2. Provision a (cheapest) VM using the above image in a VNet. At the time when you test the loadbalancer the VM should not have a public IP address.
3. Provision a VMSS that uses (cheapest) VMs to run the VM image above. Configure the CPU autoscaling for up to 3 VM instances. VM instances must not have public IP addresses.
4. Provision a Standard Public Load Balancer (LB).
   * Use a Public IP address for the frontend configuration.
   * Add both a singular VM and the VMSS to a single backed pool.
   * Configure the health probe to hit the health probe endpoint of your application.
   * Create the load balancing rule that routes the traffic from port 80 of the LB to the API port of your VMS.
   * Once the LB is provisioned navigate to VMSS instances and click on "Upgrade" button.
5. Use your browser to submit HTTP requests to port 80 of LB public IP address. Use multiple browsers, incognito windows, and time separated attempts to hit both the singular VM and a VMSS VM.
   * For some reason I had to occasionaly whitelist the application ports (ans the SSH/RDP ports) in the NSG rules, not sure why, but you might have to the same.
6. Configure Inbound NAT rules to be able to SSH/RDP to every machine in the backend pool.
7. Configure the Outbound rules to allow your backend pool VMs to talk to the public internet. curl google.com before and after to verify.
8. Run a application/script/JMeter to place enough load for long enough time on the load balancer to trigger the VMSS autoscaling. Track the max CPU usage metrics in Azure monitor to verify that the load is balanced evenly accross the machines.
   * [Example Load Testing Application](https://gitlab.com/BasiukTV/azure-sandbox/-/tree/main/apps/load_balancer/python/load_tester)
9.  Clean up the resources.

### 6. Azure Application Gateway
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Provision a VNet with at least two subnets, one of them being dedicated for the App Gateway.
2. Provision the infrastructure for and deploy two different application that expose public or private endpoints.
   * One application can be the status app from the previous assignment, another can be a dummy App Service Application.
3. Provision a Standard Application Gateway.
   * Use the dedicated subnet you provisioned before.
   * Use Public IP address for the App Gateways frontend.
   * Configure an HTTP Listener that listens on port 80.
   * Configure a Backend pool and backend configuration that can be used to reach your application.
      - Depending on the backend you mayb need to adjust the protocol, ports, path override, host override, etc.
   * Configure a URL path based rule that can route the traffic from the App Gateway to either application.
4. Open the public IP address of your App Gateway in you browser and use URL path based routing to route the trafic to both apps.
5. Enable WAF policy in the prevention mode for your App Gateway. Set a simple custom rule that would allow you to test the policy.
6. Demonstrate that your custom WAF policy rule works by blocking the traffic to the App Gateway.
7. Clean up the resources.

### 7. Azure Traffic Manager
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Have your application deployed in two different Azure regions using VMs, VMSS, AppService, etc.
   * Application HTTP response should be lightweight and should indicate which region is responding.
   * [Example Suitable Application](https://gitlab.com/BasiukTV/azure-sandbox/-/tree/main/apps/load_balancer/express_js/status_app)
2. Provision a Priority-based Traffic Manager profile, designate one regional endpoint of your application (primary) as priority 1 and another (secondary) as priority 2.
3. Demonstrate automatic disaster recovery failover performed by the Traffic Manager.
   * Generate ~10 minutes worth of load on the Traffic Manager endpoint. Consoder using this [Load Generator](https://gitlab.com/BasiukTV/azure-sandbox/-/tree/main/apps/load_balancer/python/load_tester)
   * Make sure all the traffic is going to the primary endpoint at first.
   * After ~2 minutes - make primary endpoint unresponsive (stop/descale VMs, adjust NSG rules, etc.), wait for the error responses starting to come in from the load generator.
   * After another ~2 minutes - notice how responses are again positive but coming from the secondary endpoint.
4. Provision a Performance-based Traffic Manager profile, add two endpoints from different regions.
5. Generate ~1 minute worth of load to the Traffic Manager profile from a VM close to the first endpoint, make sure only the first endpoint responds to the requests.
6. Generate ~1 minute worth of load to the Traffic Manager profile from a VM close to the second endpoint, make sure only the second endpoint responds to the requests.
7. Provision a Weight-based Traffic Manager profile, add prod endpoint with weight of 90, add canary endpoint with weight 10.
8. Generate ~2 minutes worth of load to the Traffic Manager profile. Notice that most of the traffic goes to the prod endpoint, and only some to the canary endpoint.
9. Clean up the resources.

### 8. Azure Front Door Assignemnt
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Have your application deployed in two different Azure regions using VMs, VMSS, AppService, etc.
   * Application HTTP response should be lightweight and should indicate which region is responding.
   * [Example Suitable Application](https://gitlab.com/BasiukTV/azure-sandbox/-/tree/main/apps/load_balancer/express_js/status_app)
2. Additionaly, deploy a multi-page static website into an Azure Storage Account.
   * See this instruction [Video](https://youtu.be/ttmEOLKk3Cw?si=vGg-pXUFQQOC3O8f)
3. Provison Standard Azure Front Door
   * Have 3 origin groups and 3 routing rules.
   * First origin and rule for the two endpoints of your application deployed in two different regions. Use latency sensitivity of 50ms or lower.
   * Second origin and rule are the same as above but with the cached response.
   * Third origin and rule is for the static website.
4. Demonstrate Front Door ability to route the trafic to the closest endpoint by calling the Front Door on the path corresponding to the first rule.
5. Demonstrate Front Door ability to return cached response much faster by calling the Front Door on the path corresponding to the cached rule.
6. Demonstrate your ability to reach your static website through the Front Door by calling the last path.
7. Implement the Rule Set that overwites the Front Doors routing desicion based on the URL parameter. Attach the rule set to the first rule and demonstrate it.
8. Clean up the resources.

### 9. Azure API Management Service Assignemnt
0. Capture the screenshots for the below milestones and submit an archive of them to me over Skype.
1. Have an API application deployed to a VM, VMSS, AppService, etc.
   * [Example Suitable Application](https://gitlab.com/BasiukTV/azure-sandbox/-/tree/main/apps/load_balancer/express_js/status_app)
2. Prepare an OpenAPI file defining the API exposed by your application (use ChatGPT to do this quickly).
3. Provision a Development tier APIM instance.
4. Create an APIM product.
5. Invite yourself using your personal email to the APIM product as a developer. Give yourself a subscription to the product.
6. Add an API to your product by using the prepared OpenAPI file. Edit the resulting API to make it work (most importantly replace the backend).
7. Publish the developer portal. Login into it with your personal email. Atempt to test the API from the portal. If that doesn't work due to CORS issues use the generated code snippets to test the API from your laptop.
8. Test using additional revisions of your API.
9. Test using additional versions of your API.
10. Test using various API policies:
   * Cache Lookup
   * Rate Limiting
     * Consider using this [Load Generator](https://gitlab.com/BasiukTV/azure-sandbox/-/tree/main/apps/load_balancer/python/load_tester) to trigger the rate limiting.
   * Mock Responses
11. Clean up the resources.
