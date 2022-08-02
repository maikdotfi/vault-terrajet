# Vault Crossplane Provider

For now just testing if this will work with reasonable effort, otherwise might go with a Terraform operator directly.

## Steps so far

```bash
make submodules
export ProviderNameLower=vault
export ProviderNameUpper=Vault
./hack/prepare.sh
```

Next modified the top vars in Makefile to match the Vault provider, also realized might need to do this in Linux.. Let's see!

When adding the provider configuration noticed the env vars seem to be deprecated/perhaps even broken (if in shared gRPC?):
		// set environment variables for sensitive provider configuration
		// Deprecated: In shared gRPC mode we do not support injecting
		// credentials via the environment variables. You should specify
		// credentials via the Terraform main.tf.json instead.

Thus I decided to go with the keys even for token.
