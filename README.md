# Building a website hosted on IPFS
*This should be fun*

## Lets build a static website
### The approach
Not being a front end developer, I have looked for something relatively simple to implement. Some of the existing tutorials used the [hugo framework](https://gohugo.io/) which proves very easy to implement.  

I pushed the fun to change the default theme, adding a post as well as a manual summary split (`<!--more-->`). Time will tell if I add more posts but the idea here is to learn...  
Next step ! 

### Helpful resources
- https://gohugo.io/getting-started/quick-start/


## Continuous Deployment to IPFS and pinning in Pinata
### Approach
OK, time to play with GitHub actions ! 
  
At first glance, the steps are:
- Checkout Code
- Install Hugo
- Build hugo website
- Upload `public` folder (resulting from the `build` action) to Pinata directly (yes I do want the website to be accessible straight away)

>NB: It WORKED ! At the time of writing, the url is : https://gateway.pinata.cloud/ipfs/QmUkDw96Pa472EH9WMS6xtCQB8VmmALuVzGWwXMEZ1RJbi/
  
Right, but now is the catch: if I update the contents and push it automatically via my workflow, the content identifier (CID) from my pin will change. However, I want followers to be able to find my site at any time. So lets investigate how to do that.

### Resources
- https://github.com/peaceiris/actions-hugo
- https://github.com/marketplace/actions/ipfs-pinata-deploy-github-action

## Gateway, DNS and all the rest
### 1st try
By looking more into gateways, at the moment, I am good to use the pinata one `https://gateway.pinata.cloud/ipfs`. 
> First error: I can retrieve this info from any public gateway (cloudflare-ipds.com, ipfs.io etc ... just much slower). Wow, this is cool !
IPFS Gateways are third-party nodes that fetch content from the IPFS network and serve it over HTTPS. 

Looking at the output from the Pinata deploy Task, I can identify the `HASH/CID` of the newly uploaded folder that makes the full URL of the decentralised website:
```
...
path: ./public
sourcePath: /home/runner/work/se-to-be-website/se-to-be-website/public
{
  IpfsHash: 'QmUkDw96Pa472EH9WMS6xtCQB8VmmALuVzGWwXMEZ1RJbi',
  PinSize: 62085,
  Timestamp: '2022-01-06T14:53:01.480Z'
}
HASH: QmUkDw96Pa472EH9WMS6xtCQB8VmmALuVzGWwXMEZ1RJbi
{
  count: 1,
  rows: [
    {
      id: '1940f08f-4cf8-4ab2-84c7-0fcb6eded02c',
      ipfs_pin_hash: 'QmUkDw96Pa472EH9WMS6xtCQB8VmmALuVzGWwXMEZ1RJbi',
      size: 62085,
      user_id: '81fc76d9-866d-46f9-9f7d-0f1cc30d80e3',
      date_pinned: '2022-01-06T14:53:01.480Z',
      date_unpinned: null,
      metadata: [Object],
      regions: [Array]
    }
  ]
}
...
```
Right, so I have the inputs I need. Now I need to understand what is a DNS and how it works.

### Resources
https://docs.ipfs.io/concepts/dnslink/#publish-content-path
https://blog.cloudflare.com/distributed-web-gateway/
https://developers.cloudflare.com/distributed-web/ipfs-gateway


## Continuous deployment
https://withblue.ink/2019/03/20/hugo-and-ipfs-how-this-blog-works-and-scales.html

## Resources
- https://teetotality.blog/posts/how-this-blog-was-made/
- https://github.com/totality-dot-earth/totality-blog/tree/master/totality
- https://cloudflare-ipfs.com/ipfs/Qmbq5hoM4eCeCnSSTcXSyaYNjNHgCmeQ58VuqJxU1tu3ho/IPFS_For_Sysadmins.pdf
- https://medium.com/pinata/how-to-easily-host-a-website-on-ipfs-9d842b5d6a01
