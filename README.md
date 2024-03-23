# deploy-api

Deploy Glados API to A-dapt servers

## Inputs

### `application-name`

**Required** Name of the application to deploy. This must match the buildpack name.

### `aws-region`

**Optional** AWS region to deploy to. Default `eu-west-1`

### `buildpack-bucket`

**Optional** Name of the S3 bucket where buildpacks are stored. Default `a-dapt-deployment-artefacts`

### `cluster-name`

**Optional** Name of the K8 cluster to deploy application. Default `production`

### `role-to-assume`

**Required** ARN of the role to assume for deployment

## Example usage

The permissions are needed to interact with GitHub's OIDC Token endpoint. This is on the root of your workflow yaml file

```yaml
permissions:
  id-token: write
  contents: write
  statuses: write
```

The following is an example of how to use this action in a workflow:

```yaml
uses: a-dapt/deploy-api@v2.0
with:
  application-name: api-glados
  role-to-assume: ${{ secrets.AWS_ROLE_TO_ASSUME_ADAPT_CORE_PLATFORM }}
```

## Release

1. To release change version in the `VERSION` file and push branch to the repository
2. Merge to master
3. On master, run release make target `make release`
