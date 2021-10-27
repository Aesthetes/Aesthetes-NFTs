# Aesthetes NFTs
### This is how we mint NFTs on XRPL

We chose IPFS as the storing solution for our NFTs, ensuring the durability of your artwork through time. You could use any gateway to upload your artwork, but as Aesthetes we currently work with https://gateway.pinata.cloud so we suggest for you to use it as well.

A JSON-formatted file containing the metadata of your artwork is required, its fields may contain the name of the token, the author and a description. 
Besides those, the metadata must also contain a referral to your artwork in a field called *image* (also videos can be referenced but it's called like that for compliance reasons).
We don't use complete links, instead we use the CID of the content calculated according to IPFS standard, in order to be able to migrate your content without having to change the metadata or using backup links. Remember to prepend *hash:* to the CID of your artwork.
The structure of the fields is the one showed in the [example below](https://gateway.pinata.cloud/ipfs/QmaULakAx6jUYFHvV8RcSY4kKuYJGY21L6JjNUkAAFJ2aN "NFT metadata.json").

```json
{
	"name":"ELSContest01",
	"description":"The Digital Artwork \"Elysian - Logo Contest nr. 04\" was created by Claudia Cimaglia for the Elsyian Logo Contest run on Twitter in the period 04th Aug - 03rd Sept 2021. NFT minted on the XRPL by Aesthetes S.R.L. - Milan.",
	"image":"hash:QmZ5AXgQtNKGzAmjPMpkZGFeK6TFFLBrzF6XoyVCMmsXeS",
	"properties": {
		"author":"Claudia Cimaglia"
	}
}
```
Of course, the metadata.json file is uploaded on IPFS as well and its CID is placed inside the *Domain* setting of the NFT minting account (as proposed by XLS-14d). Again, remember to prepend *hash:* to the CID of the metadata file.

<p align="center">
  <img src="https://user-images.githubusercontent.com/91289434/138886096-c95dc135-4780-4e5c-a8d9-bae62f7d1899.png">
</p>

In case all your primary storage solutions go down, you can always restore to the Ripple network to retrieve the on-chain metadata for your artwork. 
This metadata is placed inside the Memo fields of a transaction referred to by a CTI that is inserted inside the currency identifier of the NFT (as proposed by XLS-16d). Therefore, the currency code for an NFT consists of 3 parts: 
* Prefix 02 for HEX currency code.
* CTI (Concise Transaction Identifier).
* Short name converted to HEX for the NFT to a maximum of 12 characters or less (filled up with 0's if it's less).

The CTI is also used for certification purposes, so if you want to see that green check next to your artwork you better use this feature.
The structure of the on-chain metadata fields is the one showed in the [example below](https://bithomp.com/explorer/80668339B5A79B68858F5AB63D011016E3644AC91818FD1A5744CBB3C8FCE848 "NFT on-chain metadata"), the artwork's CID is placed under the *PrimaryUri* field.

<p align="center">
  <img src="https://user-images.githubusercontent.com/91289434/138886009-475b164b-4e6d-4049-b966-3398e9cfdbbe.png">
</p>

Also bithomp plays an important role, so we advise you to create a Gravatar account for each NFT in order to display an artwork-related image (or a QR Code  directly routing to the related NFT page on xrplnft.art page - as sometimes we use like in the example above). 
This is done by leveraging the EmailHash field of the [NFT minting account](https://bithomp.com/explorer/rrsDg7S7e7FPLJRLy3DXrzTSHYBfTeepm9 "NFT minting account").

### FUNDAMENTAL RULES
* **1000000000000000e-96 only**: only truly indivisible NFTs will be accepted, so be sure to issue only 1000000000000000e-96 coins for your NFT currency. Other values will not be accepted.
* **Always do blackholing**: you must blackhole the issuing account otherwise the Ripple community cannot be sure that another identical token will never be issued. NFTs coming from non-blackholed accounts will not be accepted.

### HOW TO SETUP THE TRUSTLINE PROPERLY
If you want send a NFTs from a wallet to another one, you should set the Trustline toward the NFT Issuer Address. In order to set it correctly we suggest to use related page on our NFTs Visualizer  https://xrplnft.art. 
