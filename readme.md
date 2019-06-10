# How to use Wishpond Contest V1 on Landing Pages

Please Make sure you follow all these steps in order to implement this feature fully functional

## Create a Contest Page

1. Please Create a contest page.

2. Click on `Edit CSS and JS`

3. Copy the page number from the url which looks like This

~~https://www.wishpond.com/central/landing_pages/~~`2455192`~~/edit?type=photo&urk=418b5f54ae82abcc10425e279c33c512c5f0a7e5f23f98aa&user_action=editing&wizard_step_key=9acfbeef-4614-4981-8fe8-976f0e6a65c4~~

4. Add the code below on the JS section

```javascript
$();

function getQueryVariable(variable)
{
       var query = window.location.search.substring(1);
       var vars = query.split("&");
       for (var i=0;i<vars.length;i++) {
               var pair = vars[i].split("=");
               if(pair[0] == variable){return pair[1];}
       }
       return(false);
}

if(getQueryVariable('gallery') == 'true'){
    $('.row:eq(3)').remove()
}
else{
    $('.row:eq(4)').remove();
    $('.row:eq(5)').remove();
    $('.row:eq(6)').remove();
    $('.row:eq(7)').remove();
    $('.row:eq(4)').remove();
}

$('button').click(function(){
	var count = 0;
	$('.form-control').each(function(){
		if(this.value == ""){
			count +=1;
		}
	})
	if (count == 0){
	    console.log('done');
		window.parent.postMessage('xgfdfsLLS', 'https://wipond.wishpond.com')
	}
})
```

5. Add the code below to the CSS section

```css
.container:first-child, .container-fluid, .col-md-6.col-md-offset-1.col-sm-7{
    display: none;
}

body.wp_body{
    background-color: white;
}
```
6. Click `Next`

7. Select the option `Embed on My Website or Blog` from `Choose where your campaign will appear`

8. Leave the `My Website URL` empty

9. Copy the embed code that looks like this:

```HTML
<!-- Wishpond embed code -->
<script type="text/javascript" src="//cdn.wishpond.net/connect.js?merchantId=772639&writeKey=664c0889106b" async></script><div class="wishpond-campaign" data-wishpond-id="2455192" data-wishpond-href="https://embedded.wishpondpages.com/lp/2455192/"></div>
```

10. Click on Publish the change

## 11. Create a Landing Page

12. Create any Kind of Landing page

13. Click on `Campaign Design`

14. Click on `Custom Javascript`

15. Add the code Below

```javascript
$();
function closeIFrame(){
    console.log('worked');
    $(".hide-this").click();
}

function receiveMessage(evt){
    if( evt.data === "xgfdfsLLS"){
        closeIFrame();
    }
}

window.addEventListener('message', receiveMessage, false);
```

16. Click on `Add Content` and Drag `HTML` and drop it where you want your field to be.

17. Edit the `HTML` content and paste the embed code that was copied on step `8` the following code

***Make Sure You change the the content in between `[]` in regards to your own information***

```HTML
<!-- Wishpond embed code -->
<script type="text/javascript" src="//cdn.wishpond.net/connect.js?merchantId=772639&writeKey=664c0889106b" async></script><div class="wishpond-campaign" data-wishpond-id="[2455192 page number from step 3]" data-wishpond-href="https://embedded.wishpondpages.com/lp/[2455192 page number from step 3]/"></div>
```

17. Follow Step `15` and `16` and add the following code for the `Gallery Section`

```HTML
<iframe style="position: absolute; height: 100%; border: none" src="https://embedded.wishpondpages.com/lp/[2455192 page number from step 3]/?gallery=true" style="border:0px #ffffff none;" name="gallery" scrolling="yes" frameborder="1" marginheight="0px" marginwidth="0px" height="100%" width="100%" allowfullscreen></iframe>
```

18. Save the changes and Good luck
