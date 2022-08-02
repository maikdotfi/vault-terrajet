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
