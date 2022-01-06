# Building a website hosted on IPFS
*This should be fun*

## Lets build a static website
Not being a front end developer, I have looked for something relatively simple to implement. Some of the existing tutorials used the [hugo framework](https://gohugo.io/) which proves very easy to implement.  

I pushed the fun to change the default theme, adding a post as well as a manual summary split (`<!--more-->`). Time will tell if I add more posts but the idea here is to learn...  
Next step ! 

## Continuous Deployment to IPFS and pinning in Pinata
OK, time to play with GitHub actions ! 
  
At first glance, the steps are:
- Checkout Code
- Install Hugo
- Build hugo website
- Upload `public` folder (resulting from the `build` action) to Pinata directly (yes I do want the website to be accessible straight away)

## Gateway, DNS and all the rest

## Continuous deployment
https://withblue.ink/2019/03/20/hugo-and-ipfs-how-this-blog-works-and-scales.html

## Resources
- https://gohugo.io/getting-started/quick-start/
- https://teetotality.blog/posts/how-this-blog-was-made/
- https://github.com/totality-dot-earth/totality-blog/tree/master/totality
- https://cloudflare-ipfs.com/ipfs/Qmbq5hoM4eCeCnSSTcXSyaYNjNHgCmeQ58VuqJxU1tu3ho/IPFS_For_Sysadmins.pdf
