# Tanzu Application Platform Initialize Accelerator

The following files are included:
- `config/workload.yaml`: The definition of a Workload for a TAP Supply Chain
- `catalog/catalog-info.yaml`: The definition of a Component to make the Workload available in the TAP GUI Catalog
- `INSTRUCTIONS.md` : This file, providing instructions for preparing your project
- `accelerator-log.md` : This is the log file from the accelerator engine processing

## Preparing your spring-boot-samples project

Copy the provided `config` and `catalog` directories including the files they contain into your `spring-boot-samples` project.

You can now follow the instructions below to deploy your project.

## Working on your spring-boot-samples project

### Deploying to Kubernetes as a TAP workload with Tanzu CLI

If you make modifications to the source you must push the changes to your Git repository.

When you are done developing your app, you can simply deploy it using:

```
tanzu apps workload apply -f config/workload.yaml
```

If you would like to deploy the code from your local working directory you can use the following command:

```
tanzu apps workload create spring-boot-samples -f config/workload.yaml \
  --local-path . \
  --source-image <REPOSITORY-PREFIX>/spring-boot-samples-source \
  --type web
```

### Accessing the app deployed to your cluster

Determine the URL to use for the accessing the app by running:

```
tanzu apps workload get spring-boot-samples
```

To access the deployed app use the URL shown under "Workload Knative Services".

This depends on the TAP installation having DNS configured for the Knative ingress.
