<!-- @author: gautham_reddy_mrrv -->
<!-- src: https://web3.storage -->
<h1>Welcome to Web 3.0</h1>
<h2> Uploading files in a Decentralized network using Web3 Storage with Node js running on IPFS protocol </h2>
<p>Create a file "put-file.js" & paste the code down below </p>

```
import process from 'process'
import minimist from 'minimist'
import { Web3Storage, getFilesFromPath } from 'web3.storage'

async function main () {
  const args = minimist(process.argv.slice(2))
  const token = args.token

  if (!token) {
    return console.error('A token is needed')
  }

  if (args._.length < 1) {
    return console.error('Please supply the path to a file or directory')
  }

  const storage = new Web3Storage({ token })
  const files = []

  for (const path of args._) {
    const pathFiles = await getFilesFromPath(path)
    files.push(...pathFiles)
  }

  console.log(`Uploading ${files.length} files`)
  const cid = await storage.put(files)
  console.log('Content added with CID:', cid)
}

main()
```
<p>You should have created token from web3.storage. So, create and have it copied somewhere but keep it ready we're about to use it. Create a "package.json" file to install necessary packages for web3.storage & paste the code below.</p> <br>

```
{
    "name": "web3-storage-quickstart",
    "version": "0.0.0",
    "private": true,
    "description": "Get started using web3.storage in Node.js",
    "type": "module",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "dependencies": {
        "minimist": "^1.2.5",
        "web3.storage": "^3.1.0"
    },
    "author": "AUTHOR",
    "license": "(Apache-2.0 AND MIT)"
}
```

> npm install 
<p>Get your sharable files and be sure to place them in the same working folder before uploading them to the decentralized network called IPFS(InterPlanetary File System). </p>

``` 
node put-file.js --token=<YOUR_TOKEN> ~/fileName1 ~/fileName2 ~/fileNameN
```

<pre> For example node put-file.js --token=<YOUR_TOKEN> myFile.txt holiday_cheers.jpeg machine_learning.ipynb </pre>
<p>Running this will give an output as below: </p>

```
Content added with CID: bafybeig7sgl52pc6ihypxhk2yy7gcllu4flxgfwygp7klb5xdjdrm7onse

```

<p>It will generate your own hash or CID basically. Uploaded files can be accessed in two ways </p>

<pre>https://YOUR_CID.ipfs.dweb.link 
              or 
https://dweb.link/ipfs/YOUR_CID </pre>


***********************************************************************************************************************************************************************
