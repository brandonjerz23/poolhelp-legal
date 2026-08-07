# PoolHelp Privacy Policy

**Last updated: August 5, 2026**

PoolHelp is built to be private by default. This policy explains, in plain English, what data the app handles and what it does not.

## The short version

- PoolHelp does **not** require an account. You can create one, but it is optional and used only for backup and sync.
- By default, all of your pool data stays **on your device**. We do not collect it, sync it to a cloud, or keep copies of it unless you create an account and sign in; see "Optional account and sync" below.
- We do **not** use analytics, tracking, advertising, or third-party marketing SDKs.
- Beyond optional sync, the only data that leaves your device is the content of a request when **you** use an optional AI feature: your question and a summary of your pool, and/or the photo you selected. That content is sent to PoolHelp's AI server, which passes it to Anthropic to generate the response. Neither stores your pool data; see "The optional AI features" below.

## What data the app stores on your device

When you use PoolHelp, the app saves information locally on your phone or tablet so it can work offline. This is stored using your device's standard app storage (AsyncStorage) and includes:

- Pools you create (name, size in gallons, surface/type, and similar details you enter)
- Water test logs (readings you record such as pH, chlorine, alkalinity, and dates)
- Chemical/dosing logs (products and amounts you record adding)
- Reminders you set
- Chat history and any diagnoses generated in the app
- Your app settings (such as theme preference)

Unless you create an account and sign in, this data lives **only on your device**. It is not uploaded to us in the background, and we keep no copy of it. If you do sign in, some of it syncs as described in the next section.

## Optional account and sync

You can create an optional PoolHelp account (email address and password) to back up your pool data and sync it across devices. The app is fully functional without one, and in builds where no sync backend is configured, accounts are not available at all.

While you are signed in, the app syncs four kinds of data to our database (a Supabase Postgres project operated by us): your pools, water test logs, chemical/dosing logs, and reminders. Chat history and diagnosis history are never synced; they stay on your device.

- Synced records are tied to your account id, and row-level security in the database isolates each account's records from every other account's.
- Sync traffic is encrypted in transit (HTTPS). Your email address is held by the authentication system to operate your account.
- **Signing out** stops syncing and keeps your local data on your device.
- **Reset all data** in Settings, used while signed in, also removes the synced content: deletions propagate to the database (as deletion markers) and to your other signed-in devices.
- **Delete account** on the Account screen permanently removes your account and every synced record from our servers. Data on your device stays until you reset the app. You can also ask us at **support@poolhelp.app** and we will remove them for you.

## The optional AI features

PoolHelp's core features (test logging, dosing math, reminders, charts) run entirely on your device and send nothing off it.

The AI features are optional: the chat assistant, photo diagnosis, and test-strip scanning. When you use one, the app sends only the content needed to answer that request, over an encrypted connection (HTTPS), to PoolHelp's AI server:

- For chat questions, that is your question plus a summary of your pool: the profile details you entered (which can include the pool's name and a location if you added one), recent test readings, and recent chemical additions.
- For photo features, that is the photo you take or select, plus the same kind of pool summary where relevant.

The AI server is a small relay we operate (a Cloudflare Worker). It forwards your request to Anthropic's API and returns the response to the app. It is a pass-through: it does not store the content of requests or responses. Anthropic processes the content to generate the response under its commercial API terms; by default, Anthropic does not use API inputs or outputs to train its models. Anthropic's handling of the data is governed by its own terms and privacy policy.

If the AI service is not configured or cannot be reached, the app runs these features in an on-device demo mode and nothing leaves your device.

## Subscriptions and purchases

The AI features are unlocked by an optional subscription ("PoolHelp AI"). Payment itself is handled entirely by Apple through your App Store account — we never see or store your name, card details, or billing address.

To know whether your subscription is active, the app uses RevenueCat, a subscription-infrastructure service. RevenueCat receives purchase receipt information from Apple together with a random identifier for your app installation (and, if you created an optional PoolHelp account, your account id so the subscription can follow you across devices). RevenueCat does not receive your pool data, photos, questions, or anything else about how you use the app. When the app talks to our AI server, it includes that same random identifier so the server can confirm the subscription is active; the server checks it against RevenueCat and does not build any usage profile. RevenueCat's handling of this data is governed by its own privacy policy at revenuecat.com/privacy.

You can manage or cancel the subscription any time in your App Store settings. Cancelling stops future charges; nothing about your pool data changes.

## Camera and photo library

PoolHelp requests camera and photo-library access only so you can pick or take an image for the AI photo features. Images are used to build that single request as described above and are not otherwise collected or stored by us. The app does not browse or upload your photo library in the background.

## Reminders and notifications

Reminders use local notifications scheduled on your device. No notification data is sent anywhere.

## Children's privacy

PoolHelp is a general-audience app for pool owners. It is not directed at children and does not knowingly collect data from children.

## Your control over your data

- By default, all app data is stored locally, so **you** hold it.
- You can remove everything at any time using **Reset all data** in Settings. If you are signed in, this also removes your synced data.
- **Uninstalling PoolHelp deletes all of its local data** from your device. Uninstalling does not delete data you have synced to an account; use Reset all data first while signed in, or contact support.
- AI features send data only when you use them. If you never use an AI feature and never sign in, nothing leaves your device.

## Changes to this policy

If we change how the app handles data, we will update this policy and its "Last updated" date, and update the copy shown inside the app to match.

## Contact

Questions about privacy? Contact us at **support@poolhelp.app**.
