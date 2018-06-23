# puppet-vault
A set of tools for puppet <-> Hashicorp vault integration.
Though a hiera-based solution exists, we chose a different solution to provide credentials to the puppet. 

# design description
## facter plugin
A facter plugin is used to fetch credentials from the vault credentials storage. The plugin expects either $VAULT_TOKEN and $VAULT_HOST variables to be set, or a config file /etc/vault.conf to exist. If none provided, the plugin gracefully exits. The plugin populates a $::vault hash with variables available for the specific token.

## vault-token puppet module
A vault-token puppet module is used to generate a new accessor token using a pre-defined policy. This token is stored in a /etc/vault.conf file.
