# Privacy Policy — DoseNova

**Last updated:** 27 September 2026
**Effective:** on the first public release of the app

DoseNova ("the app", "we", "us") is operated by **Vijaylaxmi Gurjar**,
Jaipur, Rajasthan, India. Contact: **dosenova01@gmail.com**.

---

## 1. Plain summary

- Your medicine data is stored **on your device first**. The app works fully
  offline.
- If you sign in, your data is **synced to your private Firebase account** so
  you can restore it on a new phone.
- **We do not sell your data. We never share health information with
  advertisers, insurers, employers or data brokers.**
- **Nobody else can see your medication information unless you invite them as
  a caregiver.** You choose who, and exactly what they can see, and you can
  remove them at any time — see § 3.1.
- **The app contains no advertising.** There are no ads, no ad SDKs and no
  advertising identifiers on any plan.
- You can permanently delete everything, on our servers and on your device,
  from **Profile → Delete account** — see [Account Deletion](ACCOUNT_DELETION.md).
  A copy of your data is available on request by email.

---

## 2. What we collect

### 2.1 Information you give us

| Data | Why | Where it is stored |
|---|---|---|
| Email address, name | To create and secure your account | Firebase Authentication |
| Password | To sign you in | Firebase Authentication (hashed; we never see it) |
| Phone number (optional) | Account recovery | Cloud Firestore |
| Medicine names, dosage, form, category, instructions, schedules | The core function of the app | Device (SQLite) + Cloud Firestore |
| Dose history (taken / skipped / missed, timestamps) | Adherence tracking and reports | Device (SQLite) + Cloud Firestore |
| Medicine photos | To help you identify the right medicine | Device + Firebase Storage |
| Family profile names, relationship, date of birth, blood group, allergies | To manage medicines for people you care for | Device + Cloud Firestore |
| Prescription images and PDFs | To keep your prescriptions with you | Device + Firebase Storage |
| Caregiver invitations you send — the invitee's **email address**, the permissions you chose and the alert timing | So the person you invite can find and accept the invitation | Device + Cloud Firestore |
| Caregiver access you have granted — the caregiver's account identifier, name and email address, your display name, the permissions and when access was granted or removed | So our servers can check, on every read, what that caregiver is allowed to see | Cloud Firestore |
| Missed-dose alert records — that one of your doses was missed and when, **never which medicine** | To notify caregivers you have allowed to be told | Device + Cloud Firestore |
| Stock counts | Refill alerts | Device + Cloud Firestore |
| Emergency medical profile — name, date of birth, blood group, emergency contacts, allergies, conditions, current medications, notes | To show responders what they need if you cannot tell them yourself | **Device only**, in encrypted storage (Android Keystore). Optional and off unless you turn it on; it is **not uploaded**, and switching it off erases it |
| Health report PDFs you export | Created by you, on your device, for you to share | **Device only.** We never receive them. Once you share one, where it goes is up to you |

### 2.2 Information collected automatically

| Data | Why | Processor |
|---|---|---|
| Device model, OS version, app version, language | Diagnostics and compatibility | Firebase Crashlytics / Analytics |
| Crash reports and stack traces | To fix defects | Firebase Crashlytics |
| Anonymous usage events (screens viewed, features used, counts) | To improve the app | Firebase Analytics |
| Push notification token | To deliver notifications | Firebase Cloud Messaging |
| Reminder-delivery diagnostics — whether alarms survived a restart, and device settings such as battery optimisation | To detect and repair reminders the system dropped | **Device only.** Counts and outcomes; it records no medicine or dose |
| Purchase receipts | To verify and restore your subscription | Google Play Billing |

### 2.3 What we deliberately do **not** collect

- We do not collect your **precise location**. Photo GPS metadata (EXIF) is
  **stripped before storage**.
- We do not collect your contacts, calendar, SMS, call logs or microphone.
- We do not send **any** health information to Firebase Analytics.
  Analytics events carry categories and counts only — never a medicine name,
  a person's name, or an individual's adherence record.
- We do not read your prescriptions for profiling.

---

## 3. Health data

Medicine names, dosages, schedules, adherence records and prescriptions are
**sensitive personal data**. We treat them accordingly:

- They are stored in **your own private area** of our database. Security rules
  make it technically impossible for another user to read them, **unless you
  invite that person as a caregiver**, and then only the parts you chose
  (§ 3.1).
