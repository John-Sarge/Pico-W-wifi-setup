# Pico-W-wifi-setup

This is an example of setting up a Raspberry Pi Pico W onto a network using MicroPython.
It is initialized in the boot.py file as that file is first run at micropython startup and to keep it out of main.py.

1\. Importing Modules:

-   `import network`: This line imports the `network` module, which provides functions for working with WiFi networks.

-   `import time`: This line imports the `time` module, which allows you to work with time-related functions like delays and pauses.

-   `from time import sleep`: This line imports the specific `sleep` function from the `time` module, making it easier to use for pausing the code execution.

2\. Connecting to the WiFi Network:

-   `wlan = network.WLAN(network.STA_IF)`: This line creates a new WiFi object named `wlan` in station mode, meaning it will connect to an existing WiFi network.

-   `wlan.active(True)`: This line activates the WiFi interface on the Pico W.

-   `wlan.config(pm = 0xa11140)`: This line configures the WiFi power management settings to prevent the wireless chip from entering power-saving mode when it's idle, ensuring a more stable connection.

-   `wlan.ifconfig(('ip', 'subnet', 'gateway', 'dns'))`: This line configures a static IP address for the Pico W. You'll need to replace the placeholders with appropriate values for your network.

-   `ssid = 'ssid'`: This line sets the SSID (network name) of the WiFi network you want to connect to. Replace 'ssid' with your actual network name.

-   `wlan.connect(ssid)#, password)`: This line initiates the connection to the specified WiFi network. Optionally, you can uncomment the `password` argument and provide the password if your network requires one.

3\. LED Feedback and Connection Status:

-   `led = machine.Pin('LED', machine.Pin.OUT)`: This line creates an object named `led` to control the onboard LED on the Pico W, setting it as an output pin.

-   `for i in range(wlan.status()):`: This loop continuously checks the WiFi connection status and blinks the LED while the connection is being established.

    -   `led.on()`: Turns the LED on.

    -   `time.sleep(2)`: Pauses the code for 2 seconds.

    -   `led.off()`: Turns the LED off.

    -   `time.sleep(2)`: Pauses the code for another 2 seconds.

    -   `print('Connected')`: Prints a message indicating that the connection is successful.

    -   `status = wlan.ifconfig()`: Gets the current IP configuration of the Pico W.

    -   `print('ip = ' + status[0])`: Prints the assigned IP address.

In summary, the code's primary functions are:

-   Establishing a WiFi connection to the specified network.

-   Providing visual feedback through the LED during the connection process.

-   Displaying the assigned IP address once the connection is successful.

created by [John Seargeant](https://github.com/John-Sarge) with a little help from GPT and Bard.  03Feb2024
