#Gimmie Rewards Catalog Embed

You can integrate the rewards catalog of your game into your site through the following steps.

## 1. Embed a `<script>` into your page
Copy the script below and put in your page:
````html
<script id="gimmie-rewards_catalog-script" async data-gimmie-proxy="/__PROXY_LOCATION__" 
src="http://api.lvh.me/1/embed/rewards_catalog.js?oauth_consumer_key=__GAME_KEY__"></script>
````

`__GAME_KEY__` is your game's unique key, taken from [Gimmie Portal](http://portal.gimmieworld.com)

`__PROXY_LOCATION__` is the uri to the proxy that your site has to serve, which is step 2:

## 2. Serve proxy
Add a [proxy](https://github.com/gimmie/proxies) according to your system.
For example if you are in php, serve [this file](https://github.com/gimmie/proxies/blob/master/php/connect.php) from the root, and you will have:
````html
<script... data-gimmie-proxy="/connect" src=... />
````
