
## UI
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

3. Create a new branch with subject "CHGXXXXX" on [xplore-k8](https://github.com/anzx/xplore-k8s) and update the `xplore-k8s/environments/prod/versions.json` (Always good to compare it with `xplore-k8s/environments/staging/versions.json`)

![screenshot_new_branch](https://user-images.githubusercontent.com/109929798/185264404-061f463d-f965-4c59-9b60-75ad0b910ccf.png)

4. Raise a PR for this new branch / Wait for approve / Merge to `master` branch
