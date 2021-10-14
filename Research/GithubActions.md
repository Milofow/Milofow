create secret on azure with ```az ad sp create-for-rbac --name "githhubactionazure" --role contributor --scopes /subscriptions/your-subscription/resourceGroups/your-resource-group --sdk-auth```




different kind of acitons from azure https://github.com/azure/actions



actions like ```actions/checkout@v2``` are actually docker images 
(https://www.linkedin.com/learning/learning-github-actions-2/workflow-and-action-attributes?autoAdvance=true&autoSkip=true&autoplay=true&resume=false&u=2095956)



which events: https://docs.github.com/en/actions/learn-github-actions/events-that-trigger-workflows

<img width="975" alt="Schermafbeelding 2021-10-14 om 14 58 44" src="https://user-images.githubusercontent.com/73555911/137321994-093374a4-cead-478d-bb9b-de243f03c49e.png">
(https://www.linkedin.com/learning/learning-github-actions-2/add-actions-to-a-workflow-2?autoAdvance=true&autoSkip=true&autoplay=true&resume=false&u=2095956)


## Troubleshoot

if image is not build correctly into docker reference to url docker image is probably wrong try ```${{ secrets.DOCKER_HUB_USERNAME }}/devices-service:latest```

If jdk version is a problem while running change jdk version dockerfile
