---
title: Lightsats API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

toc_footers:
  - <a href='https://lightsats.com' target="_blank">Create A Lightsats account</a>
  - <a href='https://github.com/lightsats/lightsats/issues' target="_blank">Report an issue</a>
  - <a href='https://github.com/slatedocs/slate' target="_blank">Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Lightsats API
---

# Introduction

Welcome to the Lightsats API! You can use our API to access Lightsats API endpoints to automate the management of Lightsats tips.

# Authentication

Lightsats uses API keys to allow access to the API. You can register a new Lightsats API key in you [Lightsats Profile](http://lightsats.com/profile).

Lightsats expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer your_lightsats_api_token`

<aside class="notice">
You must replace <code>your_lightsats_api_token</code> with your personal API key.
</aside>

# Tipper Tips

Endpoints for managing tips you have created as a tipper.

## Get all Tips

```shell
curl "https://lightsats.com/api/tipper/tips" \
  -H "Authorization: Bearer your_lightsats_api_token"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "clfw7rh1p000slo8n4j0kyrik",
        "amount": 1,
        "fee": 10,
        "tipperId": "cla56o9pr0000lo0jb71mkc3p",
        "tippeeId": "claauuz5z0001lo4rcr0t9j0s",
        "tippeeName": "Bob",
        "tippeeLocale": "th",
        "invoice": "lnbc....",
        "invoiceId": "f8ea6b72d7b....",
        "preparationInvoice": "lnbc110....",
        "preparationInvoiceId": "1fd492...",
        "status": "CLAIMED",
        "created": "2023-03-31T07:18:57.803Z",
        "updated": "2023-03-31T07:19:52.046Z",
        "claimed": "2023-01-21T05:25:37.261Z",
        "expiry": "2023-04-21T07:18:57.784Z",
        "copiedClaimUrl": "2023-01-13T08:08:43.998Z",
        "currency": "USD",
        "note": "Thank you for the amazing meal",
        "version": 1,
        "withdrawalId": "clcvpy3h20...",
        "numSmsTokens": 3,
        "onboardingFlow": "DEFAULT",
        "lastWithdrawal": "2023-03-31T07:19:13.109Z",
        "groupId": "clfw7rh1o000olo8n5qrqjc6e",
        "groupTipIndex": 3,
        "claimedFromPrintedCard": false,
        "recommendedWalletId": "wos",
        "anonymousTipper": false,
        "passphrase": "execute aerobic clock",
        "claimWebhookUrl": "https://discord.com/api/webhooks/..."
    },
    // ... more tips
]
```

This endpoint gets created tips.

### HTTP Request

`GET https://lightsats.com/api/tipper/tips`

## Get a single Tip

```shell
curl "https://lightsats.com/api/tipper/tips/clfw7rh1p000slo8n4j0kyrik" \
  -H "Authorization: Bearer your_lightsats_api_token"
```


> The above command returns JSON structured like this:

```json
{
    "id": "clfw7rh1p000slo8n4j0kyrik",
    "amount": 1,
    "fee": 10,
    "tipperId": "cla56o9pr0000lo0jb71mkc3p",
    "tippeeId": "claauuz5z0001lo4rcr0t9j0s",
    "tippeeName": "Bob",
    "tippeeLocale": "th",
    "invoice": "lnbc....",
    "invoiceId": "f8ea6b72d7b....",
    "preparationInvoice": "lnbc110....",
    "preparationInvoiceId": "1fd492...",
    "status": "CLAIMED",
    "created": "2023-03-31T07:18:57.803Z",
    "updated": "2023-03-31T07:19:52.046Z",
    "claimed": "2023-01-21T05:25:37.261Z",
    "expiry": "2023-04-21T07:18:57.784Z",
    "copiedClaimUrl": "2023-01-13T08:08:43.998Z",
    "currency": "USD",
    "note": "Thank you for the amazing meal",
    "version": 1,
    "withdrawalId": "clcvpy3h20...",
    "numSmsTokens": 3,
    "onboardingFlow": "DEFAULT",
    "lastWithdrawal": "2023-03-31T07:19:13.109Z",
    "groupId": "clfw7rh1o000olo8n5qrqjc6e",
    "groupTipIndex": 3,
    "claimedFromPrintedCard": false,
    "recommendedWalletId": "wos",
    "anonymousTipper": false,
    "passphrase": "execute aerobic clock",
    "claimWebhookUrl": "https://discord.com/api/webhooks/..."
}
```

