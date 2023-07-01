# Unpack `disc`

Disc file is actually a password encrypted zip file (ZipCrypto encryption).

Because we don't know the password yet, we will use [**bkcrack**](https://github.com/kimci86/bkcrack/) to unpack the `disc` file.

## Find zip key

Use `bkcrack` to find zip key.

**TLDR**: the key is `34b8693b e785fb33 af93b36c`

## Change disc password

Use `bkcrack` to change password using this command:

```bash
bkcrack -C disc -k 34b8693b e785fb33 af93b36c -U new-disc.zip newpassword 
```

then extract **new-disc.zip** using the new password that we have set, in this example **"new-password"** and of course without those quotes.
