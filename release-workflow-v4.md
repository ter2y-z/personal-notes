
## Preparation of the deployment
### Cutting release (deploy from NP to STAGING)

1. Wait for Aimee to finish BVT on np  `Tuesday`

2. Check the list on the Release section for each repo `Tuesday`  
- ui: https://github.com/anzx/xplore-ui/releases
- bff: https://github.com/anzx/xplore-backend/releases
- codex: https://github.com/anzx/codex-jmix/releases

3. An automated PR should be on [xplore-k8](https://github.com/anzx/xplore-k8s) after each repo publishing release
   - [Why I can't see an automated PR on k8s](#deployment-on-xplore-k8s)

4. Get approved and merge the automated PRs on xplore-k8s  `Tuesday`  

5. Check and test the changes on [**STAGING**](https://xplore-staging.service.anz/) to verify features from release notes   `Tuesday` /  `Wednesday`  

6. Let Amiee know **STAGING** is ready  `Tuesday` /  `Wednesday`  

7. Ask Amiee please have a CR (change request)  `Tuesday` /  `Wednesday`  

8. Get CR number (CHGXXXXX) and Release Notes from Aimee  `Tuesday`  /  `Wednesday`

# TO BE CONTINUE

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
1. Change CR status to `Implement`
![Screenshot 2023-06-29 at 11 22 42 am](https://github.com/TerryZhengANZx/personal-notes/assets/109929798/2d6ce01a-154c-4382-9e5a-8988cac6f339)

2. Create a new branch with subject "CHGXXXXX" on [xplore-k8](https://github.com/anzx/xplore-k8s) and update the `xplore-k8s/environments/prod/versions.json` (Always good to compare it with `xplore-k8s/environments/staging/versions.json`)

![screenshot_new_branch](https://user-images.githubusercontent.com/109929798/185264404-061f463d-f965-4c59-9b60-75ad0b910ccf.png)

3. Raise a PR for this new branch / Wait for approve / Merge to `master` branch

4. Go to [xplore-k8s/actions](https://github.com/anzx/xplore-k8s/actions), getting the gha pending link

5. Now we get CR number, CR link and the gha link, we can go to the [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4) channel on Slack and click `Prod pipeline approval` under Shortcuts:

Shout out in the channel and wait for approval.

6. Go back to Harness and wait for all the boxes are green then we can ask Aimee, Jenny or Daisy to do the BVT for the prod.


### Deployment on xplore-cloud-functions

We still need to deploy `xp-cf-service-casegenerator` and `xp-cf-service-evidencegen` according to the release notes. Sometimes it can be searched on Github to locate which repo it is or confirm it with the support members. In thise case, they're sitting in `xplore-cloud-functions`

![Screenshot 2023-02-28 at 4 08 00 pm](https://user-images.githubusercontent.com/109929798/221759637-d0f03b83-b46d-4004-8411-7e4461675bd2.png)


1. Create a new branch with subject "CHGXXXXX" on [xplore-cloud-functions](https://github.com/anzx/xplore-cloud-function) and update the `xplore-cloud-functions/versions/prod.jsonnet`

![Screenshot 2023-11-02 at 1 36 49 pm](https://github.com/TerryZhengANZx/personal-notes/assets/109929798/79721254-3be5-4352-9918-b291b405b734)

2. Raise a PR for this new branch / Wait for approve / Merge to `master` branch

3. Go to [xplore-cloud-functions/actions](https://github.com/anzx/xplore-cloud-functions/actions) and find the related gha link.

4. Now we get CR number, CR link and the gha link, we can go to the [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4) channel on Slack and click `Prod pipeline approval` under Shortcuts:

Shout out in the channel and wait for approval.

5. Go back to Harness and wait for all the boxes are green then we can ask Aimee, Jenny or Daisy to do the BVT for the prod.