This endpoint retrieves a specific tip.

### HTTP Request

`GET https://lightsats.com/api/tipper/tips/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the tip to retrieve

## Create a Tip / Tip Group

```shell
curl --location --request POST 'https://lightsats.com/api/tipper/tips' \
--header 'Authorization: Bearer your_lightsats_api_token' \
--header 'Content-Type: application/json' \
--data-raw '{
  "expiry": "2024-01-21T08:28:48.518Z",
  "amount": 21,
  "quantity": 1
}'
```


> When providing a quantity of 1, the above command returns JSON structured like this:

```json
{
    "id": "clgccm1nz000nlo8l3atu5599",
    "amount": 21,
    "fee": 10,
    "tipperId": "cla56o9pr0000lo0jb71mkc3p",
    "tippeeId": null,
    "tippeeName": null,
    "tippeeLocale": null,
    "invoice": "lnbc310n1pjr2mrkpp5ghppr0aul08kxrn9x6e5cq7sa9yrp2z6x8vtr6j83yklec0jntkqdq4f35kw6r5wdshgueqw35hqcqzpgxqyz5vqsp585s7qv2x3a87u06eaf9v3gkchpgtueherw4qfuj3c32nh2d9l8yq9qyyssq5vpt4psr2msfqm2j2gszn4r7wf578glnexne5gyleqp3jemnmvy3kkd50p28sl29p6rc0slhe2a73m83y0eqq82zts3qgsng6jt87kqpl0qnnq",
    "invoiceId": "45c211bfbcfbcf630e6536b34c03d0e94830a85a31d8b1ea47892dfce1f29aec",
    "preparationInvoice": null,
    "preparationInvoiceId": null,
    "status": "UNFUNDED",
    "created": "2023-04-11T14:19:01.487Z",
    "updated": "2023-04-11T14:19:06.279Z",
    "claimed": null,
    "expiry": "2024-01-21T08:28:48.518Z",
    "copiedClaimUrl": null,
    "currency": null,
    "note": null,
    "version": 1,
    "withdrawalId": null,
    "numSmsTokens": 0,
    "onboardingFlow": "DEFAULT",
    "lastWithdrawal": null,
    "groupId": null,
    "groupTipIndex": null,
    "claimedFromPrintedCard": false,
    "recommendedWalletId": null,
    "anonymousTipper": false,
    "passphrase": null,
    "claimWebhookUrl": null
}
```

> When providing a quantity greater than 1, the above command returns JSON structured like this:

```json
{
    "id": "clgcda8fu000qlo8llc1v36mp",
    "created": "2023-04-11T14:37:50.010Z",
    "updated": "2023-04-11T14:37:53.190Z",
    "status": "UNFUNDED",
    "name": null,
    "quantity": 2,
    "tipperId": "cla56o9pr0000lo0jb71mkc3p",
    "invoice": "lnbc620n1pjr2uxapp5ulw7z2pmflxa2uncr5aqps6e4w7yvvpl3kg6zgmetzl2h0q3acrqdq4f35kw6r5wdshgueqw35hqcqzpgxqyz5vqsp5wccm3fw73hhes83p0d8wfgc5whywk6spgt9ecxevnlqrx25r0wcq9qyyssqmgkeyl94gxs8r4y54hxg7227jpa9qtgj9qczyg9s8feasw66vp8rzhl7xmy5jvhqpd9r24z7zffxnlmq29mgrwgk5rn0zwx9erf4keqp2sqqhh",
    "invoiceId": "e7dde1283b4fcdd572781d3a00c359abbc46303f8d91a1237958beabbc11ee06",
    "tips": [
        {
            "id": "clgcda8fu000rlo8llou18pbg",
            "amount": 21,
            "fee": 10,
            "tipperId": "cla56o9pr0000lo0jb71mkc3p",
            "tippeeId": null,
            "tippeeName": null,
            "tippeeLocale": null,
            "invoice": null,
            "invoiceId": null,
            "preparationInvoice": null,
            "preparationInvoiceId": null,
            "status": "UNFUNDED",
            "created": "2023-04-11T14:37:50.010Z",
            "updated": "2023-04-11T14:37:50.010Z",
            "claimed": null,
            "expiry": "2024-01-21T08:28:48.518Z",
            "copiedClaimUrl": null,
            "currency": null,
            "note": null,
            "version": 1,
            "withdrawalId": null,
            "numSmsTokens": 0,
            "onboardingFlow": "DEFAULT",
            "lastWithdrawal": null,
            "groupId": "clgcda8fu000qlo8llc1v36mp",
            "groupTipIndex": 0,
            "claimedFromPrintedCard": false,
            "recommendedWalletId": null,
            "anonymousTipper": false,
            "passphrase": null,
            "claimWebhookUrl": null
        },
        {
            "id": "clgcda8fu000slo8limy2cqyb",
            "amount": 21,
            "fee": 10,
            "tipperId": "cla56o9pr0000lo0jb71mkc3p",
            "tippeeId": null,
            "tippeeName": null,
            "tippeeLocale": null,
            "invoice": null,
            "invoiceId": null,
            "preparationInvoice": null,
            "preparationInvoiceId": null,
            "status": "UNFUNDED",
            "created": "2023-04-11T14:37:50.010Z",
            "updated": "2023-04-11T14:37:50.010Z",
            "claimed": null,
            "expiry": "2024-01-21T08:28:48.518Z",
            "copiedClaimUrl": null,
            "currency": null,
            "note": null,
            "version": 1,
            "withdrawalId": null,
            "numSmsTokens": 0,
            "onboardingFlow": "DEFAULT",
            "lastWithdrawal": null,
            "groupId": "clgcda8fu000qlo8llc1v36mp",
            "groupTipIndex": 1,
            "claimedFromPrintedCard": false,
            "recommendedWalletId": null,
            "anonymousTipper": false,
            "passphrase": null,
            "claimWebhookUrl": null
        }
    ]
}
```

This endpoint creates a tip or tip group.

### HTTP Request

`POST https://lightsats.com/api/tipper/tips`

