# Alfred Airpod Workflow

![Connect](https://user-images.githubusercontent.com/437043/185495573-c3191458-dba0-4cc0-9b8c-e622284d8645.gif)

I made this workflow because MacOS doesn't always properly connect/disconnect from my Airpods and I didn't want to have to use the mouse to do so. There are other Alfred Workflows that do this, but the one I was most recently using stopped working and I thought it was a good excuse to figure out how to make my own Workflow.

In order to use this Workflow, you'll need to install [blueutil](https://github.com/toy/blueutil) and a [this](https://github.com/sendhil/airpod_alfred_connector) cli helper utility I wrote to go along with the workflow (detailed instructions below).

# Installing

1. Download the `alfredworkflow` [file](https://github.com/sendhil/alfred-airpod-workflow/raw/main/Connect%20to%20Airpods.alfredworkflow) and import it into Alfred.
2. Install blueutil. If you have homebrew, just run `brew install blueutil`.
3. Install the CLI helper by cloning https://github.com/sendhil/airpod_alfred_connector. Assuming you have cargo installed, run `cargo install --path .` from within the project. Instructions on installing Cargo can be found [here](https://doc.rust-lang.org/cargo/getting-started/installation.html). 
4. Within the Alfred workflow, make sure you configure the `BLUEUTIL_PATH` and the `CLI_PATH` (both are currently set to where they live on my computer). If you aren't sure how to do this, check out this screenshot [here](https://user-images.githubusercontent.com/437043/185488620-808f34ec-99b6-49e6-aff8-77f4c2f96753.png).
5. To check that everything is working correctly, type in `airp` and hit enter, you should see a list of any bluetooth device you've paired with that has "Airpod" (Case-/insensitive) in the title.

# Using the Workflow

The primary entry point for using the workflow is to type `airp` into Alfred and hit enter. This will list all of all bluetooth devices you've connected with that have the word "Airpod"(Case-insensitive) in them. Selecting a device will toggle the connection state of the device (i.e. if you are not connected to the device, it will connect to it, and if you are connected it will disconnect). If you want to force a connection or disconnect(sometimes the state is stale), you can use `Cmd-Enter` to force a connection and `Ctrl-Enter` to force a disconnection.

To specify set of devices for the Workflow, you can use the `airp configure` command which will list all Bluetooth devices your Mac is paired with. Selecting a device and hitting it enter will save it to a list of devices that the Workflow displays when running the main command.

Here's an example of what this looks like:
![Specify Devices](https://user-images.githubusercontent.com/437043/185495641-425a3741-816d-4b1f-b422-f96da4a4712f.gif)

To remove a device you have saved, enter `airp configure` hit `Cmd-Enter` which lists out the saved devices. From here, select the device you want to remove and then hit "Cmd-Enter" again and it will remove it from the list. Here's an example of what this looks like:

![Remove Device](https://user-images.githubusercontent.com/437043/185495678-de7dd48a-21b8-4b08-8935-d3289e224444.gif)

# Known Issues

* Sometimes the device state (i.e. if the Workflow lists it as connected) is stale. This seems to be an issue that crops up if your Airpods are switching between multiple Apple devices. Just run the command you want to twice and you should be good (i.e. if you try to connect and it doesn't work, just retry it).
* I need to test this more, but when MacOS first notices the Airpods and asks you to connect to them, you sometimes have to click the connect button it presents you with before the workflow works.

