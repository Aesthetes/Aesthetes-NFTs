# Aesthetes NFT standard
### This is how we mint NFTs on XRPL

We chose IPFS as the storing solution for our NFTs, ensuring the durability of your artwork through time. You could use any gateway to upload your artwork, but as Aesthetes we currently work with https://gateway.pinata.cloud so we suggest for you to use it as well.

'
{
	"name":"ELSContest01",
	"description":"The Digital Artwork \"Elysian - Logo Contest nr. 04\" was created by Claudia Cimaglia for the Elsyian Logo Contest run on Twitter in the period 04th Aug - 03rd Sept 2021. NFT minted on the XRPL by Aesthetes S.R.L. - Milan.",
	"image":"hash:QmZ5AXgQtNKGzAmjPMpkZGFeK6TFFLBrzF6XoyVCMmsXeS",
	"properties": {
		"author":"Claudia Cimaglia"
	}
}
'

A JSON-formatted file containing the metadata of your artwork is required, its fields may contain the name of the token, the author and a description. Besides those, the metadata must also contain a referral to your artwork in a field called *image* (also videos can be referenced but it's called like that for compliance reasons). We don't use complete links, instead we use the CID of the content calculated according to IPFS standard, in order to be able to migrate your content without having to change the metadata or using backup links. Remember to prepend <i>hash:</i> to the CID of your artwork.
The structure of the fields is the one showed in the example.
