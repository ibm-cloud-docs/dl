---

copyright:
  years: 2021, 2024
lastupdated: "2024-06-19"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Setting up BGP Message Digest 5 (MD5) authentication keys
{: #dl-md5}

Border Gateway Protocol (BGP) authentication is an added layer of security that enables routers to share information only if they can verify that they are communicating with a trusted source, based on a key. TCP MD5 authentication between BGP peers verifies each transmitted message sent through the BGP session.
{: shortdesc}

## BGP authentication requirements
{: #bgp-md5-important-notices}

Make sure to adhere to the following BGP MD5 authentication requirements:

 * BGP MD5 keys must be created as an imported, **type-standard key** (not a root key). The key material that you provide must be base64-encoded and the original string cannot exceed a maximum of 126 printable ASCII characters in length. For more information, see [Creating base64-encoded encryption keys](/docs/dl?topic=dl-dl-md5#create-encryption-keys).

   The key material must be base-64-encoded and can be up to 7,500 bytes. The key name (different from the key material) is a unique, human-readable name for easy identification of your key.
   {: note}

 * During an authenticated BGP session, BGP peers must be configured with the same key to establish a BGP neighbor relationship. Routers that are configured with a different key cannot maintain a BGP neighbor relationship.

## Setting up BGP MD5 authentication keys
{: #setting-up-bgp-md5-keys}

You can store your keys in either Key Protect or Hyper Protect Crypto Services (HPCS). To configure BGP MD5 authentication, follow these steps:

1. Set up a keystore instance with keys. For instructions, see [Key Protect: Getting started with encryption keys](/docs/key-protect?topic=key-protect-getting-started-tutorial) or [HPCS: Creating and importing encryption keys](/docs/hs-crypto?topic=hs-crypto-tutorial-import-keys).

   If you use HPCS, it is important to note that the `"extractable": <key_type>` value is set to `true` for standard keys.
   {: note}

1. After you create encryption keys for Direct Link, use IBM Cloud Identity and Access Management (IAM) to grant authorization between your instance and the Direct Link service. You can grant access at the instance level, which grants the Direct Link service access to all the keys inside that instance. You can also grant access on a key-by-key basis. For instructions, see [Using authorizations to grant access between services](/docs/account?topic=account-serviceauth).

   If you use Key Protect, select **Resources based on selected attributes** after you select **Direct Link** as the Source service. Then, select either **Resource type > Direct Link Connect** or **Resource type > Direct Link Dedicated** before selecting **Key Protect** as the Target service.
   {: important}

   You should grant access to all keys in the instance; otherwise, you must grant a new service-to-service authorization each time that you want to use a different key for Direct Link. As long as a key is in use by your gateway, you should never delete it, nor should you revoke the service-to-service authorization.

1. If the Key Protect or HPCS instance has a context-based restriction (CBR) rule, a Direct Link Service Reference must be added to the network zone of that rule. For instructions, see [How Direct Link integrates with context-based restrictions](/docs/dl?topic=dl-cbr&interface=cli#cbr-overview).

## Creating base64-encoded encryption keys
{: #create-encryption-keys}

This section describes how to base64 encode your key value for proper key creation. The following examples show you how to use utilities that are readily available on your operating system to receive the encoded key string.

   There are many tools you can use to base64 encode your key material. For example, to use OpenSSL to create and encode new or existing key material, see [Hyper Protect Crypto Services](/docs/hs-crypto?topic=hs-crypto-import-standard-keys#encode-key-material-standard-key) or [Key Protect](/docs/key-protect?topic=key-protect-import-standard-keys#how-to-encode-standard-key-material) documentation.
   {: note}

### Windows users
{: #md5-windows}

You can use Powershell to base64-encode your key material.

#### Key string input
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

#### Key file input
{: #md5-key-file-input}

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

### MacOS and Linux users
{: #md5-mac-linux}

You can use the `base64` utility available in the bash shell to base64-encode your key material.

#### Key string input
{: #md5-mac-linux-key-string-input}

To encode a raw string to its base64 value with `base64`, pipe the string as input to the utility. Use `printf` to avoid adding a newline character:

```bash
KEY_VALUE="abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789"
printf '%s' $KEY_VALUE | base64
```

Output: `YWJjZGVmMDEyMzQ1Njc4OWFiY2RlZjAxMjM0NTY3ODlhYmNkZWYwMTIzNDU2Nzg5YWJjZGVmMDEyMzQ1Njc4OQ==`

#### Key file input
{: #md5-mac-linux-key-file-input}

To encode a key string from a file to its base64 value, first get the file content, removing any new lines. Then, pipe this value to the `base64` utility. Again, use `printf` to avoid adding a newline character:

```bash
KEY_FILE="path/to/file/key.txt"
KEY_VALUE=$(tr -d '\n' < $KEY_FILE)
printf '%s' $KEY_VALUE | base64
```

Output: `YWJjZGVmMDEyMzQ1Njc4OWFiY2RlZjAxMjM0NTY3ODlhYmNkZWYwMTIzNDU2Nzg5YWJjZGVmMDEyMzQ1Njc4OQ==`

## Next step
{: #md5-next-step}

[Activate BGP MD5 authentication](/docs/dl?topic=dl-enable-disable-md5#dl-enable-md5)
