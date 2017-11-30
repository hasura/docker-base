# docker-base

A minimal docker template to be used as a starting point to build projects on Hasura. A "project" is a "gittable" directory in the file system, which captures all the information regarding clusters, services and migrations. It can also be used to keep source code for custom services that you write.

### Step 1: Getting the project

```sh
$ hasura quickstart hasura/docker-base
$ cd docker-base
```

The above command does the following:
1. Creates a new folder in the current working directory called `docker-base`
2. Creates a new trial hasura cluster for you and sets that cluster as the default cluster for this project
3. Initializes `docker-base` as a git repository and adds the necessary git remotes.

### Step 2: Getting cluster information

Every hasura project is run on a Hasura cluster. To get details about the cluster this project is running on:

```sh
$ hasura cluster status
```

This will give you your cluster status like so

```sh
INFO Status:                                      
Cluster Name:       h34-excise98-stg
Cluster Alias:      hasura
Kube Context:       h34-excise98-stg
Platform Version:   v0.15.3
Cluster State:      Synced
```

Keep a note of your cluster name. Alternatively, you can also go to your [hasura dashboard](https://dashboard.hasura.io) and see the clusters you have.

### Step 3: Make modifications to base docker microservice

```sh
$ cd microservices/app
```

1. Add your source files/ binaries here
2. Modify Dockerfile to include the source files/binaries
3. Modify k8s.yaml to specify environment variables

### Step 4: Deploying on a hasura cluster

```sh
$ git add .
$ git commit -m "Initial Commit"
$ git push hasura master

