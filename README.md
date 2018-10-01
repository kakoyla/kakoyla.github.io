# icecold

> cold wallet interface

# Build Setup
This is just the demo BUT you can use this if you don't care about looking at the code.

Click the green Clone or Download button to save locally.


To use this without a server (offline):
	
	1. OPEN the index.html
	2. FIND ALL "href=/" REPLACE WITH "href="
	3. FIND ALL "src=/" REPLACE WITH "src="
	4. SAVE 

After saving you can open index.html and it will load offline with no server running.

## Why would I ever trust this without looking at the code? 
	
Good question!
	
I made this for friends and family who are not tech savy. 
They will never look at the code anyway.
Based on my experience reading the different forums, neither will anyone else, mainly because they dont know how. If they do know how they most likely have better things to do with their time.

## Is there another way to test this is legit?

I was thinking, do you really need to go through the code line by line in-order to trust this or is there another way?

If used for its intended purpose (only on an offline PC),the only piece that comes out of this app that will ever be exposed will be the tx_blob, which will be submitted on an online pc.

So why not check that the tx_blob is legitimate rather than going through the code line by line (which never happens anyway). 

You can easily convert a signed tx_blob back to JSON by using the ripple binary codec.


## Decode tx_blob with the following (assumes you have node installed):
	 
install ripple binary codec (https://github.com/ripple/ripple-binary-codec)
		
		npm i ripple-binary-codec
	
save this code as decodeTx.js:
		
		const binary = require('ripple-binary-codec')
		const signedTX ='ENTER tx_blob HERE' 
		var decoded = (binary.decode(signedTX))
		console.log(decoded)
		if (decoded.Memos) {
  		console.log(decoded.Memos)
		}
		
Then update const signedTX with your tx_blob and save
	
Run it on the command line with
	 	
		node decodeTx.js 
The decoded tx_blob will be shown and you can now review to make sure the fields present match your expected transaction.
