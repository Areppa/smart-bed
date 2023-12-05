# CURRENT STATUS: NOT PROPERLY TESTED!

# Smart Bed
Smart Bed is a project that allows you to have better control of your motorized bed. The actual code is generated using [ESPHome](https://esphome.io/) which makes it easy to connect to automation platforms such as [Home Assistant](https://www.home-assistant.io/) or any other system that is compatible with ESPHome.

# Why?
This was just one of those ideas that I thought would be interesting to implement. But does it have any practical use? Maybe it is a better way to wake you up if you have a hard time waking up. I don't know. I just wanted to make it.

Also I saw [Colinfurze's video](https://www.youtube.com/watch?v=EVzn1pl4nlo) about an automatically ejecting bed which gave me some inspiration.

# How it works
This project assumes that the bed's remote has 4 buttons. There are two buttons for raising the head and legs and two for lowering them. Relays are used to simulate pressing those buttons. Some remotes might have more buttons, such as buttons for raising and lowering the whole bed. Those features can be used by using both head and leg relays at the same time.

There are two ways of wiring this: either replacing the original remote or wiring it in parallel with the new controller. I chose the latter because I believe that smart devices should always add new features, never remove them or make them harder to use. This way, you can still use the bed with the original remote.

For the position of the bed, I chose to use ESPHome's time_based cover component. This is not 100% accurate but it should be accurate enough.

The next problem with the smart bed are timings. I found out that the raising and lowering times change depending on the weight on the bed. Also, when raising both the head and legs at the same time, the time is longer than when raising only one of them. If you want to replicate this project, you should do some experimenting with your bed and adjust the timings accordingly. I would also add some extra time to the lowering time to reset the timer based location tracking.

For the power, I used an old phone charger that I had laying around. This is an easy way to give power to the controller. You just need to check that the voltage is correct and that the power supply can provide enough current for the controller and relays.

# Requirements
- ESPHome compatible controller (ESP32, ESP8266, etc.)
- 4ch relay board
- Power supply (I used an old phone charger for this)
- A cable to connect everything together
- Connectors that go between your bed controller and bed
  - This is optional but recommended if you want to keep the original controller. Otherwise, you need to cut the remote cable and use its connector.
- USB to TTL converter
  - This is only required if your controller does not have an USB port

Personally I used prefabricated [ESP32 board with 4ch relay](https://devices.esphome.io/devices/AC-DC-ESP32-Relay-x4). You can find similar ones from Ebay and Aliexpress.

# DISCLAIMER!
I don't take any responsibility if you break something. This is just a documentation on how I made this project!