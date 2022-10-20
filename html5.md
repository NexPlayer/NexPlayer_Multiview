#  MultiView

## Demo

You can see the multiview demo <a href="https://nex360.s3.amazonaws.com/MultiView/index.html">here</a>:

<img width="100%" text-align="center" src="./assets/multiview.PNG" alt="logo of docsify-awesome repository" >

## Sample

Multi-view playback integrated in html5:

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
	<title>NexPlayer</title>
	<style type="text/css">
		body {
			background-color: #1E1F23;
		}
		#player_container {
			width: 90%;
			margin: auto;
			padding-top: 50.625%;
			/* 16:9 Aspect Ratio 56.25 * 0.9 */
			position: relative;
			background-color: rgba !important;
		}
		#player_container2,
		#player_container3,
		#player_container4 {
			width: 90%;
			margin: auto;
			padding-top: 40.625%;
			/* 16:9 Aspect Ratio 56.25 * 0.9 */
			position: relative;
			background-color: rgba !important;
		}
		#global_container {
			display: flex;
			justify-content: space-around;
		}
		#player_container_360 {
			width: 90%;
			margin: auto;
			position: relative;
			padding-top: 50.625%;
			/* 16:9 Aspect Ratio 56.25 * 0.9 */
		}
		@media (min-width: 75rem) {
			#player_container {
				width: 50%;
				padding-top: 28.125%;
				/* 16:9 Aspect Ratio 56.25 * 0.5 */
			}
			#player_container2,
			#player_container3,
			#player_container_360,
			#player_container4 {
				width: 25%;
				padding-top: 22.125%;
				/* 16:9 Aspect Ratio 56.25 * 0.5 */
			}
		}
		h1 {
			text-align: center;
		}
		#player {
			background-color: black;
			position: absolute;
			top: 0px;
			width: 100%;
			height: 100%;
		}
		#player2,
		#player3,
		#player4 {
			background-color: black;
			position: absolute;
			top: 0px;
			width: 100%;
			height: 100%;
		}
		.box {
			padding-top: 2%;
			display: flex;
			justify-content: space-between;
		}
	</style>
</head>
    <body>
        <div id="player_container">
            <div id="player" width="530" height="315"></div>
        </div>
        <div id="global_container">
            <div id="player_container2">
                <div id="player2" width="530" height="315"></div>
            </div>
            <div id="player_container3">
                <div id="player3" width="530" height="315"></div>
            </div>
            <div id="player_container4">
                <div id="player4" width="530" height="315"></div>
            </div>
        </div>
	    <script src="Ask for the latest NexPlayer SDK version"></script>
        <script>
            
        var multiView = new nexplayer.MultipleView();

        var callBackWithPlayers = function (nexplayerInstance, videoElement) {
            };

            multiView.additionalVideo({
                key: "Your license key",
                allowScreenPlayPause: false,
                callbacksForPlayer: callBackWithPlayers,
                debug: false,
                div: document.getElementById('player'),
                hideScreenPlay: false,
                showingFullUI: false,
                src: 'Your stream URL',
            });

            multiView.additionalVideo({
                key: "Your license key",
                allowScreenPlayPause: false,
                callbacksForPlayer: callBackWithPlayers,
                debug: false,
                div: document.getElementById('player2'),
                hideScreenPlay: false,
                showingFullUI: false,
                src: 'Your stream URL',
            });

            multiView.additionalVideo({
                key: "Your license key",
                div: document.getElementById('player3'),
                callbacksForPlayer: callBackWithPlayers,
                allowScreenPlayPause: false,
                showingFullUI: false,
                hideScreenPlay: false,
                debug: false,
                src: 'Your stream URL',
            });

            multiView.additionalVideo({
                key: "Your license key",
                div: document.getElementById('player4'),
                callbacksForPlayer: callBackWithPlayers,
                allowScreenPlayPause: false,
                debug: false,
                hideScreenPlay: false,
                showingFullUI: false,
                src: 'Your stream URL',
            });

        multiView.Initialize();
        
        </script>
    </body>
</html>

```

## Step-by-Step

To integrate NexPlayer™ multiview into your project you must complete the following steps:

- The NexPlayer™ JavaScript library should be included in the HTML file:

```html
<script src="Ask for the latest NexPlayer SDK version"></script>
```

<div class="alert alert-success hints-alert">
    <div class="hints-icon">
        <i class="fa fa-mortar-board"></i>
    </div>
    <div class="hints-container">
        <p>Please note that the use of https to call our library is mandatory. </p>
    </div>
</div>

- A div that will contain the videos and the UI has to be declared:

```html
    <body>
        <div id="player_container">
            <div id="player" width="530" height="315"></div>
        </div>
        <div id="global_container">
            <div id="player_container2">
                <div id="player2" width="530" height="315"></div>
            </div>
            <div id="player_container3">
                <div id="player3" width="530" height="315"></div>
            </div>
            <div id="player_container4">
                <div id="player4" width="530" height="315"></div>
            </div>
        </div>
    </body>

```

- To create the players we will have to call multiview.addVideo() after callBackWithPlayers is created so that the players are initialized sequentially:

```js

    var multiView = new nexplayer.MultipleView();

    var callBackWithPlayers = function (nexplayerInstance, videoElement) {

    };

    multiView.additionalVideo({
        key: "Your license key",
        allowScreenPlayPause: false,
        callbacksForPlayer: callBackWithPlayers,
        debug: false,
        div: document.getElementById('player'),
        hideScreenPlay: false,
        showingFullUI: false,
        src: 'Your stream URL',
    });

    multiView.additionalVideo({
        key: "Your license key",
        allowScreenPlayPause: false,
        callbacksForPlayer: callBackWithPlayers,
        debug: false,
        div: document.getElementById('player2'),
        hideScreenPlay: false,
        showingFullUI: false,
        src: 'Your stream URL',
    });

    multiView.additionalVideo({
        key: "Your license key",
        div: document.getElementById('player3'),
        callbacksForPlayer: callBackWithPlayers,
        allowScreenPlayPause: false,
        showingFullUI: false,
        hideScreenPlay: false,
        debug: false,
        src: 'Your stream URL',
    });

    multiView.additionalVideo({
        key: "Your license key",
        div: document.getElementById('player4'),
        callbacksForPlayer: callBackWithPlayers,
        allowScreenPlayPause: false,
        debug: false,
        hideScreenPlay: false,
        showingFullUI: false,
        src: 'Your stream URL',
    });

    multiView.Initialize();

```
- There are some functions available to use, consult the <a href="https://nexplayer.github.io/NexPlayer_HTML5_Documentation/#/API?id=multiview" target = "_blank" >api</a>

## Synchronization

To be able to use the synchronization we have to configure in the setup the ```liveSettings```.

```javascript

   multiView.additionalVideo({
          key: "Your license key",
          div: document.getElementById('id video'),
          callbacksForPlayer: callBackWithPlayers,
          lowLatency: true,
          liveSettings: { //Optional, requires low latency
            liveDelay: 5, // Optional, seconds of delay.
            maxDrift: 10, // Optional, the maximum delay before to make a seek live.
            playbackRate: 0.5,   // Optional, the speed that the player gets in order to keep the live delay.
        }, 
          src: 'Your stream URL',
      });
   
```
<div class="alert alert-warning hints-alert"><div class="hints-icon"><i class="fa fa-warning"></i></div><div class="hints-container"><p>Currently, live synchronization is only available for Dash.</p>
</div></div>
