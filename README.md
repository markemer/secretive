# Secretive

Secretive is an app for storing and managing SSH keys in the Secure Enclave. It is inspired by the [sekey project](https://github.com/sekey/sekey), but rewritten in Swift with no external dependencies and with a handy native management app.

<img src="/.github/readme/app.png" alt="Screenshot of Secretive" width="600">

## Why?

### Safer Storage

The most common setup for SSH keys is just keeping them on disk, guarded by proper permissions. This is fine in most cases, but it's not super hard for malicious users or malware to copy your private key. If you store your keys in the Secure Enclave, it's impossible to export them, by design.

### Access Control

If your Mac has a Secure Enclave, it also has support for strong biometric access controls like Touch ID. You can configure your key so that they require Touch ID (or Watch) authentication before they're accessed.

<img src="/.github/readme/touchid.png" alt="Screenshot of Secretive authenticating with Touch ID">

### Notifications

Secretive also notifies you whenever your keys are acceessed, so you're never caught off guard.

<img src="/.github/readme/notification.png" alt="Screenshot of Secretive notifying the user">

### Support for Smart Cards Too!

For Macs without Secure Enclaves, you can configure a Smart Card (such as a YubiKey) and use it for signing as well.

## Getting Started

### Security Considerations

For the moment, you must build Secretive from source. For an app like this, it's critical that you trust that the app you're running is the app whose source you've checked out. To this end, Secretive has no third party dependecies, and is designed to be easy for you to audit for exploits.

### A Note Around Code Signing and Keychains

While Secretive uses the Secure Enclave for key storage, it still relies on Keychain APIs to access them. Keychain restricts reads of keys to the app (and specifically, the bundle ID) that created them. If you build Secretive from source, make sure you are consistent in which bundle ID you use so that the Keychain is able to locate your keys.

### Backups and Transfers to New Machines

Beacuse secrets in the Secure Enclave are not exportable, they are not able to be backed up, and you will not be able to transfer them to a new machine. If you get a new Mac, just create a new set of secrets specific to that Mac.
