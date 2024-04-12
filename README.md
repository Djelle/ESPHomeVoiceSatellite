YAML code for ESP32. For making a unit with microphone and speaker to use with Home Assistant: Voice Assistant.

It has support for adressable LED-strip. And 5 buttons for interactions. It has audio sounds for key-click and "Listening" start/end.

A better YAML programmer could probably make this code smarter and more compact. But it is working as it should :)

## Buttons
I used a cheap (and faulty) bluetooth speaker for this project. Which happened to have 5 buttons. Which I utilised like this:
- ⏻ Power: Wake Word On/Of
- ✆ Call: Push To Listen
- ⏯ Play/Pause: Change config selection. E.g. Volume, LED Brightness. (Future maybe: Mic-volume, Noise suppression, Gain.) Volume is not supported yet. But will probably be in the future.
- ➕ Next: Config selection increase
- ➖ Prev: Config selection decrease

## LED-strip
I added an addressable LED-strip around it for state feedback. And made some custom light effects that can support my LED-brightness setting:
- White: "Not Ready" Not connected to HA.
- Orange: "Muted" Wake word disabled.
- Green: "Idle" Wake word enabled.
- Blue: "Listening" Listening for command.
- Pink: "Thinking" Waiting for interpretation of speach.
- Yellow: "Replying" Talking.
- Red: "Error" Is not used. As I am unable to read any error messages (They are gibberish).

State is also exposed in Home Assistant. So automations can be activated by it.

My LED-Strip is RGBW. I do not use the White channel though.

## Future

I hope that it will be possible to send Text-To-Speach to the speaker in the future. Which could have many uses. Like annoucing which config-option is selected.

I experimented with continous listening (no wake word). But I found it very unreliable as it is. So I removed that part of the code. Can re-make it if this option become more valid.

> [!NOTE]
> - When connecting the physical modules together: Make sure the I2S connections are as short as posible.
> - The amplifier module can use 2A of power. So preferably use a power supply that can output that.
> - If you use a LED-strip with many diodes, don't feed it power though the ESP32. But connect the strip and the ESP32 through a common power plug like an USB-C or a barrel plug.

## Photos of the unit I made
![01](/docs/01.jpg)
There was just the perfect room for the elektronics in a corner. I extended the screw 'pins' by 5 mm. So that there was room for a 6 mm latex tube (originally for aquariums) around all the edge. To difuse the led-strip.

![02](/docs/02.jpg)
Idle green. Which is more like teal.

![03](/docs/03.jpg)
Brin-colored scan animation while thinking.

![04](/docs/04.jpg)
Example of LED colors while setting volume: Blue indicate it's volumen. White fills up the rest of the space acording to procentage set.
