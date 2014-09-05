#Gimmie Rewards Catalog Embed

You can integrate the rewards catalog of your game into your site through the following steps.

## 1. Serve proxy
Add a [proxy](https://github.com/gimmie/proxies) according to your system.
For example if you are in php, serve [this file](https://github.com/gimmie/proxies/blob/master/php/connect.php) from the root, and you will have:
````html
<script... data-gimmie-proxy="/connect" src=... />
````
## 2. Embed a `<script>` into your page
Copy the script below and put in your page:
````html
<script id="gimmie-rewards_catalog-script" async data-gimmie-proxy="/PROXY_LOCATION" 
src="https://api.gimmieworld.com/1/embed/rewards_catalog.js?oauth_consumer_key=GIMMIE_KEY"></script>
````

`GIMMIE_KEY` is your game's unique key, taken from [Gimmie Portal](http://portal.gimmieworld.com)

`PROXY_LOCATION` is the uri to the proxy that your site has to serve, which is from step 1.


## Screenshots

- Embeded catalog
![Embeded catalog](/images/embed/rewards_catalog_embed.png)

- Rewards detail
![Rewards detail](/images/embed/rewards_catalog_embed_detail.png)
![Rewards detail mobile](/images/embed/rewards_catalog_embed_detail_m.png)

- Rewards redeemd
![Rewards detail](/images/embed/rewards_catalog_embed_redeemed.png)
![Rewards detail mobile](/images/embed/rewards_catalog_embed_redeemed_m.png)
