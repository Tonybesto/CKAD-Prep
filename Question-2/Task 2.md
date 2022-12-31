Create a new file named config.txt with the following environment variables as key/value pairs
`DB_URL-localhost:1433 and DB_USERNAME-speed`

Create a new configmap named `db-config`

Create a Pod named `sqlsvr` that uses the environment variables from the configmap and runs a container using image of `nginx`

Shell into the pod and display the create environment variables.
