## Basic Setup

NexPlayer synchronization can be enabled by setting the following property:


```java
mNexPlayer.setProperty(NexPlayer.NexProperty.ENABLE_SPD_SYNC_TO_GLOBAL_TIME, 1);
```

To set the SPD value from the client side for both DASH and HLS you can set the
SPD value with the property ```SET_PRESENTATION_DELAY``` as shown below:

```java
mNexPlayer.setProperty (NexProperty.SET_PRESENTATION_DELAY, 10000);
```

Note that if the value of ```SET_PRESENTATION_DELAY``` is too large, the player may not
find the delayed segment provided by the live content server.

## Advanced configuration

You can control the synchronization behaviour further by adjusting the below
properties.

### Synchronization Accuracy

By default server time is used for synchronziation. You can use the device UTC time instead for more accurate behaviour. Please keep in mind that the device time should be adjusted correctly for synchronization to work properly.

```java
mNexPlayer.setProperty(NexPlayer.NexProperty.ENABLE_SPD_SYNC_TO_DEVICE_TIME, 1);
```

Default: 0

Values:

- 0: Disabled
- 1: Enabled


### Synchronization Speed Control Range

Player will keep the syncronization by controlling the playback speed as long as the playback position is within this range. You can adjust this threshold with the ```SET_SPD_SYNC_DIFF_TIME``` property.

```java
mNexPlayer.setProperty(NexPlayer.NexProperty.SET_SPD_SYNC_DIFF_TIME, 500);
```

Unit: msec (1/1000 sec)

Default: 300 (300 msec)

### Synchronization Seek Range

If playback is out of synchronization more than this value, the player will make a seek to synchronize the video rather than changing the playback speed.

```java
mNexPlayer.setProperty(NexPlayer.NexProperty.SET_SPD_TOO_MUCH_DIFF_TIME,5000);
```

Unit: msec (1/1000 sec)

Default: 5000 (5 seconds)

## Things to consider

- For HLS, you should set ```SET_PRESENTATION_DELAY``` property as mentioned
above.
- You should make sure there is enough distance from the live edge to provide
a smooth playback which should be adjusted with *suggestedPresentationDelay* and ```SET_PRESENTATION_DELAY``` properties. If there is not enough space to buffer from the live edge, playback might be effected.