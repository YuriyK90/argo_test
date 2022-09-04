kubectl apply -f helm-app.yaml

# airflow
`kubectl apply -f helm-airflow-kuber.yaml`
`kubectl port-forward svc/${AIRFLOW_NAME}-web 8080:8080 --namespace $AIRFLOW_NAMESPACE`