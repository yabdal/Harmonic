# 🎵 Harmony: Music Royalty Collective Contract

**Harmony** is a Clarity-based smart contract that enables **fractional ownership of songs**, **automated royalty distribution**, and **community-driven marketing campaigns** on the Stacks blockchain. It is designed for artists, fans, and promoters to collaborate and profit from music streaming in a decentralized and transparent way.

---

## 🚀 Features

* **Song Tokenization:** Register songs with a fixed supply of ownership tokens.
* **Fan Investment:** Fans buy tokens to become co-owners and earn royalties.
* **Automated Royalties:** Distributes monthly streaming royalties based on token ownership.
* **Decentralized Campaigns:** Fans create and vote on marketing campaigns to boost songs.
* **Tamper-Proof Voting:** Fans use their token-weighted votes to support or oppose campaigns.
* **Quarterly Claims:** Fans claim their earnings for each royalty quarter.

---

## 🛠 Contract Functions

### 🔊 Public Functions

* `register-song(...)`
  Register a new song with metadata, token supply, and royalty configuration. Only callable by the record label.

* `buy-fan-tokens(track-id, token-amount)`
  Fans purchase fractional ownership of a song by buying tokens.

* `distribute-royalties(track-id, quarter)`
  Trigger royalty distribution for a track. Only the lead musician can initiate.

* `claim-royalties(track-id, quarter)`
  Fans claim their share of royalties for a given quarter.

* `create-campaign(track-id, campaign-name, strategy, duration)`
  Fans propose a promotional campaign for a song.

* `support-campaign(campaign-id, in-favor)`
  Fans vote for or against a campaign using their token weight.

---

### 🔍 Read-Only Functions

* `get-song(track-id)`
  Returns song metadata.

* `get-fan-tokens(track-id, fan)`
  Returns number of tokens a fan owns for a specific song.

* `get-campaign(campaign-id)`
  Returns campaign details.

* `calculate-royalty-share(track-id, fan)`
  Calculates the fan's share of royalties.

---

## 🧱 Data Structures

* **hit-songs:** Maps song IDs to metadata and royalty settings.
* **fan-tokens:** Tracks token ownership by song and fan.
* **marketing-campaigns:** Campaign metadata for promotion proposals.
* **campaign-support:** Voting records of fans per campaign.
* **royalty-claims:** Tracks whether a fan has claimed royalties for a given period.

---

## 🔐 Access Control

* Only the `RECORD_LABEL` (set to `tx-sender` during deployment) can register new songs.
* Only the **lead musician** can distribute royalties for their tracks.

---

## ⚠️ Errors

| Code | Description                |
| ---- | -------------------------- |
| 300  | Unauthorized access        |
| 301  | Insufficient tokens        |
| 302  | Track not found            |
| 303  | Invalid amount             |
| 304  | Campaign not found         |
| 305  | Already supported campaign |

---

## 📈 Example Flow

1. Record label registers a song with token supply and royalties.
2. Fans buy tokens to become fractional owners.
3. Lead musician distributes royalties monthly or quarterly.
4. Fans claim royalties through `claim-royalties`.
5. Token-holding fans launch and vote on campaigns.
6. Campaign success is determined by token-weighted votes.

---

## 🧪 Development & Testing

Test the contract on the Stacks testnet using Clarinet:
