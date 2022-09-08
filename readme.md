kubectl apply -f helm-app.yaml

# airflow
`kubectl apply -f helm-airflow-kuber.yaml`
`kubectl port-forward svc/airflow-web 8080:8080 --namespace airflow`

`kubectl create secret generic airflow-ssh-git-secret --from-file=gitSshKey=/Users/yuriy/Documents/study/airflow_k8s/argocd_template/.ssh/id_rsa -n airflow`

yc iam key create \
  --service-account-name sa-ingress \
  --output sa-ingress-key.json

  export HELM_EXPERIMENTAL_OCI=1 && \
cat sa-key.json | helm registry login cr.yandex --username 'json_key' --password-stdin && \
helm pull oci://cr.yandex/yc/yc-alb-ingress-controller-chart \
  --version=v0.1.0 \
  --untar && \
helm install \
  --namespace yc-alb-ingress \
  --set folderId=b1ghud05kp68m8mkm5kj \
  --set clusterId=b1gv3klte1l0to0dduvt \
  --set-file saKeySecretKey=sa-key.json \
yc-alb-ingress-controller ./yc-alb-ingress-controller-chart/
