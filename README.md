# dotnet-certificate-tool

Command line tool to install and remove pfx certificates from the current user's store.

Mainly used to workaround the limitation of certificates installed in the current user's store in Unix hosts.

See [following github issue for more information](https://github.com/dotnet/corefx/issues/32875).

## Usage

Available arguments:

- **--base64 (-b)**: base 64 encoded certificate value
- **--file (-f)**: path to the \*.pfx certificate file
- **--password (-p)**: password for the \*.pfx certificate _(required)_
- **--thumbprint (-t)**: certificate thumbprint _(required)_
- **--store-name (-s)**: certificate store name (defaults to My). See possible values [here](https://docs.microsoft.com/en-us/dotnet/api/system.security.cryptography.x509certificates.storename?view=netframework-4.8)

### With a base 64 string

Assuming you have the following environment variables setup:

- \$base64: base 64 encoded certificate value
- \$password: pfx certificate password
- \$thumbprint: certificate's thumbprint

`dotnet ShareGate.CertificateTool.dll add --base64 $base64 --password $password --thumbprint $thumbprint --store-name My`

`dotnet ShareGate.CertificateTool.dll remove --base64 $base64 --password $password --thumbprint $thumbprint --store-name My`

### With a pfx file

Assuming you have the following environment variables setup:

- \$password: pfx certificate password
- \$thumbprint: certificate's thumbprint

`dotnet ShareGate.CertificateTool.dll add -f ./cert.pfx --password $password --thumbprint $thumbprint --store-name Root`

`dotnet ShareGate.CertificateTool.dll remove -f ./cert.pfx --password $password --thumbprint $thumbprint --store-name Root`