### Parameters

Parameters marked * are required.

Parameter | Example  | Description
--------- | ----------- | -----------
amount* | 21 | The value of the tip in sats (not including fees)
quantity* | 1 | The amount of tips to create. A group will be created if the quantity is greater than 1.
expiry* | "2023-04-21T08:28:48.518Z" | After this date your tip can no longer be claimed or withdrawn, and the funds will be returned to you
currency | "USD" | The fiat currency your tippee uses
onboardingFlow | "DEFAULT" | "DEFAULT", "SKIP", or "LIGHTNING". Skip instantly shows LNURLw code. Lightning guides user to get a wallet and then login with lnurl-auth
tippeeName | "Bob" | The name of the recipient
tippeeLocale | "th" | Locale code for translations shown to the tippee. If not provided, the language will be guessed from the user's browser settings
note | "Thanks for the great pizza!" | A note to the tippee, shown when they claim the tip
tippeeNames | ["Name 1", "Name 2"] | Specify names of each tippee, if creating a tip group
recommendedWalletId | "alby" | Always show a specific wallet at the top of the list. See app/lib/items/wallets.ts
anonymousTipper | false | If true, do not reveal your profile to the recipient.
generatePassphrase | false | If true, generate a 3-word magic passphrase a user can use to redeem at https://lightsats.com/tip
claimWebhookUrl | "https://discord.com/api/webhooks/..." | Fire a webhook when the tip gets claimed. Only works for onboardingFlow of "DEFAULT" and "LIGHTNING"

## Funding Tips

