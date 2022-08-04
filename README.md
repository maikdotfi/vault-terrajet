# Vault Crossplane Provider

For now just testing if this will work with reasonable effort, otherwise might go with a Terraform operator directly.

**NOTE:** Realized that there is a terrajet generated vault provider already, but this was interesting to learn still: <https://github.com/crossplane-contrib/provider-jet-vault>

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

## Generate

Turns out Go 1.18 isn't a good version, so I switched to 1.17 on the macbook:

```bash
mv /opt/homebrew/bin/go /opt/homebrew/bin/go-1.18
sudo cp /opt/homebrew/Cellar/go@1.17/1.17.11/bin/go /opt/homebrew/bin/go
go version
```

Was also missing goimports binary:

```bash
go install golang.org/x/tools/cmd/goimports
export PATH=$PATH:$HOME/go/bin
make generate
```

Now generation works, and on a M1 MBP!
