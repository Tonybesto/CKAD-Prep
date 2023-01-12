Create a secret from literal values

Create a new secret named `db-credentials` with the key/value pair `db-password=speed`


Create a Pod names `sqlsvr` that uses the secret as environment variable named `DB_PASSWORD` and run the container with the image `nginx`


Shell into the Pod and print out the created environment variables

