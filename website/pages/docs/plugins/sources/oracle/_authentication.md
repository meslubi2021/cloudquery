In order for CloudQuery to sync resources from your Oracle Cloud setup, you will need to authenticate with your Oracle Cloud account.
CloudQuery supports the same authentication methods as the OCI Go SDK, and uses the "default" configuration provider. You can read about how to create an Oracle Cloud configuration file in https://docs.oracle.com/en-us/iaas/Content/API/Concepts/sdkconfig.htm.


### Option 1: Config file

An example configuration file (e.g. in `~/.oci/config`) looks like this:

```ini copy
[DEFAULT]
user=ocid1.user.oc1..<unique_ID>
fingerprint=<your_fingerprint>
key_file=~/.oci/oci_api_key.pem
tenancy=ocid1.tenancy.oc1..<unique_ID>
region=us-ashburn-1
```

:::callout{type="info"}
Note that CloudQuery will `sync` information from all regions - not only the region specified in the `oci` config.
:::

### Option 2: Environment variables

Environment variables are configured the same way as for the terraform provider, and should therefore be prefixed with `TF_VAR_` (e.g. `TF_VAR_tenancy_ocid`). See the [documentation](https://docs.oracle.com/en-us/iaas/Content/API/SDKDocs/terraformproviderconfiguration.htm) for a full list of available variables.

Example environment variables:

```bash copy
export TF_VAR_security_token_file=/path/to/token/file
export TF_VAR_fingerprint="<your_fingerprint>"
export TF_VAR_tenancy_ocid="ocid1.tenancy.oc1..<unique_ID>"
export TF_VAR_user_ocid="ocid1.user.oc1..<unique_ID>"
export TF_VAR_region="us-ashburn-1"
export TF_VAR_private_key_path="~/.oci/oci_api_key.pem"
```