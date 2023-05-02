# About Creating Bots
Here's a note for things related to creating bots for xplore.

## How to test the bot
A testing / checking use case for a DQ bot is going to be showing below.

1. Update code under the repo [anzx/xplore-bots](https://github.com/anzx/xplore-bots)
2. Raise a PR for the changes and deploy it to NP environment
3. Go to [GCP](https://console.cloud.google.com/)
4. Select `anz-x-xplore-np`, which is under `anz.com / ANZx / Xplore / Non-Production / anz-x-plore-np`
<img width="1725" alt="Screenshot 2023-05-02 at 1 28 07 pm" src="https://user-images.githubusercontent.com/109929798/235573464-0027c7a8-61e2-49c3-956d-647ca752b5db.png">

5. Find the related functions:
<img width="1725" alt="Screenshot 2023-05-02 at 1 30 39 pm" src="https://user-images.githubusercontent.com/109929798/235573720-5200cfac-1e74-4d24-89f4-12c3843025c5.png">

6. Go to `TESTING` tab, we can trigger the function from here. However, there are two types of functions - one can be triggered without parameter, while others need the parameter passing
<img width="1725" alt="Screenshot 2023-05-02 at 1 31 52 pm" src="https://user-images.githubusercontent.com/109929798/235573855-78826553-3f35-4943-be6a-7f76b6251f90.png">

7. Now we can go to [anzx/xplore-k8s](https://github.com/anzx/xplore-k8s), looking into the file: `xplore-k8s/lib/apps/trigger.libsonnet`. The testing fake trigger payload can be found here. Search for the bot you were creating and get the payload
<img width="1725" alt="Screenshot 2023-05-02 at 1 38 47 pm" src="https://user-images.githubusercontent.com/109929798/235574468-ae1ce4fa-7de1-4ee9-b209-bf343d3dfe61.png">

8. Encode the payloadData into base64 with the command line:
`echo -n 'input' | openssl base64`

9. Paste the encoded base64 string to GCP
<img width="711" alt="Screenshot 2023-05-02 at 1 44 02 pm" src="https://user-images.githubusercontent.com/109929798/235574956-46cd0330-8815-4bd4-9c0b-a5d1cf578e29.png">

<img width="1725" alt="Screenshot 2023-05-02 at 1 43 34 pm" src="https://user-images.githubusercontent.com/109929798/235574972-6b1773d1-d3fa-4910-b891-9aabbad83398.png">

10. Now we can test the bot on GCP.
