# kubereboot charts
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fkubereboot%2Fcharts.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fkubereboot%2Fcharts?ref=badge_shield)


[![](https://github.com/kubereboot/charts/workflows/Release%20Charts/badge.svg?branch=main)](https://github.com/kubereboot/charts/actions)

## Usage

Add the repo (only needed if you want to use the classical approach without using the [OCI registry](https://helm.sh/docs/topics/registries/)):

```
helm repo add kubereboot https://kubereboot.github.io/charts
```

## Charts

- [kured](https://github.com/kubereboot/charts/tree/main/charts/kured)

### Overriding kured options with environment variables

Kured supports overriding most configuration options using environment variables. The convention is:

- The environment variable name is the CLI flag name, uppercased, with dashes replaced by underscores, and prefixed with `KURED_`.
- For example:
  - `slackHookUrl` → `KURED_SLACK_HOOK_URL`
  - `notifyUrl` → `KURED_NOTIFY_URL`
  - `rebootSentinel` → `KURED_REBOOT_SENTINEL`

This is especially useful for injecting sensitive values (such as webhook URLs) from Kubernetes secrets. You can use the `extraEnvVars` section in `values.yaml` to add these environment variables, for example:

```yaml
extraEnvVars:
  - name: KURED_NOTIFY_URL
    valueFrom:
      secretKeyRef:
        name: my-secret
        key: notify-url
```

See the Kured [Repository](https://github.com/kubereboot/kured) and [Documentation](https://kured.dev) for more details.

## Contributing

Please refer to the [Kured Contribution guidelines](https://github.com/kubereboot/kured/blob/main/CONTRIBUTING.md).

## Code of conduct

Please refer to the [Code of Conduct guidelines](https://github.com/kubereboot/kured/blob/main/README.md).

## Security

Please refer to the [Security process](https://github.com/kubereboot/kured/blob/main/README.md).


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fkubereboot%2Fcharts.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fkubereboot%2Fcharts?ref=badge_large)