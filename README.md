# DoseNova — legal documents

The published privacy policy, terms and account-deletion instructions for the
**DoseNova** Android app. They live in their own public repository because
Google Play requires each of them at a public HTTPS URL that works without
signing in, and because a legal document should have a history you can read.

| Document | What it is for |
|---|---|
| [Privacy Policy](PRIVACY_POLICY.md) | What the app collects, why, who processes it, how long it is kept, and your rights over it. Required by Google Play for every app, and by the DPDP Act. |
| [Terms of Service](TERMS_OF_SERVICE.md) | The agreement between you and us: the medical disclaimer, subscriptions, acceptable use, liability. |
| [Account Deletion](ACCOUNT_DELETION.md) | How to delete your account and data, in the app or by email, and what happens to each kind of record. Google Play requires this at a URL of its own. |

## Where each URL goes

Once this repository is published (see below), each document has a stable
address. They are needed in three places:

| URL | Used by |
|---|---|
| Privacy Policy | Play Console → App content → Privacy policy; and the Data safety form |
| Terms of Service | Play Console → Store listing; and linked from the app |
| Account Deletion | Play Console → App content → Data deletion → "URL to request account deletion" |

The app links all three from **Settings → About** and from the registration
screen. They are passed to the build as `PRIVACY_POLICY_URL`, `TERMS_URL` and
`ACCOUNT_DELETION_URL`, so the links and these documents can never drift apart.

## Publishing

GitHub renders Markdown at a public URL already, so the file links above are
usable as they stand. For nicer pages at a shorter address, enable GitHub
Pages: **Settings → Pages → Source: deploy from branch → `dosenova` / root**.
The documents are then served at `https://gurjarvikram.github.io/dosenova-legal/`.

Whichever you choose, check that each URL opens in a private browser window
before entering it in Play Console. Play rejects a privacy policy URL that is
missing, broken, or behind a login.

## Before these are relied upon

These documents were drafted alongside the app, so they describe what it
actually does rather than a template's guesses. The operator is
**Vijaylaxmi Gurjar**, Jaipur, Rajasthan, India, contactable at
**dosenova01@gmail.com**, who is also the grievance officer named under the
DPDP Act. Courts at Jaipur have jurisdiction under the terms.

Three things still need attention before these are relied on:

1. **Have a lawyer review them** — one qualified in Indian data-protection law
   (DPDP Act 2023), and in GDPR as well if you serve users in the EU or UK. A
   privacy policy is a binding public representation, not marketing copy.
2. **Consider a full postal address.** These documents give the operator's city
   rather than a street address. That is common for an individual developer,
   but the DPDP Act expects a contact a data principal can reach, and some
   jurisdictions expect a postal address on a privacy notice.
3. **Deploy the backend before publishing.** The deletion these documents
   promise is carried out by a Cloud Function that erases the account's server
   records and files the analytics deletion request. Publish these pages when
   that function is live, not before — a promise the backend cannot yet keep is
   the one thing worse than no page at all.

The app links these documents by URL, passed to the build as
`PRIVACY_POLICY_URL`, `TERMS_URL` and `ACCOUNT_DELETION_URL`. If the contact
address changes, change it here and in those defines together.

## Changing them

Edit the document, update its **Last updated** date, and commit. Material
changes must also be notified in the app before they take effect, which is what
both documents promise.
