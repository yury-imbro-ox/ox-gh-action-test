# OX Security Scan GitHub Action

A [GitHub Action](https://github.com/features/actions) for using [OX Security](https://www.ox.security) to scan for vulnerabilities in your software projects.

You can use the Action as follows:

```yaml
name: Example workflow with OX Security Scan
on:
  push:
    branches:
      - main
  pull_request:
    types: [opened, reopened, synchronize]
    branches:
      - main
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Run OX Security Scan to check for vulnerabilities
        with:
          ox_api_key: ${{ secrets.OX_API_KEY }}
        uses: yury-imbro-ox/ox-gh-action-test@main
```

### Getting your OX Security API key

The Actions example above refer to an OX Security API key:

```yaml
with:
  ox_api_key: ${{ secrets.OX_API_KEY }}
```

Once you login to your OX Security account, an API key can be generated on the [settings page](https://app.ox.security/settings?tab=apiKey).

### Inputs

##### `ox_scan_full_branch`

If you want to scan the entire branch and not only the latest introduced commits, you can set `ox_scan_full_branch` to `"true"`. Default is `"false"`.

```yaml
with:
  ox_scan_full_branch: "true"
```

##### `ox_override_blocking`

If you want the step not to fail even if blocking issues are found, you can set `ox_override_blocking` to `"true"`. Default is `"false"`.

```yaml
with:
  ox_override_blocking: "true"
```

##### `ox_timeout`

Timeout in minutes after which OX Security scan will be canceled. Whether the step will fail or not depends on `ox_fail_on_timeout` option. Default is `20`.

```yaml
with:
  ox_timeout: "20"
```

##### `ox_fail_on_timeout`

If you want the step to fail if scan times out, you can set `ox_fail_on_timeout` to `"true"`. Default is `"false"`.

```yaml
with:
  ox_fail_on_timeout: "true"
```

##### `ox_fail_on_error`

If you want the step to fail if an error occurs (i.e. network, infrastructure), you can set `ox_fail_on_error` to `"true"`. Default is `"false"`.

```yaml
with:
  ox_fail_on_error: "true"
```
