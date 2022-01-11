## PSQR CLI

The `psqr` command line interface is a NodeJS command line interface
to

### Install the PSQR Command
Install `psqr` globally via npm:

```
sudo npm i -g psqr
```

At this point, the `psqr` command is available. Check the version to ensure that
it executes properly.

```
psqr --version
```

### Create a Self-Hosted Identity
Virtual Public Squares operate on identities that expose human readable information
and public keys for cryptographic signature validation.These identities are tied
to the domain that hosts them and changing the location or key information is
disruptive, so plan ahead.

#### Preparation
Select the domain that will host your identity. Ideally, this is a domain you
control. If you have a WordPress site, use the WordPress plugin to host your new
identity.

Identify the URL that will host your identity. In the case of a WordPress user,
this is the URL of the user profile on the site. If you are creating an identity
for the site as a whole, only the domain is required.

You will also need the name of entity being identified. This can be an entire site,
an individual, or a publishing pseudonym. Additional optional information includes
a profile image URL, a tagline, primary URL, an email address, a phone number,
and a street address.

Note that the information used to create an identity is exposed to the public. Do
not include private information. The email, phone, and street address fields are
intended to promote businesses.

#### Create a New Identity
Convert the URL that will host your identity to PSQR DID format by replacing
the slashes with colons as below:

The specified Key IDentifier (`[KID]`) determines where this new identity must
be hosted and the name of the first key pair to be created. The files are
generated locally, and the DID document must be made available to the public at
the corresponding URL.

In practice, more information may be desired. Keep in mind that everything
specified here goes into the identity and is available to the public.

Example:
```bash
psqr identity:new 'did:psqr:bobbert.com/u/bob#publish' \
  --name "Bob Bobbert" \
  --image "https://bobbert.com/u/bob/profile.png" \
  --url "https://bobbert.com/u/bob" \
  --tagline "Hey I'm bob" \
  --email "bob@bobbert.com" \
  --phone "867-5309" \
  --address "111 Bobbert Street"
```
