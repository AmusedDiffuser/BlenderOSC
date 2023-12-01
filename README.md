# BlenderOSC and ReaperOSC

## *Note: Early development, NOT WORKING YET!* 

BlenderOSC and ReaperOSC are two tools that allow you to integrate Blender and Reaper using OSC and MIDI communication. You can control various aspects of both applications with live feedback, and create complex interactions between them using different data types and formats. These tools enhance your creative potential and productivity, as well as provide a fun and engaging experience.

## Table of Contents

- [Overview](#overview)
- [BlenderOSC](#blenderosc)
  - [Installation](#installation-blenderosc)
  - [Features](#features-blenderosc)
- [ReaperOSC](#reaperosc)
  - [Installation](#installation-reaperosc)
  - [Features](#features-reaperosc)
- [Workflow](#workflow)
  - [How to use BlenderOSC and ReaperOSC together](#how-to-use-blenderosc-and-reaperosc-together)
  - [Some use cases and suggestions](#some-use-cases-and-suggestions)
  - [Some tips and helpful hints](#some-tips-and-helpful-hints)
  - [Other DAWs](Other-DAWs)

## Overview

BlenderOSC is a Blender add-on that enables you to send and receive OSC messages from Reaper. You can use OSC nodes and Blender data nodes to create and manipulate OSC messages with different data types and formats. You can also use virtual MIDI ports to communicate with Reaper via ReaLearn plugin.

ReaperOSC is a Reaper script or action that enables you to send and receive OSC messages from Blender. You can use ReaLearn mappings and VST parameters or Reaper actions to create and manipulate OSC messages with different data types and formats. You can also use virtual MIDI ports to communicate with Blender via NodeOSC addon.

[Return to top](#table-of-contents)

## BlenderOSC

BlenderOSC is a Blender add-on that enables you to send and receive OSC messages from Reaper. You can use OSC nodes and Blender data nodes to create and manipulate OSC messages with different data types and formats. You can also use virtual MIDI ports to communicate with Reaper via ReaLearn plugin.

### Installation (BlenderOSC)

To install BlenderOSC, follow these steps:

- Download the latest release of BlenderOSC from here: https://github.com/maybites/blender.NodeOSC/releases
- Open Blender and go to Edit > Preferences > Add-ons
- Click on Install... button and browse to the downloaded zip file
- Enable the add-on by checking the box next to Node: NodeOSC
- Save your preferences

[Return to top](#table-of-contents)

### Features (BlenderOSC)

BlenderOSC has the following features:

- It enables NodeOSC addon in the preferences panel and creates a new node tree of type OSC.
- It adds an OSC server node and an OSC client node and sets their ports and address patterns. It also adds a panel in the N panel that shows the status and settings of the OSC server and client.
- It scans the ReaLearn mappings in Reaper and generates corresponding OSC input nodes and output nodes in Blender, with the correct data type, format, address pattern, and arguments. It also connects the OSC input nodes to the OSC server node, and the OSC output nodes to the OSC client node.
- It scans the ReaLearn mappings in Reaper and generates corresponding Blender data nodes in Blender, such as compositor nodes, geometry nodes, material nodes, etc. with the correct data type, format, value range, and name. It also connects the Blender data nodes to the OSC input nodes and output nodes.
- It detects the available MIDI devices on your system and creates virtual MIDI ports that match them. It also sets the input and output ports of NodeOSC to match the virtual MIDI ports.
- It provides a user interface for selecting and editing the OSC nodes and Blender data nodes, as well as connecting them to other nodes. It also provides options for saving and loading presets, refreshing and syncing with Reaper, and enabling or disabling feedback.

[Return to top](#table-of-contents)

## ReaperOSC

ReaperOSC is a Reaper script or action that enables you to send and receive OSC messages from Blender. You can use ReaLearn mappings and VST parameters or Reaper actions to create and manipulate OSC messages with different data types and formats. You can also use virtual MIDI ports to communicate with Blender via NodeOSC addon.

### Installation (ReaperOSC)

To install ReaperOSC, follow these steps:

- Download the ReaperOSC script or action from here: https://github.com/maybites/ReaperOSC/releases
- Open Reaper and go to Actions > Show action list
- Click on Load... button and browse to the downloaded script or action file
- Assign a shortcut key or a toolbar button to the script or action if you want
- Close the action list

[Return to top](#table-of-contents)

### Features (ReaperOSC)

ReaperOSC has the following features:

- It loads ReaLearn plugin as an FX on a track or on the master track.
- It scans the OSC nodes or Blender data nodes in Blender and generates corresponding ReaLearn mappings in Reaper, with the correct source, target, mode, range, feedback, address pattern, and arguments. It also generates corresponding VST parameters or Reaper actions in Reaper, with the correct data type, format, value range, and name.
- It detects the available MIDI devices on your system and creates virtual MIDI ports that match them. It also sets the input and output ports of ReaLearn to match the virtual MIDI ports.
- It registers a handler function to be called every frame and sends the values of the ReaLearn mappings as OSC messages to Blender.

[Return to top](#table-of-contents)

## Workflow

BlenderOSC and ReaperOSC are designed to work together seamlessly and provide a powerful integration between Blender and Reaper. You can use them to control various aspects of both applications with live feedback, and create complex interactions between them using different data types and formats.

### How to use BlenderOSC and ReaperOSC together

To use BlenderOSC and ReaperOSC together, follow these steps:

- Install BlenderOSC and ReaperOSC as described above.
- Open Blender and create a new node tree of type OSC. You can also use an existing node tree or load a preset.
- Open Reaper and load ReaLearn plugin as an FX on a track or on the master track. You can also use an existing ReaLearn instance or load a preset.
- In Blender, run the OSC server by clicking on Run Server button in the BlenderOSC panel. You should see a message saying "Server running" in the panel.
- In Reaper, run the ReaperOSC script or action by using the shortcut key or toolbar button that you assigned. You should see a message saying "Script running" in the console.
- In Blender, run the OSC client by clicking on Run Client button in the BlenderOSC panel. You should see a message saying "Client running" in the panel.
- In Reaper, enable feedback in ReaLearn by checking the box next to Feedback enabled in the ReaLearn panel.
- Now you can start sending and receiving OSC messages between Blender and Reaper. You can use OSC nodes and Blender data nodes in Blender to create and manipulate OSC messages with different data types and formats. You can also use ReaLearn mappings and VST parameters or Reaper actions in Reaper to create and manipulate OSC messages with different data types and formats. You should see live feedback in both applications as you change the values of the nodes or mappings.
- To stop sending and receiving OSC messages between Blender and Reaper, you can stop the OSC server, client, and script by clicking on Stop Server, Stop Client, and Stop Script buttons in BlenderOSC and ReaperOSC panels respectively.

[Return to top](#table-of-contents)

### Some use cases and suggestions

BlenderOSC and ReaperOSC can be used for various purposes that would otherwise be impossible or difficult with Blender or Reaper alone. Here are some examples of what you can do with them:

- Create dynamic soundtracks or sound effects for your animations or videos in Blender by controlling different aspects of your audio tracks or FX in Reaper with OSC messages based on your animation data or scene properties.
- Synchronize your music or audio with your visuals or effects in Blender by controlling different aspects of your 3D models or scenes in Blender with OSC messages based on your audio data or parameters.
- Manipulate your 3D models or scenes in Blender with sound or music by controlling different aspects of your geometry nodes or material nodes in Blender with OSC messages based on your MIDI input or output devices.
- Generate visuals or effects from sound or music by controlling different aspects of your compositor nodes or shader nodes in Blender with OSC messages based on your audio analysis or synthesis tools in Reaper.
- Experiment with different musical or visual styles or genres by controlling different aspects of your instruments or FX in Reaper with OSC messages based on your random or procedural generation tools in Blender.
- Learn about sound synthesis or signal processing by controlling different aspects of your synthesizers or processors in Reaper with OSC messages based on your mathematical or logical functions in Blender.

[Return to top](#table-of-contents)

### Some tips and helpful hints

BlenderOSC and ReaperOSC are powerful and flexible tools that can be customized and extended to suit your needs and preferences. Here are some tips and helpful hints to make the most out of them:

- You can edit the OSC nodes and Blender data nodes in Blender to change their data type, format, address pattern, arguments, value range, name, etc. You can also add new nodes or delete existing nodes as you wish. You can also use node groups to organize your nodes and create reusable presets.
- You can edit the ReaLearn mappings and VST parameters or Reaper actions in Reaper to change their source, target, mode, range, feedback, address pattern, arguments, name, etc. You can also add new mappings or delete existing mappings as you wish. You can also use ReaLearn presets to organize your mappings and create reusable presets.
- You can edit the BlenderOSC and ReaperOSC settings and options in Blender and Reaper to change their port, address pattern, feedback, etc. You can also save and load your settings and options as presets.
- You can use different OSC address patterns and arguments to create different types of OSC messages with different data types and formats. You can also use wildcards or regular expressions to match multiple OSC messages with a single OSC node or mapping.
- You can use different MIDI message types and channels to create different types of MIDI messages with different data types and formats. You can also use MIDI learn or MIDI map functions to assign MIDI messages to OSC nodes or mappings easily.
- You can use different VST parameters or Reaper actions to control different aspects of your audio tracks or FX in Reaper. You can also use automation or modulation functions to automate or modulate your VST parameters or Reaper actions with OSC messages.
- You can use different Blender data nodes to control different aspects of your 3D models or scenes in Blender. You can also use drivers or modifiers to drive or modify your Blender data nodes with OSC messages.

[Return to top](#table-of-contents)

## Other DAWs

Here are some ways you may be able to use some of the functions of BlenderOSC with other DAWs like Cubase or Ableton Live, even if you do not use Reaper.

- A user might be able to use BlenderOSC with other DAWs that support OSC communication by setting up the OSC server and client in BlenderOSC and the corresponding OSC devices or plugins in the other DAWs. The user would need to make sure that the port and address pattern of the OSC server and client match the port and address pattern of the OSC devices or plugins in the other DAWs. The user would also need to create OSC nodes and Blender data nodes in BlenderOSC that match the OSC messages that the other DAWs send and receive.
- A user might be able to use BlenderOSC with other DAWs that support MIDI communication by setting up the virtual MIDI ports in BlenderOSC and the corresponding MIDI devices or plugins in the other DAWs. The user would need to make sure that the name of the virtual MIDI ports match the name of the MIDI devices or plugins in the other DAWs. The user would also need to create OSC nodes and Blender data nodes in BlenderOSC that match the MIDI messages that the other DAWs send and receive.

[Return to top](#table-of-contents)
