
# Terraform, tflint, and TFGrunt (terraform)

Installs the Terraform CLI and optionally TFLint and Terragrunt. Auto-detects latest version and installs needed dependencies.

## Example Usage

```json
"features": {
    "ghcr.io/devcontainers/features/terraform:1": {}
}
```

## Options

| Options Id | Description | Type | Default Value |
|-----|-----|-----|-----|
| version | Terraform version | string | latest |
| tflint | Tflint version (https://github.com/terraform-linters/tflint/releases) | string | latest |
| terragrunt | Terragrunt version | string | latest |
| installSentinel | Install sentinel, a language and framework for policy built to be embedded in existing software to enable fine-grained, logic-based policy decisions | boolean | false |
| installTFsec | Install tfsec, a tool to spot potential misconfigurations for your terraform code | boolean | false |
| installTerraformDocs | Install terraform-docs, a utility to generate documentation from Terraform modules | boolean | false |
| httpProxy | Connect to a keyserver using a proxy by configuring this option | string | - |
| customDownloadServer | Custom server URL for downloading Terraform and Sentinel packages, including protocol (e.g., https://releases.hashicorp.com). If not provided, the default HashiCorp download server (https://releases.hashicorp.com) will be used. | string | - |

## Customizations

### VS Code Extensions

- `HashiCorp.terraform`



## Licensing

On August 10, 2023, HashiCorp announced a change of license for its products, including Terraform. After ~9 years of Terraform being open source under the MPL v2 license, it was to move under a non-open source BSL v1.1 license, starting from the next (1.6) version. See https://github.com/hashicorp/terraform/blob/main/LICENSE

## Custom Download Server

The `customDownloadServer` option allows you to specify an alternative server for downloading Terraform and Sentinel packages. This is useful for organizations that maintain internal mirrors or have proxies for HashiCorp downloads.

When using this option:
- Provide the complete URL including protocol (e.g., `https://my-mirror.example.com`)
- The server should mirror the HashiCorp releases structure

Example:
```json
"features": {
    "ghcr.io/devcontainers/features/terraform:1": {
        "customDownloadServer": "https://my-mirror.example.com"
    }
}
```

### ⚠️ Security Considerations

When using a custom download server, be aware of the following security implications:

- **Server Verification**: Always verify that the custom server is trustworthy and maintained by your organization or a trusted entity. Using an untrusted or compromised server could lead to downloading malicious software.
  
- **Supply Chain Risks**: Malicious actors may attempt to distribute compromised versions of Terraform that contain backdoors, cryptominers, or other harmful code.
  
- **Integrity Checks**: The feature performs SHA256 checks when available, but these are only as trustworthy as the source of the checksums. If both the binaries and checksums come from a compromised server, the integrity check may pass despite the software being malicious.
  
- **Organizational Policy**: Ensure your custom download server adheres to your organization's security policies and implements proper access controls.

Always use the official HashiCorp download server (https://releases.hashicorp.com) unless you have a specific need for an alternative source.

## OS Support

This Feature should work on recent versions of Debian/Ubuntu-based distributions with the `apt` package manager installed.

`bash` is required to execute the `install.sh` script.


---

_Note: This file was auto-generated from the [devcontainer-feature.json](https://github.com/devcontainers/features/blob/main/src/terraform/devcontainer-feature.json).  Add additional notes to a `NOTES.md`._
