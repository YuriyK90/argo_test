kubectl apply -f helm-app.yaml

# airflow
`kubectl apply -f helm-airflow-kuber.yaml`
`kubectl port-forward svc/airflow-web 8080:8080 --namespace airflow`