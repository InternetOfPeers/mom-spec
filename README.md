# MOM v1 Specification

See [ERCXXX](#) (_it will be submitted soon_).

## Valid MOM transaction's structure

| ATTRIBUTE | VALUE |
|:--------|:------------|
| `from` | `MUST` be the tx signer |
| `to` | `MUST` be the tx signer |
| `value` |  `MUST` be 0 wei |
| `data` | `MUST` be at least 1 byte. First byte is the operational code, then it comes the content. |

## List of supported operations and messages

| OPERATION | HEX CODE  | PARAMETERS | MEANING 			|
|--------|:------------:|------------|-------------------|
| ADD | 00       | multihash  | Add a message. The parameter is the multihash of the content. Content default is Markdown text in UTF8 without BOM |
| DELETE | 01	   | multihash | Delete a message identified by the specified multihash. This does not delete a message from the blockchain, just tell clients to hide because it's not valid anymore for some reason. Think it like: I changed my mind so please ÐApps don't show this anymore, unless expressly asked by the user of course, and if the content is still available and shared by someone, of course (it's very likely that deleted messages are not shared anyore by the author). |
| UPDATE | 02       | multihash, multihash | Update a message. The first parameter is the message to be updated. The second parameter is the multihash of the updated message |
| REPLY | 03       | multihash, multihash | Reply to a message. The first parameter is the message to reply to. The second parameter is the multihash of the message
| ENDORSE | 04	   | multihash | Endorse a message identified by the specified multihash. Think it as a "like", a "retwitt", etc. |
| DISAPPROVE | 05  | multihash | Disapprove a message identified by the specified multihash. Think it as a "I don't like it" |
| ENDORSE & REPLY | 06 | multihash, multihash | Endorse a message and reply to it. The first parameter is the message to reply to. The second parameter is the multihash of the message
| DISAPPROVE & REPLY | 07 | multihash, multihash | Disapprove a message and reply to it. The first parameter is the message to reply to. The second parameter is the multihash of the message
| CLOSE ACCOUNT | FD | multihash | "Close the account" or "Never consider valid any other MOM messages sent by this account from now on.". This is  useful when you want to change account, especially when the private key is compromised - or you think it is. The multihash parameter is an optional file with motivations |
| CUSTOM | FE	   | any | Custom MOM specifications
| RAW | FF	   | any | Raw content, no need to disclose the meaning. General client can ignore it.

## Project's rationales (work in progress)

My Own Messages
"Just say it to MOM"

Create your Ethereum account dedicated to your personal messages
Spread your words to the world
Follow other

And do it all by yourself

How MOM can help me?

You can send messages to users of your ÐApp or Smart Contract, and they always know it is a voice reliable as the smart contract is.
Say once, show everywhere. Say something only once, it can be seen on every social platform (no more reply of the same post/opinion on dozens of sites like reddit, twitter, facebook, medium, disquis, and so on...)

Verificable and decentralized content

Small fee to be free: pay just few cents of dollar to notarize your messages, and distribute them with IPFS or Swarm.

Get tips for your words directly into your wallet.

Why [multihash](https://github.com/multiformats/multihash)? Because it is flexible, future-proof and there are already a tons of library supporting it.

# MOM v2 Specification (work in progress)

### You don't like default specification? Choose yours
FE - Define your own specification. If you encounter FE again, you read the next byte to know the message type, and so on. If you find FE it means user want to define it's own MOM specifications and meaning. To do that, a smart contract with the specification need to be deployed. To do that, with MOM v2 you can choose to use a MOM Factory but it's not mandatory.

## How to contribute to the MOM standard
- Put a star on this repo
- Spread this repo all over the world via social networks
- Contribute to the specification: open an issue and let's discuss; then, just send a pull request and it will be evaluated

