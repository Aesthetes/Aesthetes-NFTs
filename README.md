# Aesthetes NFT standard
### This is how we mint NFTs on XRPL

We chose IPFS as the storing solution for our NFTs, ensuring the durability of your artwork through time. You could use any gateway to upload your artwork, but as Aesthetes we currently work with https://gateway.pinata.cloud so we suggest for you to use it as well.

* A JSON-formatted file containing the metadata of your artwork is required, its fields may contain the name of the token, the author and a description. Besides those, the metadata must also contain a referral to your artwork in a field called *image* (also videos can be referenced but it's called like that for compliance reasons). We don't use complete links, instead we use the CID of the content calculated according to IPFS standard, in order to be able to migrate your content without having to change the metadata or using backup links. Remember to prepend *hash:* to the CID of your artwork.
The structure of the fields is the one showed in the example.

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

* In case all your primary storage solutions go down, you can always restore to the Ripple network to retrieve the on-chain metadata for your artwork as suggested by the XLS-16d. This metadata is placed inside the Memo fields of a transaction referred to by a CTI (as proposed in XLS-15d), so read the documentation before proceding. The CTI is also used for certification purposes, so if you want to see that green check next to your artwork you better use this feature.
The structure of the fields is the one showed in the example.

```
Description: The Digital Artwork \"Elysian - Logo Unveil\" was created by Claudia Cimaglia after the choice of the Elysian Logo by the XRPCommunity. NFT minted on the XRPL by Aesthetes S.R.L. - Milan.
Author: Claudia Cimaglia
PrimaryUri: hash:QmZ5AXgQtNKGzAmjPMpkZGFeK6TFFLBrzF6XoyVCMmsXeS
```

* Also bithomp plays a role in our NFT game (for now), so we advise you to create a Gravatar account for each NFT in order to display an artwork-related image in the most popular XRP explorer (for now). This is done leveraging the EmailHash field of the NFT minting account.

### FUNDAMENTAL RULES
* **1000000000000000e-96 only**: only truly indivisible NFTs will be accepted, so be sure to issue only 1000000000000000e-96 coins for your NFT currency. Other values will not be accepted.
* **Always do blackholing**: you must blackhole the issuing account otherwise the Ripple community cannot be sure that another identical token will never be issued. NFTs coming from non-blackholed accounts will not be accepted.
