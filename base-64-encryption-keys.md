---

copyright:
  years: 2021, 2025
lastupdated: "2025-06-17"

keywords:

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Creating base64-encoded encryption keys
{: #create-encryption-keys}

This section describes how to base64-encode your key value for proper key creation. This is required for MD5 authentication and if you plan to enable the MACsec feature.

The following examples show you how to use utilities that are readily available on your operating system to receive the encoded key string.

   There are many tools that you can use to base64 encode your key material. For example, to use OpenSSL to create and encode new or existing key material, see [Hyper Protect Crypto Services](/docs/hs-crypto?topic=hs-crypto-import-standard-keys#encode-key-material-standard-key) or [Key Protect](/docs/key-protect?topic=key-protect-import-standard-keys#how-to-encode-standard-key-material) documentation.
   {: note}

## Windows users
{: #windows-users}

You can use Powershell to base64-encode your key material.

### Key string input
{: #md5-key-string-input}

To encode a raw key string, first convert the string into bytes using UTF-8 encoding. Then, convert the bytes into a base64-encoded string:

```powershell
$KEY_VALUE = "abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789"
$ENCODED_KEY = [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes($KEY_VALUE))
```

To verify that the value was encoded properly, print the `$ENCODED_KEY` variable to the console:

```powershell
Write-Output $ENCODED_KEY
```

Output: `YWJjZGVmMDEyMzQ1Njc4OWFiY2RlZjAxMjM0NTY3ODlhYmNkZWYwMTIzNDU2Nzg5YWJjZGVmMDEyMzQ1Njc4OQ==`

### Key file input
{: #key-file-input}

To encode a key string from a file to its base64 value, first get the contents of the file. Then, convert the contents into bytes using UTF-8 encoding. In turn, you can then convert the bytes into a base64-encoded string using the same methods as the key string input:

```powershell
$KEY_FILE = "c:\path\to\file\key.txt"
$KEY_VALUE = get-content $KEY_FILE
$ENCODED_KEY = [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes($KEY_VALUE))
```

Again, verify by logging the `$ENCODED_KEY` value:

```powershell
Write-Output $ENCODED_KEY
```

Output: `YWJjZGVmMDEyMzQ1Njc4OWFiY2RlZjAxMjM0NTY3ODlhYmNkZWYwMTIzNDU2Nzg5YWJjZGVmMDEyMzQ1Njc4OQ==`

## MacOS and Linux users
{: #mac-linux-users}

You can use the `base64` utility available in the bash shell to base64-encode your key material.

### Key string input
{: #mac-linux-key-string-input}

To encode a raw string to its base64 value with `base64`, pipe the string as input to the utility. Use `printf` to avoid adding a newline character:

```bash
KEY_VALUE="abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789"
printf '%s' $KEY_VALUE | base64
```

Output: `YWJjZGVmMDEyMzQ1Njc4OWFiY2RlZjAxMjM0NTY3ODlhYmNkZWYwMTIzNDU2Nzg5YWJjZGVmMDEyMzQ1Njc4OQ==`

### Key file input
{: #mac-linux-key-file-input}

To encode a key string from a file to its base64 value, first get the file content, removing any new lines. Then, pipe this value to the `base64` utility. Again, use `printf` to avoid adding a newline character:

```bash
KEY_FILE="path/to/file/key.txt"
KEY_VALUE=$(tr -d '\n' < $KEY_FILE)
printf '%s' $KEY_VALUE | base64
```

Output: `YWJjZGVmMDEyMzQ1Njc4OWFiY2RlZjAxMjM0NTY3ODlhYmNkZWYwMTIzNDU2Nzg5YWJjZGVmMDEyMzQ1Njc4OQ==`
