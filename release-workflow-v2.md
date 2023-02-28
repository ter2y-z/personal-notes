
## Preparation of the deployment
1. Check the list on the chore releasing PR under ui repo  `Tuesday`  

2. Wait for Aimee to finish BVT on np  `Tuesday`  

3. Check, review and merge chore releasing PR  `Tuesday`  

4. After merging the releasing PR, an automated PR should be on [xplore-k8](https://github.com/anzx/xplore-k8s)  `Tuesday`  

5. Get approved and merge the automated PR on xplore-k8  `Tuesday`  

6. Check and test the changes on [**STAGING**](https://xplore-staging.service.anz/) to verify features from release notes   `Tuesday` /  `Wednesday`  

7. Let Amiee know **STAGING** is ready  `Tuesday` /  `Wednesday`  

8. Ask Amiee please have a CR (change request)  `Tuesday` /  `Wednesday`  

9. Get CR number (CHGXXXXX) and Release Notes from Aimee  `Tuesday`  /  `Wednesday`

## Deployment
1. Communicate with the primary support persons (usually one from Backend and one from Codex) to confirm the version deploying to prod

![Screenshot 2023-02-23 at 8 44 13 am](https://user-images.githubusercontent.com/109929798/221045628-3dc1961d-c14e-415f-98b1-ee16bf7d589d.png)

*We can know from the release note that*
- *Codex -> `v2.2.4`*
- *Xplore UI -> `v1.83.0`*
- *Xplore BFF -> `v1.32.3`*
- *xp-cf-service-casegenerator -> `v2.6.0`*
- *xp-cf-service-evidencegen -> `v2.6.0`*

2. Send "Commencing PROD Deployment CHGXXXXXXX" to Slack channel: [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4)

### Deployment on xplore-k8s
1. Create a new branch with subject "CHGXXXXX" on [xplore-k8](https://github.com/anzx/xplore-k8s) and update the `xplore-k8s/environments/prod/versions.json` (Always good to compare it with `xplore-k8s/environments/staging/versions.json`)

![screenshot_new_branch](https://user-images.githubusercontent.com/109929798/185264404-061f463d-f965-4c59-9b60-75ad0b910ccf.png)

2. Raise a PR for this new branch / Wait for approve / Merge to `master` branch

3. Go to [Harness Xplore Pipelines](https://anz.harness.io/#/account/hS-HqMsFS-q-XMGo1MMOow/app/0chR16ahRPChX7M1HiYqGA/pipelines) and find the related pipeline. In this case, for xplore-k8s, we should look for `tk-apply`. Click the latest execution:

![Screenshot 2023-02-28 at 3 55 33 pm](https://user-images.githubusercontent.com/109929798/221757875-0b868cc8-5d13-42b0-972e-4a9b256a3dec.png)

Once the `STAGE 1` and `STAGE 2` are green, we can copy the Harness link:

![Screenshot 2023-02-28 at 3 56 35 pm](https://user-images.githubusercontent.com/109929798/221758107-fb7a3a6f-aa66-4737-8fcb-72350975d5da.png)

4. Now we get CR number, CR link and the Harness link, we can go to the [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4) channel on Slack and click `Prod pipeline approval` under Shortcuts:

![Screenshot 2023-02-28 at 4 01 43 pm](https://user-images.githubusercontent.com/109929798/221758889-738eee5c-5af5-4fce-9901-99d38a5e1aa3.png)

Shout out in the channel and wait for approval.

5. Go back to Harness and wait for all the boxes are green then we can ask Aimee, Jenny or Daisy to do the BVT for the prod.


### Deployment on xplore-cloud-functions

We still need to deploy `xp-cf-service-casegenerator` and `xp-cf-service-evidencegen` according to the release notes. Sometimes it can be searched on Github to locate which repo it is or confirm it with the support members. In thise case, they're sitting in `xplore-cloud-functions`

![Screenshot 2023-02-28 at 4 08 00 pm](https://user-images.githubusercontent.com/109929798/221759637-d0f03b83-b46d-4004-8411-7e4461675bd2.png)


1. Create a new branch with subject "CHGXXXXX" on [xplore-k8](https://github.com/anzx/xplore-k8s) and update the `xplore-k8s/environments/prod/versions.json` (Always good to compare it with `xplore-k8s/environments/staging/versions.json`)

![screenshot_new_branch](https://user-images.githubusercontent.com/109929798/185264404-061f463d-f965-4c59-9b60-75ad0b910ccf.png)

2. Raise a PR for this new branch / Wait for approve / Merge to `master` branch

3. Go to [Harness Xplore Pipelines](https://anz.harness.io/#/account/hS-HqMsFS-q-XMGo1MMOow/app/0chR16ahRPChX7M1HiYqGA/pipelines) and find the related pipeline. In this case, for xplore-k8s, we should look for `tk-apply`. Click the latest execution:

![Screenshot 2023-02-28 at 3 55 33 pm](https://user-images.githubusercontent.com/109929798/221757875-0b868cc8-5d13-42b0-972e-4a9b256a3dec.png)

Once the `STAGE 1` and `STAGE 2` are green, we can copy the Harness link:

![Screenshot 2023-02-28 at 3 56 35 pm](https://user-images.githubusercontent.com/109929798/221758107-fb7a3a6f-aa66-4737-8fcb-72350975d5da.png)

4. Now we get CR number, CR link and the Harness link, we can go to the [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4) channel on Slack and click `Prod pipeline approval` under Shortcuts:

![Screenshot 2023-02-28 at 4 01 43 pm](https://user-images.githubusercontent.com/109929798/221758889-738eee5c-5af5-4fce-9901-99d38a5e1aa3.png)

Shout out in the channel and wait for approval.

5. Go back to Harness and wait for all the boxes are green then we can ask Aimee, Jenny or Daisy to do the BVT for the prod.