- They are **encrypted in transit** (TLS) and **at rest** by Google Cloud.
- They are **never** used for advertising, never sold, and never shared with
  insurers, employers, pharmaceutical companies or data brokers.
- Our staff do not access your health data except where you explicitly ask us
  to for support, or where we are legally compelled.
- The app reads your schedule **on your device, in the background**, roughly
  twice a day, so that reminders keep being set even during long stretches when
  you never open the app. This runs entirely offline: it reads the local
  database and asks Android to hold the alarms. Nothing is uploaded by it, and
  no medicine name leaves your phone as part of it.

### 3.1 Sharing with a caregiver

Caregiver mode lets you give another person — a family member, a friend, a
nurse — **read-only** access to part of your medication information from their
own DoseNova account. It only ever starts with you.

**You choose who.** You invite someone by their email address. They must sign
in to DoseNova with that same, verified email address to accept, and they can
decline. An invitation expires after **14 days** if it is not accepted. Before
accepting, the invitee sees your display name if you have set one, and nothing
else about you.

**You choose what.** Each invitation carries the permissions you tick, and
nothing is granted by default:

| Permission | What the caregiver can then see |
|---|---|
| View medicines | Your medicines and their reminder schedules, and the names of family members you manage them for |
| View adherence | Your dose history (taken, skipped, missed), with the medicine and family-member names it refers to |
| View refill status | Your medicines, reminders and refill alerts — **not** family-member names |
| Missed-dose alerts | Nothing to read. It allows us to notify the caregiver when you miss a dose (below) |

A caregiver can **never** see your prescriptions or your emergency medical
profile, and can never change any of your records. These limits are enforced by
our servers on every read, not only by the app.

**Missed-dose alerts.** If you allow it, when a dose of yours has been missed
for longer than the time you set for that caregiver (between 30 minutes and
12 hours; 2 hours unless you change it), we send them a push notification
saying that **you missed a scheduled medication**, with your name and nothing
more — never the medicine, the dose or any other health detail. Alerts cover
only doses due after that caregiver was given access, are limited to a few per
day, and are withdrawn if you take the dose before the alert is sent. They are
raised for your own doses only, never for family members you manage.

**On the caregiver's device.** So that it works offline, the caregiver's app
keeps a copy of the summary they are allowed to see. It is removed when their
access ends and their app next checks, and a refused read is treated as the end
of access straight away.

**Removing access.** You can remove a caregiver, or narrow what they can see,
at any time from **Profile → Caregivers**. Our servers refuse their reads as
soon as the change reaches them — immediately when you are online, or as soon
as your phone reconnects. Deleting your account also ends every caregiver's
access, and if you are somebody's caregiver, deleting your account ends your
access to theirs.

**If you were invited.** If someone invites you as their caregiver, your email
address is stored in their account so that you can find the invitation, and
stays in that account's records until the account is deleted. It is used for
nothing else and never sent to you or anyone else by us. If you accept, your
name and email address are recorded on the access they granted you, so they
can see who has access.

---

## 4. Legal basis and your consent

Under India's **Digital Personal Data Protection Act, 2023**, we process your
personal data on the basis of the **consent** you give when you create an
account and when you grant each device permission. Sharing with a caregiver
rests on a separate, specific consent: the invitation you send, with the
permissions you chose. You may withdraw it at any time by removing that
caregiver, and all consent by deleting your account.

If you are in the EEA/UK, our lawful bases under **GDPR Art. 6/9** are your
explicit consent (Art. 9(2)(a)) for health data, and contractual necessity
(Art. 6(1)(b)) for account operation.

---

## 5. Who processes your data

We use these sub-processors:

| Processor | Purpose | Location |
|---|---|---|
| Google Firebase (Auth, Firestore, Storage, Messaging, Crashlytics, Analytics) | App backend | asia-south1 (Mumbai), India |
| Google Play Billing | Subscription payments | Global |

Caregivers are not processors. They are people **you** choose to share with,
and they see only what you allowed (§ 3.1). We share your data with no other
person or company.

