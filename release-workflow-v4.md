# Preparation

:scissors: We need to cut release (deploy from NP to STAGING) for the repos.

1. Wait for Aimee to finish BVT on NP (Tuesday).

2. Check the Release section for each repo (Tuesday):  
   - UI: https://github.com/anzx/xplore-ui/releases
   - BFF: https://github.com/anzx/xplore-backend/releases
   - Codex: https://github.com/anzx/codex-jmix/releases

3. Ensure an automated PR is created on [xplore-k8s](https://github.com/anzx/xplore-k8s) after each repo publishes a release.
   - [Why I can't see an automated PR on k8s](#why-i-cant-see-an-automated-PR-on-k8s)

4. Approve and merge the automated PRs on xplore-k8s (Tuesday).

5. Check and test the changes on [**STAGING**](https://xplore-staging.service.anz/) to verify features from release notes (Tuesday/Wednesday).

6. Inform Aimee that **STAGING** is ready (Tuesday/Wednesday).

7. Request Aimee to initiate a Change Request (CR) (Tuesday/Wednesday).

8. Obtain the CR number (CHGXXXXX) and Release Notes from Aimee (Tuesday/Wednesday).

# Deployment
Confirm release details with the team/Aimee. Information can typically be found in the release documentation, like the example below:

![Screenshot 2023-02-23 at 8 44 13 am](https://user-images.githubusercontent.com/109929798/221045628-3dc1961d-c14e-415f-98b1-ee16bf7d589d.png)

*Example from release notes:*
- *Codex -> `v2.2.4`*
- *Xplore UI -> `v1.83.0`*
- *Xplore BFF -> `v1.32.3`*
- *xp-cf-service-casegenerator -> `v2.6.0`*
- *xp-cf-service-evidencegen -> `v2.6.0`*

## ☸ Release on xplore-k8s

1. Announce "Commencing PROD Deployment CHGXXXXXXX" in the Slack channel: [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4).

2. Change CR status to `Implement`.

   ![Screenshot 2023-06-29 at 11 22 42 am](https://github.com/TerryZhengANZx/personal-notes/assets/109929798/2d6ce01a-154c-4382-9e5a-8988cac6f339)

3. Create a new branch named "CHGXXXXX" on [xplore-k8s](https://github.com/anzx/xplore-k8s) and update `xplore-k8s/environments/prod/versions.json` (compare with `xplore-k8s/environments/staging/versions.json`).

   ![screenshot_new_branch](https://user-images.githubusercontent.com/109929798/185264404-061f463d-f965-4c59-9b60-75ad0b910ccf.png)

4. Raise a PR for this new branch, wait for approval, then merge it to the `master` branch.

5. Go to [xplore-k8s/actions](https://github.com/anzx/xplore-k8s/actions) and find the new action running under `🕋 X Single Env CICD (KubeRaw)`. Click and open it to get the GHA URL.

   ![Screenshot 2024-08-01 at 12 07 48 PM](https://github.com/user-attachments/assets/2baafb1f-30b8-43ab-a5df-339c1d923a40)

6. With the CR number, CR link, and GHA URL, go to the [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4) channel on Slack and click `Prod pipeline approval` under Shortcuts.

   ![Screenshot 2024-08-01 at 12 12 23 PM](https://github.com/user-attachments/assets/30f75a18-42a1-4f77-b393-2be34d818b21)

7. Wait for approval, which will trigger the continuation of the action.

8. Once all actions are finished, verify the changes are on PROD and request Aimee to conduct another BVT on PROD.



## 🚧 Release on xplore-infra

1. At the beginning, ask the whole team to confirm what changes need to be include in the CR. Then confirm all the information with Aimee.

2. Confirm which workflow the PR needs to run. According to Ashitha:
   > "Usually it comes up in the PR comments which component is being updated (Apromore, BigQuery, common, etc.) and we run the workflow accordingly."

   Examples:
   - [#1781](https://github.com/anzx/xplore-infra/pull/1781): Needs `🎪 CICD (BigQuery)`
   - [#1760](https://github.com/anzx/xplore-infra/pull/1760): Needs `🌰 CICD (Dashboard)`, `🎪 CICD (BigQuery)`, `🍏 CICD (Apromore)`, `⛅️ CICD (Cloudfunction)`, `🐪 CICD (Common)`
   - [#1773](https://github.com/anzx/xplore-infra/pull/1773): Confirm with the team if the comment section lacks information.

3. Go to [Actions](https://github.com/anzx/xplore-infra/actions) and find the related actions which is waiting. For example, for the PR #1781, we should click `🎪 CICD (BigQuery)` on the left handside menu. Then we can find it waiting in the list:
  ![Screenshot 2024-08-02 at 11 54 58 AM](https://github.com/user-attachments/assets/4000aa67-867d-4d01-9d1d-107840eca1a9)

4. Click the workflow, then click the pipeline that waiting for approval and get the GHA url:
   ![Screenshot 2024-08-02 at 11 56 49 AM](https://github.com/user-attachments/assets/9a2eab2f-4428-422b-b8e1-620fbe00896e)

5. With the CR number, CR link, and GHA URL, go to the [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4) channel on Slack and click `Prod pipeline approval` under Shortcuts.

## :cloud: Release on xplore-cloud-functions (OLD)

Deploy `xp-cf-service-casegenerator` and `xp-cf-service-evidencegen` as noted in the release notes. Verify the repo on GitHub or confirm with support members. In this case, they reside in `xplore-cloud-functions`.

![Screenshot 2023-02-28 at 4 08 00 pm](https://user-images.githubusercontent.com/109929798/221759637-d0f03b83-b46d-4004-8411-7e4461675bd2.png)

1. Create a new branch named "CHGXXXXX" on [xplore-cloud-functions](https://github.com/anzx/xplore-cloud-functions) and update `xplore-cloud-functions/versions/prod.jsonnet`.

   ![Screenshot 2023-11-02 at 1 36 49 pm](https://github.com/TerryZhengANZx/personal-notes/assets/109929798/79721254-3be5-4352-9918-b291b405b734)

2. Raise a PR for this new branch, wait for approval, and merge it to the `master` branch.

3. Go to [xplore-cloud-functions/actions](https://github.com/anzx/xplore-cloud-functions/actions) and find the related GHA link.

4. With the CR number, CR link, and GHA link, go to the [#xplore-release](https://anzx.slack.com/archives/C0160MTKEP4) channel on Slack and click `Prod pipeline approval` under Shortcuts. Announce in the channel and wait for approval.

5. Monitor Harness until all boxes are green, then request Aimee, Jenny, or Daisy to perform BVT for PROD.


# After BVT
1. Go to the CR page and load the related lists at the bottom of the page
![Screenshot 2024-09-13 at 11 34 39 AM](https://github.com/user-attachments/assets/4e169539-c93f-439f-9ee1-b976b5cffcc7)

2. Click the tasks assign to you.
3. Click the `Closure Information` tab at the bottom of page.
4. Update the close code to success and just simply input `Completed` to Close notes.

   
# Frequently Asked Questions
<details>
  <summary id="why-i-cant-see-an-automated-PR-on-k8s"><h2>Why can't I see an automated PR on k8s?</h2></summary>

  The absence of an automated PR on k8s can be caused by different issues, varying case by case. Here's a breakdown:

  - If you notice logs under a failed `create-pr` workflow, such as:
    ```
    ...
    To https://github.com/anzx/xplore-k8s
    ! [rejected]          auto-release-bff-staging -> auto-release-bff-staging (non-fast-forward)
    error: failed to push some refs to 'https://github.com/anzx/xplore-k8s'
    hint: Updates were rejected because the tip of your current branch is behind
    ...
    ```
    This indicates that there is already a branch named `auto-release-xxx-staging` that previously failed to merge. As a result, the workflow failed to create a new branch with the same name.
</details>
