# deploy-api

Deploy Glados API to A-dapt servers

## Inputs

### `artefact-bucket`

**Required** Name of the S3 bucket for deployment artefacts

### `aws-region`

**Optional**

### `deploy-package`

**Required** Name of the deployment package to deploy (zip)

### `role-to-assume`

**Required** ARN of the role to assume for deployment

## Example usage

```
uses: A-dapt/deploy-api@v1.0
with:
  deploy-package: 'deploy.zip'
  artefact-bucket: ${{ secrets.ADAPT_DEPLOYMENT_ARTEFACTS }}
  role-to-assume: ${{ secrets.AWS_ROLE_TO_ASSUME_ADAPT_CORE_PLATFORM }}
```

## TODO (Future versions)

- Version artefacts
- Deploy with capistrano dir layout
- Detect if deploy failed with aws ssm send-command
