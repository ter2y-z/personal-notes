== staging ==
go to chore  
check the list  
wait for Aimee to confirm  
check chore pr  
review chore pr  
merge chore pr  
after testing, can see pr on /xplore/k8s  
get approve & merge PR  
ask Amiee please have a CR (change request)  
get CR number (CHGXXXXX) from Aimee  
create new branch "CHGXXXXX" on local xplore-k8s  
update prod/version.json version number on xplore-k8s  
double check if it's same version number on staging/version.json  
Subject: CHGXXXXX  
description:   
![Screen Shot 2022-08-18 at 10 04 10 am](https://user-images.githubusercontent.com/109929798/185264404-061f463d-f965-4c59-9b60-75ad0b910ccf.png)

rebase if needed  
push to origin  
that's production ready  

== production ==  
xplore-k8s  
send "Commencing PROD Deployment for UI v1.xx.xx (CHGXXXXXXX)" to slack channel : xplore-release  
create PR on xplore-k8s  
wait for approve  
merge  
click on shortcut "Prod pipeline approval" on slack  
![Screen Shot 2022-08-11 at 11 45 31 am](https://user-images.githubusercontent.com/109929798/184051210-2d33896e-6c36-47af-b987-249b071ea2bb.png)