Each created tip or tip group has an "invoice" field containing the funding invoice. This must be paid with a lightning wallet. You can do this programmatically using any wallet API such as [lnbits](https://legend.lnbits.com/docs#/default/api_payments_create_api_v1_payments_post) or the [Alby LndHub API](https://guides.getalby.com/lndhub-api/introduction/what-is-lndhub).

Once the tip invoice has been paid, the tip must be polled (using a GET request) for its status to be updated from "UNFUNDED" to "UNSEEN".

Only tips that then get viewed (status updated to "SEEN") can be claimed.

<aside class="warning">Tip groups must be polled (using a GET request) until each tip within the tip group has been updated to "UNSEEN". </aside>


## Delete a Tip

```shell
curl "https://lightsats.com/api/tipper/tips/clfw7rh1p000slo8n4j0kyrik" \
  -X DELETE \
  -H "Authorization: Bearer your_lightsats_api_token"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific tip.

<aside class="warning">Only unfunded tips can be deleted.</aside>

### HTTP Request

`DELETE https://lightsats.com/api/tipper/tips/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the tip to delete

## Update a single Tip
Coming soon


# Tip Groups

## Get a Tip Group

```shell
curl "https://lightsats.com/api/tipGroups/clfw7rh1o000olo8n5qrqjc6e" \
  -H "Authorization: Bearer your_lightsats_api_token"
```


> The above command returns JSON structured like this:

```json
{
    "id": "clgcda8fu000qlo8llc1v36mp",
    "created": "2023-04-11T14:37:50.010Z",
    "updated": "2023-04-11T14:37:53.190Z",
    "status": "UNFUNDED",
    "name": null,
    "quantity": 2,
    "tipperId": "cla56o9pr0000lo0jb71mkc3p",
    "invoice": "lnbc620n1pjr2uxapp5ulw7z2pmflxa2uncr5aqps6e4w7yvvpl3kg6zgmetzl2h0q3acrqdq4f35kw6r5wdshgueqw35hqcqzpgxqyz5vqsp5wccm3fw73hhes83p0d8wfgc5whywk6spgt9ecxevnlqrx25r0wcq9qyyssqmgkeyl94gxs8r4y54hxg7227jpa9qtgj9qczyg9s8feasw66vp8rzhl7xmy5jvhqpd9r24z7zffxnlmq29mgrwgk5rn0zwx9erf4keqp2sqqhh",
    "invoiceId": "e7dde1283b4fcdd572781d3a00c359abbc46303f8d91a1237958beabbc11ee06",
    "tips": [
        {
            "id": "clgcda8fu000rlo8llou18pbg",
            "amount": 21,
            "fee": 10,
            "tipperId": "cla56o9pr0000lo0jb71mkc3p",
            "tippeeId": null,
            "tippeeName": null,
            "tippeeLocale": null,
            "invoice": null,
            "invoiceId": null,
            "preparationInvoice": null,
            "preparationInvoiceId": null,
            "status": "UNFUNDED",
            "created": "2023-04-11T14:37:50.010Z",
            "updated": "2023-04-11T14:37:50.010Z",
            "claimed": null,
            "expiry": "2024-01-21T08:28:48.518Z",
            "copiedClaimUrl": null,
            "currency": null,
            "note": null,
            "version": 1,
            "withdrawalId": null,
            "numSmsTokens": 0,
            "onboardingFlow": "DEFAULT",
            "lastWithdrawal": null,
            "groupId": "clgcda8fu000qlo8llc1v36mp",
            "groupTipIndex": 0,
            "claimedFromPrintedCard": false,
            "recommendedWalletId": null,
            "anonymousTipper": false,
            "passphrase": null,
            "claimWebhookUrl": null
        },
        {
            "id": "clgcda8fu000slo8limy2cqyb",
            "amount": 21,
            "fee": 10,
            "tipperId": "cla56o9pr0000lo0jb71mkc3p",
            "tippeeId": null,
            "tippeeName": null,
            "tippeeLocale": null,
            "invoice": null,
            "invoiceId": null,
            "preparationInvoice": null,
            "preparationInvoiceId": null,
            "status": "UNFUNDED",
            "created": "2023-04-11T14:37:50.010Z",
            "updated": "2023-04-11T14:37:50.010Z",
            "claimed": null,
            "expiry": "2024-01-21T08:28:48.518Z",
            "copiedClaimUrl": null,
            "currency": null,
            "note": null,
            "version": 1,
            "withdrawalId": null,
            "numSmsTokens": 0,
            "onboardingFlow": "DEFAULT",
            "lastWithdrawal": null,
            "groupId": "clgcda8fu000qlo8llc1v36mp",
            "groupTipIndex": 1,
            "claimedFromPrintedCard": false,
            "recommendedWalletId": null,
            "anonymousTipper": false,
            "passphrase": null,
            "claimWebhookUrl": null
        }
    ]
}
```

This endpoint retrieves a tip group.

### HTTP Request

`GET https://lightsats.com/api/tipGroups/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the tip group to retrieve

## Update all Tips in a Tip group 
Coming soon

## Delete a Tip Group

```shell
curl "https://lightsats.com/api/tipGroups/clfw7rh1p000slo8n4j0kyrik" \
  -X DELETE \
  -H "Authorization: Bearer your_lightsats_api_token"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific tip group and all its tips.

<aside class="warning">Only unfunded tip groups can be deleted.</aside>

### HTTP Request

`DELETE https://lightsats.com/api/tipGroups/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the tip group to delete

# Tippee Tips

Coming soon.
