# Gimmie Widget

Gimmie Widget provides gamification components for website that you can integrate by just passing javascript
on your page.

## Embed to your website.

Copy below script to put in your web site.

```html
<div id="gimmie-root"></div>
<script type="text/javascript">
    var _gimmie = {
        "endpoint": "http://yoursite.tld/proxy",
        "key": "<key from Gimmie portal>"
    };
    (function(d) {
        var js, id = "gimmie-widget",
            ref = d.getElementsByTagName("script")[0];
        if (d.getElementById(id)) {
            return;
        }
        js = d.createElement("script");
        js.id = id;
        js.async = true;
        js.src = "//api.gimmieworld.com/cdn/gimmie-widget2.all.js";
        ref.parentNode.insertBefore(js, ref);
    }(document));
</script>
```

__Endpoint__ is live in your site. [Here is sample proxy code.](https://github.com/gimmieworld/GimmieProxies) and __Key__ is from Gimmie Portal which you can [register and get from our site.](https://www.gimmie.io)

## Configuration

Gimmie Widget consists of API and 4 pages, Profile, Catalog, Leaderboards and Help. It can disable some page by configuration and override the look and feel by css. Here is the configuration in json format.

```javascript
  var _gimmie = {
    "user": {
        "name": "Name shows in profile page",
        "realname": "Real name shows when user redeem reward",
        "email": "User email for mailing reward code",
        "avatar": "User image url for showing in profile page"
    },
    // Endpoints is proxy script that hiding user id that pass to Gimmie and 
    // prevent other people redeem reward in the name of other person.
    "endpoint": "http://yoursite.com/proxy_to_gimmie",
    // This key can get from Gimmie Portal. Register and get one from https://www.gimmie.io
    "key": "Key from Gimmie Portal",
    // Country code for filtering reward, default is global (Only reward that set to global
    // will show in catalog.)
    "country": "SG",
    "options": {
        // Enable anonymous user mode. All people that visit to your website will create on
        // Gimmie and get the points but cannot redeem the reward till they sign up to your
        // System.
        "anonymous": true,
        // Enable Websocket for pushing notification to your user.
        "push_notification": true,
        // Show Gimmie notification on your web page.
        "auto_show_notification": true,
        // How long points notification will stick on your web page in seconds.
        "notification_timeout": 20,
        // Enable responsive design.
        "responsive": true,
        // Shuffle reward in catalog every time user open it or change category..
        "shuffle_reward": true,
        // Default level icon in user profile page
        "default_level_icon": "",
        "pages": {
            // Catalog page option
            "catalog": {
                // Hide catalog page from Widget
                "hide": false,
                // Hide sponsor here box from catalog
                "hide_sponsor_here": true
            },
            "profile": {
                // Hide profile page from Widget
                "hide": false,
                // Hide user redemption list from profile page
                "redemptions": true,
                // Hide Mayorship list from profile page
                "mayorships": false,
                // Hide Badge list from profile page
                "badges": false,
                // Hide user activities list from profile page
                "activities": true
            },
            "leaderboard": {
                // Hide leaderboard from Widget
                "hide": false,
                // Hide list of user who has most points from leaderboard page
                "mostpoints": true,
                // Hide list of user who has most rewards from leaderboard page
                "mostrewards": true,
                // Hide list of user who has most accumulate redeemed rewards points
                // from leaderboard page
                "mostvalues": true
            }
        }
    },
    // List of functions that get call when user or widget done something.
    "events": {
        // This function will get call when Widget is loaded.
        "widgetLoad": function() {
        },
        // This function will get call when user click on login button.
        "login": function() {
        }
    },
    // Set of string in Widget that you can change.
    "text": {
        "help": "",
        "help_url": "",
        "empty_reward": "",
        "loading_reward": "",
        "error": "",
        "login_title_text": "",
        "login_subline": "",
        "login_headline": "",
        "login_button": "",
        "help_link": "",
        
        "reward_tab_title": "",
        "reward_tab_profile": "",
        "reward_tab_leaderboard": "",

        "points": "",
        "loading": "",
        "reached_highest_level": "",
        "points_to_level": "",
        "badges_title": "",
        "mayorships_title": "",
        "redemptions_title": "",
        "activities_title": "",
        "badge": "",
        "mystery_badge": "",
        "expires": "",
        "redeemed": "",
        "expired": "",
        "loading_activities": "",
        "empty_activities": "",
        "fully_redeemed": "",
        "featured_reward": "",
        "sponsor_here": "",
        "back_to_catalog": "",
        "redeem_button": "",
        "use_reward_now": "",
        "description": "",
        "fineprint": "",
        "user_points": "",
        "see_all_redemptions": "",
        "havent_redeemed": "",
        "see_all_mayorships": "",
        "empty_mayorships": "",
        "see_all_badges": "",
        "loading_badges": "",
        "empty_badges": "",
        "see_all_activities": "",
        "loading_recent_activities": "",
        "all_time_points": "",
        
        "most_points": "",
        "most_rewards": "",
        "most_reward_value": "",
        "loading_leaderboard": ""
    }
};
```