Google's handling is governed by the
[Google Cloud Privacy Notice](https://cloud.google.com/terms/cloud-privacy-notice)
and the [Google Privacy Policy](https://policies.google.com/privacy).

Data is primarily stored in **India (asia-south1)**. Diagnostics services may
process data outside India under Google's standard contractual clauses.

---

## 6. How long we keep it

| Data | Retention |
|---|---|
| Account and medicine data | Until you delete your account |
| Dose history | Kept in full for the life of the account, including if your subscription lapses. Nothing is deleted until you delete your account. |
| Crash reports | 90 days. A crash report cannot be deleted individually; when you delete your account, your account identifier stops being attached to new reports and any report waiting on your device is discarded. |
| Analytics events tied to your account | Until you delete your account, then deleted at Google by request. Google completes the deletion within 72 hours. Events collected before you signed in carry no account identifier and expire after at most 14 months. |
| Caregiver invitations and access records | Until you delete your account. A removed caregiver's record is kept, marked as removed, so their access stays refused on every device |
| Missed-dose alert records | Until you delete your account |
| Backups | Up to 30 days after deletion, then permanently erased |

---

## 7. Your rights

You may:

- **Access and export** your data. The app itself exports a **health report
  PDF** of your medicines and dose history — Settings → Export report — which
  is generated on your device and shared wherever you choose. For a complete
  copy of everything held on your account, email us and we will send it within
  **30 days**.
- **Correct** any detail — edit it in the app.
- **Delete everything** — Profile → Delete account, or by email; the steps are
  in [Account Deletion](ACCOUNT_DELETION.md). This signs you out,
  removes your sign-in credentials and **wipes every trace from the device**.
  Your records held on our servers — medicines, dose history, prescriptions,
  family profiles, files and purchase records — are erased automatically, and
  in every case within **30 days**. At the same time we ask Google to delete
  the analytics data tied to your account, and your account identifier is
  removed from crash reporting; see § 6 for what Google retains and for how
  long.
- **Withdraw consent** by deleting your account, or by switching analytics off
  in Settings → Data & sync.
- **Opt out of analytics** — Settings → Data & sync. Nothing is collected until
  you switch it on.
- **Complain** to the Data Protection Board of India, or your local
  supervisory authority.

To exercise any right, email **dosenova01@gmail.com**. We respond within
**30 days**.

---

## 8. Children

DoseNova is **not intended for children under 18** as account holders.
An adult may create a *family profile* for a child they care for; that profile
is the adult's data and is governed by this policy. We do not knowingly create
accounts for children. If you believe a child has created an account, contact
us and we will remove it.

---

## 9. Security

- TLS 1.2+ for all network traffic.
- Encryption at rest via Google Cloud.
- **Per-user Firebase Security Rules**, so one account cannot read another's
  records — except a caregiver you invited, and then only the parts you chose.
  These are enforced on Google's servers, not in the app, and hold even
  against a modified client.
- Secrets the app must keep on the device are held in the **Android
  Keystore**, never in plain storage.
- Signing out **wipes all local data from the device**, so a shared phone does
  not leak one person's medicines to the next.

**On your device.** Anyone holding your unlocked phone can read your medicines,
and a dose reminder shows the medicine's name on your lock screen — that is
what makes the app useful in a hurry. Use your device's own screen lock, and
Android's per-app notification settings if you would rather reminders stayed
private.

No system is perfectly secure. If we become aware of a breach affecting your
personal data, we will notify you and the Data Protection Board of India as
required by law.

---

## 10. Advertising

**DoseNova shows no advertising.** The app contains no ad SDKs, requests no
ads, and does not read or transmit your advertising identifier. There is no
ad-supported plan.

---

## 11. Medical disclaimer

**DoseNova is not a medical device.** It does not diagnose, treat,
cure or prevent any disease, and it does not provide medical advice. It is a
reminder and record-keeping tool.

Notification delivery depends on your device and operating system, and can be
delayed or prevented by battery optimisation, Do Not Disturb, force-stopping
the app, or revoked permissions. **Do not rely on this app as your sole
safeguard for critical medication.** Always follow the instructions given by
your doctor or pharmacist.

---

## 12. Changes

We will post any change here and update the date above. Material changes will
be notified in the app before they take effect.

---

## 13. Contact

**Vijaylaxmi Gurjar**
Jaipur, Rajasthan, India
Email: **dosenova01@gmail.com**
Grievance Officer (DPDP Act, India): **Vijaylaxmi Gurjar**, **dosenova01@gmail.com**
