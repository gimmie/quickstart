# vBulletin quickstart

Gimmie Reward for vBulletin provides a reward program for your vBulletin. The plugin includes events that you can configure in [Gimmie portal](https://portal.gimmieworld.com) to give out points or instant rewards.

Here are the events included currently:

- __login_site__, This event is called when user login to site
- __create_poll__, This event is called when user create a poll.
- __create_post__, This event is called when user create a post.
- __rate_thread__, This event is called when user rate a thread.
- __received_thread_rating__, This event is called when use thread receive a rating.
- __refer_a_friend__, This event is called when user refer a friend and the friend sign up.
- __create_thread__, This event is called when user create a thread.
- __vote_poll__, This event is called when user vote on a poll.

## Installation

You will need vBulletin hosting that allow plugin installation. Some basic vBulletin and developer knowledge will be useful for the installation. This plugin is only applicable for vBulletin v4 and below. Here are the steps to install Gimmie Reward for vBulletin plugin.

- Get the plugin zip file from [Github](https://github.com/gimmie/vbulletin-v4)

![Gimmie Reward for vBulletin plugin on Github](images/vbulletin/vbulletin1.png)

- Extract the zip file and upload everything in the /upload folder to the root folder of your vbulletin forum.

- From your vbulletin Control Panel, go to Plugins & Products -> Manage Products -> Add/Import Product and put ./XML/product_gimmie.xml in the "OR import the XML file from your server" box and click

![Add/Import Product](images/vbulletin/vbulletin2.png)

- From your vBulletin Control Panel, go to -> Settings -> Options

- Click "Edit Settings" for Gimmie Loyalty Program Setting

- Fill in the __Gimmie KEY__ and __Gimmie Secret__ and update the option accordingly on Gimmie Loyalty Program Setting

![Gimmie Loyalty Program Setting](images/vbulletin/vbulletin3.png)

## Add reward catalog link to your vbulletin

 - To add the Rewards button, Search ```ul id="navtabs"``` under Styles & Templates > Search in Template. 

 - Click on "navbar" file. Find ``` <ul id="navtabs" class="navtabs .... `` in the Template field, add << <li><a href="javascript:;" gm-view="catalog" class="navtab"><span>Rewards</span></a></li> >> just above the </ul> 

 e.g.

 ```
 &lt;ul id="navtabs" class="navtabs floatcontainer&lt;vb:if condition="$show['member'] AND $notifications_total"&gt; notify&lt;/vb:if&gt;"&gt;
 		{vb:raw template_hook.navtab_start}
 		{vb:raw navigation}
 		{vb:raw template_hook.navtab_end}
     &lt;li&gt;&lt;a href="javascript:;" gm-view="catalog" class="navtab">&lt;span&gt;Rewards&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;
 &lt;/ul&gt;
 ```
 
 - To add user points beside Username, Search << li class="welcomelink" >> under Styles & Templates > Search in Template. 

 Click on "header" file. Find ``` li class="welcomelink" ``` in the Template field, add ``` <span gm-view="profile" style="cursor:pointer;font-weight:bold;">(<span class="gimmie-user-points">...</span> points)</span> ``` just above the ```</li>```

 e.g. 

 ```
  &lt;li class="welcomelink">{vb:rawphrase welcome_x_link_y, {vb:raw bbuserinfo.username}, {vb:link member, {vb:raw bbuserinfo}}} &lt;span gm-view="profile" style="cursor:pointer;font-weight:bold;"&gt;(&lt;span class="gimmie-user-points"&gt;...&lt;/span&gt; points) &lt;/span> &lt;/li&gt;
 ```
 