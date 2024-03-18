# deploy-api

Deploy Glados API to A-dapt servers

## Inputs

### `artefact-bucket`

**Required** Name of the S3 bucket for deployment artefacts

### `aws-region`

**Optional** AWS region to deploy to. Default `eu-west-1`

### `deploy-package`

**Required** Name of the deployment package to deploy (zip)

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
uses: A-dapt/deploy-api@v1.0
with:
  deploy-package: deploy.zip
  artefact-bucket: ${{ secrets.ADAPT_DEPLOYMENT_ARTEFACTS }}
  role-to-assume: ${{ secrets.AWS_ROLE_TO_ASSUME_ADAPT_CORE_PLATFORM }}
```

## Release

1. To release change version in the `VERSION` file and push branch to the repository
2. Merge to master
3. On master, run release make target `make release`

## TODO (Future versions)

- Version artefacts
- Deploy with capistrano dir layout
- Detect if deploy failed with aws ssm send-command
