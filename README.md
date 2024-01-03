helm package --destination charts .

helm repo index --url https://aldinkapetanovic.github.io/stress-chart .

helm repo index --url https://aldinkapetanovic.github.io/stress-chart --merge index.yaml .

helm upgrade --namespace stress --install stress ./stress-0.1.0.tgz --set ingress.enabled=true --set ingress.className=nginx --set autoscaling.enabled=true --set autoscaling.targetCPUUtilizationPercentage=5 --set autoscaling.targetMemoryUtilizationPercentage=30 --set autoscaling.maxReplicas=7
