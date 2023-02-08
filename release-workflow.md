[Release workflow on xplore-ui Wiki](https://github.com/anzx/xplore-ui/wiki/Release-workflow)

[Release / Change Request process](https://confluence.service.anz/pages/viewpage.action?pageId=1185974461)

## Deploy to staging environment
1. Check the list on the chore releasing PR under ui repo  `Tuesday`  

2. Wait for Aimee to finish BVT on np  `Tuesday`  

3. Check, review and merge chore releasing PR  `Tuesday`  

4. After merging the releasing PR, an automated PR should be on [xplore-k8](https://github.com/anzx/xplore-k8s)  `Tuesday`  

5. Get approved and merge the automated PR on xplore-k8  `Tuesday`  

6. Check and test the changes on [staging](https://xplore-staging.service.anz/) to verify features from release notes   `Wednesday`  

7. Let Amiee know STAGING is ready  `Wednesday`  

8. Ask Amiee please have a CR (change request)  `Tuesday` /  `Wednesday`  

9. Get CR number (CHGXXXXX) from Aimee  `Tuesday`  /  `Wednesday`  


## Deploy to production environment
xplore-k8s  
send "Commencing PROD Deployment for UI v1.xx.xx (CHGXXXXXXX)" to slack channel : xplore-release  
create PR on xplore-k8s  
create new branch "CHGXXXXX" on local xplore-k8s  TH

update prod/version.json version number on xplore-k8s   TH

double check if it's same version number on staging/version.json  

Subject: CHGXXXXX  

description:   
![Screen Shot 2022-08-18 at 10 04 10 am](https://user-images.githubusercontent.com/109929798/185264404-061f463d-f965-4c59-9b60-75ad0b910ccf.png)

push to origin  
that's production ready  
wait for approve  
merge  
click implement button   
click on shortcut "Prod pipeline approval" on slack  
![Screen Shot 2022-08-11 at 11 45 31 am](https://user-images.githubusercontent.com/109929798/184051210-2d33896e-6c36-47af-b987-249b071ea2bb.png)

click harness link - wait for all boxes are green:  
![Screen Shot 2022-08-18 at 10 12 13 am](https://user-images.githubusercontent.com/109929798/185265074-4743209d-0637-4e6f-93c1-5f6fc268d629.png)
then shout out in the channel `xplore-release`

do BVT by Aimee (BVT can be done by Aimee, Jenny or Daisy)


