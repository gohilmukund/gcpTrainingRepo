# Compute Engine and deployment Manager
***

## TASK 2

#### Activity: Highly available and scalable application

##### Sub Activity: Add high availabilty and scalabilty to the existing app deployed in compute engine
---

1. Create Subnet :
    ![alt text][Subnet]


2. Create VPC-Network as below:
    ![alt text][VPCNetwork]
    Details:
    ![alt text][VPCNetworkDetails]

3. Create Firewall to block other IP ports and open only port 80:
    ![alt text][Firewall]

4. Copied the startup app from github repo to personal github repo, made changes Like below:
    ```shell
    sudo apt update && sudo apt -y install git gunicorn3 python3-pip
    git clone https://github.com/gohilmukund/gcpTrainingRepo.git
    cd gcpTrainingRepo/Task2/demo
    sudo pip3 install -r requirements.txt
    sudo gunicorn3 --bind 0.0.0.0:80 app:app --daemon
    ```

5. Created instance template with the above startup script:
    ![alt text][InstanceTemplate]
    Details:
    ![alt text][InstanceTemplateDetails]

6. Create instance group from the above template with autoscaling with minimum 3VM to maximum 6VM and triggering on threshold 60% CPU usages:
    ![alt text][InstanceGroup]


7. Once created check the external IP and test the load.
    ![alt text][ExternalIP]

    When we add extra load or traffic the instances will scaled up as below:
    ![alt text][InstanceGroupScaledUp]






[ExternalIP]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/Instance%20External%20Link%20site.png?raw=true "ExternalIP"

[Firewall]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/firewall.png?raw=true "Firewall"

[InstanceGroup]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/Instance%20Group.png?raw=true "InstanceGroup"

[InstanceGroupScaledUp]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/Instance%20Group%20Scalled%20up.png?raw=true "InstanceGroupScaledUp"

[InstanceTemplate]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/Instance%20Template.png?raw=true "InstanceTemplate"

[InstanceTemplateDetails]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/Instance%20Template%20Details.png?raw=true "InstanceTemplateDetails"

[VPCNetwork]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/VPC%20network.png?raw=true "VPCNetwork"

[VPCNetworkDetails]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/VPC%20network%20details.png?raw=true "VPCNetworkDetails"

[Subnet]: https://github.com/gohilmukund/gcpTrainingRepo/blob/main/Task2/pics/Instance%20External%20Link%20site.png?raw=true "Subnet"