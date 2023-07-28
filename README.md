# micro-service-deployment

helm install my-release autoscaler/cluster-autoscaler \
    --set autoDiscovery.clusterName=<CLUSTER NAME> \
    --set awsRegion=<YOUR AWS REGION> \
    --set awsAccessKeyID=<YOUR AWS KEY ID> \
    --set awsSecretAccessKey=<YOUR AWS SECRET KEY>
    --set "autoscalingGroups[0].name=your-asg-name" \
    --set "autoscalingGroups[0].maxSize=10" \
    --set "autoscalingGroups[0].minSize=1"

## To ensure DNS records are deleted as expected.
helm install stable/external-dns --namespace=kube-system --name=external-dns --set policy=sync