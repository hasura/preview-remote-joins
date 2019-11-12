## Getting started

1. Install the dev build of the CLI for your machine from `cli/`

```
mv cli/cli-hasura-<arch> /usr/local/bin/hasura-dev
chmod +x /usr/local/bin/hasura-dev
```

2. Run hasura + postgres

```
docker-compose up -d
```

3. Run the graphql-service that we will do a remote join with

```
cd graphql-services/weather
npm i
npm start
```

4. (For linux only) Change the service endpoint of the graphql service depending on your platform
   in the migrations directory
```
cd hasura/migrations/1573259820770_create_remote_schema_weather
# Edit the file with your favorite editor and set the right ip for your service
vim up.yaml
```

5. Run the migrations to get the sample table and remote join setup

```
cd hasura
hasura-dev migrate apply
```

5. Open the console
```
hasura-dev console
```

## Troubleshooting

- *Inconsistent metadata*
When you open the console if you see an inconsistent metadata error, you might not have started the graphql-service
