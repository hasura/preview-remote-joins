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

4. (For linux only) Since we are running Hasura in a docker container, change the ip of the graphql-service (depending on OS)

```
# Edit the file with your favorite editor and set the right ip for your service
vim hasura/migrations/1573259820770_create_remote_schema_weather/up.yaml
```

5. Run the migrations to get the sample table and remote join setup

```
cd hasura
hasura-dev migrate apply
```

6. Open the console
```
hasura-dev console
```

## Troubleshooting

- *Inconsistent metadata*
When you open the console if you see an inconsistent metadata error, you might not have started the graphql-service
