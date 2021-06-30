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
	    <script src="https://nexplayer.nexplayersdk.com/multiview/nexplayer.js"></script>
        <script>
            
        var multiView = new nexplayer.MultipleView();

        var callBackWithPlayers = function (nexplayerInstance, videoElement) {
            };

            multiView.additionalVideo({
                key: "Your licence key",
                allowScreenPlayPause: false,
                callbacksForPlayer: callBackWithPlayers,
                debug: false,
                div: document.getElementById('player'),
                hideScreenPlay: false,
                lowLatency: true,
                showingFullUI: false,
                src: 'Your stream URL',
            });

            multiView.additionalVideo({
                key: "Your licence key",
                allowScreenPlayPause: false,
                callbacksForPlayer: callBackWithPlayers,
                debug: false,
                div: document.getElementById('player2'),
                hideScreenPlay: false,
                lowLatency: true,
                showingFullUI: false,
                src: 'Your stream URL',
            });

            multiView.additionalVideo({
                key: "Your licence key",
                div: document.getElementById('player3'),
                callbacksForPlayer: callBackWithPlayers,
                allowScreenPlayPause: false,
                showingFullUI: false,
                hideScreenPlay: false,
                lowLatency: true,
                debug: false,
                src: 'Your stream URL',
            });

            multiView.additionalVideo({
                key: "Your licence key",
                div: document.getElementById('player4'),
                callbacksForPlayer: callBackWithPlayers,
                allowScreenPlayPause: false,
                debug: false,
                hideScreenPlay: false,
                showingFullUI: false,
                lowLatency: true,
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
    <script src="https://nexplayer.nexplayersdk.com/multiview/nexplayer.js"></script>
    <div class="alert alert-warning hints-alert">
        <div class="hints-icon">
            <i class="fa fa-warning"></i>
        </div>
        <div class="hints-container">
            <p>The library above is a test version, the official version will be in the next release.</p>
        </div>
    </div>
    <div class="alert alert-success hints-alert">
        <div class="hints-icon">
            <i class="fa fa-mortar-board"></i>
        </div>
        <div class="hints-container">
            <p>Please note that the use of https to call our library is mandatory. </p>
        </div>
    </div>

```
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

- To create the players we will have to call multiview.additionalVideo() after callBackWithPlayers is created so that the players are initialized sequentially:

```js

    var multiView = new nexplayer.MultipleView();

    var callBackWithPlayers = function (nexplayerInstance, videoElement) {

    };

    multiView.additionalVideo({
        key: "Your licence key",
        allowScreenPlayPause: false,
        callbacksForPlayer: callBackWithPlayers,
        debug: false,
        div: document.getElementById('player'),
        hideScreenPlay: false,
        lowLatency: true,
        showingFullUI: false,
        src: 'Your stream URL',
    });

    multiView.additionalVideo({
        key: "Your licence key",
        allowScreenPlayPause: false,
        callbacksForPlayer: callBackWithPlayers,
        debug: false,
        div: document.getElementById('player2'),
        hideScreenPlay: false,
        lowLatency: true,
        showingFullUI: false,
        src: 'Your stream URL',
    });

    multiView.additionalVideo({
        key: "Your licence key",
        div: document.getElementById('player3'),
        callbacksForPlayer: callBackWithPlayers,
        allowScreenPlayPause: false,
        showingFullUI: false,
        hideScreenPlay: false,
        lowLatency: true,
        debug: false,
        src: 'Your stream URL',
    });

    multiView.additionalVideo({
        key: "Your licence key",
        div: document.getElementById('player4'),
        callbacksForPlayer: callBackWithPlayers,
        allowScreenPlayPause: false,
        debug: false,
        hideScreenPlay: false,
        showingFullUI: false,
        lowLatency: true,
        src: 'Your stream URL',
    });

    multiView.Initialize();

```
- There are some functions available to use, consult the <a href="#/API?id=multiview" target = "_blank" >api</a>

## Synchronization

To be able to use the synchronization we have to configure in the setup the ```lowLatency``` and ```dashSettings```.

```javascript

   multiView.additionalVideo({
          key: "Your licence key",
          div: document.getElementById('player4'),
          callbacksForPlayer: callBackWithPlayers,
          lowLatency: true,
          dashSettings: {  // Optional: Allow modifying some dash properties like the following
            "liveDelay": 20,    // Allow adjusting the live delay
            "liveCatchUpPlaybackRate": 0.5, // The speed that the player gets in order to keep the live delay
            "liveCatchUpMaxDrift": 3,   // The maximun delay before to make a seek live
            "liveCatchupLatencyThreshold": 30,  // The threshold where the synchronization properties works
          }
          src: 'Your stream URL',
      });
   
```
<div class="alert alert-warning hints-alert"><div class="hints-icon"><i class="fa fa-warning"></i></div><div class="hints-container"><p>Currently, live synchronization is only available for Dash.</p>
</div></div>
