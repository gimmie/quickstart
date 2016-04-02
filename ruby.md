#Ruby Example

Some gems that the example requires
````
# sudo gem install oauth json
require 'rubygems'
require 'oauth'
require 'json'
````

## Set up authentication

As described at http://support.gimmie.io/hc/en-us/articles/202788800-API#trigger

````
my_player_uid = "TEST123"
consumer_key = "015cc2ed0ff11f1bc3b49ec39816"
consumer_secret = "b83febd7e9f73cc0b5e147f79159"

# notice there is no token request steps. you already have access!
access_token = my_player_uid
access_token_secret = consumer_secret

# oauth
consumer = OAuth::Consumer.new(consumer_key, consumer_secret, :site => "https://api.gimmie.io")
token = OAuth::AccessToken.new(consumer, access_token, access_token_secret)
````
## Call api

````
puts JSON.pretty_generate(JSON.parse token.get("https://api.gimmie.io/1/profile.json").body)
````
