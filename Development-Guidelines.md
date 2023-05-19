# Development concepting and guidelines 

## Table of contents 
- [Signal flow](Brief-summary-of-signal-flow)

- [Approach](Brief-summary-of-why this-approach-is-good:)




According to the search results, **Reaper DAW scripting and remote control** is the process of creating and running scripts that can automate tasks, extend functionality, and control Reaper from external devices or applications. Reaper supports several scripting languages, such as **EEL2**, **Lua**, and **Python**, and provides a comprehensive API for accessing Reaper's data and functions³. Reaper also supports various protocols for remote control, such as **MIDI**, **OSC**, and **Web Remote**².

With this in mind, I can suggest some different approaches that could be employed to create bidirectional communications between Reaper and Blender, allowing them to share audio and MIDI data, as well as possibly implementing OSC or HUI standards:

Approach one: using MIDI protocol

This approach would involve sending and receiving MIDI messages between Reaper and Blender, using either a virtual MIDI port or a physical MIDI interface. You would need to write scripts in both Reaper and Blender that can encode and decode MIDI messages, and map them to the desired actions or parameters. For example, you could use MIDI note messages to trigger sounds or animations, MIDI control change messages to adjust volume or rotation, MIDI program change messages to switch between scenes or tracks, etc. You could also use MIDI sysex messages to send custom data between the applications. This approach would require some knowledge of MIDI protocol and scripting languages, but it would be relatively simple and compatible with most devices and applications.

Approach two: using OSC protocol

This approach would involve sending and receiving OSC messages between Reaper and Blender, using a network connection. You would need to write scripts in both Reaper and Blender that can encode and decode OSC messages, and map them to the desired actions or parameters. For example, you could use OSC address patterns to identify specific objects or functions, OSC arguments to pass values or data, OSC bundles to group multiple messages together, etc. You could also use OSC queries to request information from the other application. This approach would require some knowledge of OSC protocol and scripting languages, but it would be more flexible and expressive than MIDI protocol.

Approach three: using Web Remote protocol

This approach would involve using Reaper's built-in Web Remote feature to control Reaper from Blender, using a web browser. You would need to write a web page that can communicate with Reaper's web server, using HTML, CSS, JavaScript, and AJAX. You would also need to write a script in Blender that can load the web page in a panel or a window, and interact with it using mouse or keyboard events. For example, you could use buttons, sliders, menus, text boxes, etc. to control Reaper's transport, mixer, plugins, etc. You could also use web sockets to receive feedback from Reaper's web server. This approach would require some knowledge of web development and scripting languages, but it would be easy to customize and integrate with Blender's user interface.

Source: Conversation with Bing, 5/19/2023

(1) REAPER | ReaScript. https://www.reaper.fm/sdk/reascript/reascript.php.

(2) Reaper DAW 101 Part 6:- Control Surfaces, OSC and Web Remote. https://www.youtube.com/watch?v=QI2jK94Tv1g.

(3) Control Surface Integration (CSI) Technical Feature Discussion - Cockos. https://forum.cockos.com/showthread.php?t=183143.



Based on the search results, I can synthesize a specific approach that would allow MIDI or OSC data from Reaper to have live control over the values of various nodes in Blender, for example compositor nodes, geometry nodes, and material nodes. And that would also allow the output of such nodes and automation drivers in Blender to control parameters of a VST synthesizer or effect in Blender. Here is my suggestion:

Approach: using ReaLearn and NodeOSC

This approach would involve using ReaLearn plugin in Reaper to create MIDI/OSC learn mappings for controlling VST parameters or Reaper actions, and using NodeOSC addon in Blender to create OSC nodes for receiving and sending OSC messages. You would also need to use a virtual MIDI port or a physical MIDI interface to connect Reaper and Blender.

Brief explanation:

- In Reaper, you would load ReaLearn plugin as an FX on a track or on the master track. You would then create mappings for the VST parameters or Reaper actions that you want to control from Blender. You would also create mappings for the VST parameters or Reaper actions that you want to control with your external controller (such as a MIDI keyboard or a knob). You would set the source and target of each mapping, as well as the mode, range, feedback, and other options. You would also set the input and output ports of ReaLearn to match your MIDI device and your virtual MIDI port.

- In Blender, you would enable NodeOSC addon in the preferences panel. You would then create a new node tree of type OSC. You would add an OSC server node and set its port and address pattern. You would also add an OSC client node and set its port and address pattern. You would then add OSC input nodes and OSC output nodes as needed. You would connect the OSC input nodes to the OSC server node, and the OSC output nodes to the OSC client node. You would also connect the OSC input nodes and output nodes to other nodes that manipulate Blender data, such as compositor nodes, geometry nodes, material nodes, etc. You would set the data type and format of each OSC input node and output node, as well as the address pattern and arguments.

- To control VST parameters or Reaper actions from Blender, you would send OSC messages from Blender's OSC output nodes to Reaper's ReaLearn plugin via the virtual MIDI port. The OSC messages would match the address patterns and arguments of the ReaLearn mappings that you created in Reaper. The ReaLearn plugin would then translate the OSC messages into MIDI messages or REAPER actions and apply them to the VST parameters or Reaper actions.

- To control Blender data from Reaper, you would send MIDI messages from Reaper's ReaLearn plugin to Blender's OSC input nodes via the virtual MIDI port. The MIDI messages would match the data type and format of the OSC input nodes that you created in Blender. The NodeOSC addon would then translate the MIDI messages into OSC messages and apply them to the Blender data.

## Brief summary of signal flow

- From external controller to VST parameters or Reaper actions: External controller -> MIDI device -> ReaLearn plugin -> VST parameters or Reaper actions

- From external controller to Blender data: External controller -> MIDI device -> ReaLearn plugin -> virtual MIDI port -> NodeOSC addon -> Blender data

- From VST parameters or Reaper actions to Blender data: VST parameters or Reaper actions -> ReaLearn plugin -> virtual MIDI port -> NodeOSC addon -> Blender data

- From Blender data to VST parameters or Reaper actions: Blender data -> NodeOSC addon -> virtual MIDI port -> ReaLearn plugin -> VST parameters or Reaper actions

[return to top](Development concepting-and-guidelines)

## Brief summary of why this approach is good

- This approach is feasible because it uses existing tools that are compatible with Reaper and Blender, and that provide comprehensive features for creating MIDI/OSC learn mappings and OSC nodes.

- This approach is expandable because it allows you to create multiple mappings and nodes for different purposes, and to customize them according to your needs and preferences.

- This approach is powerful because it allows you to control various aspects of both applications with live feedback, and to create complex interactions between them using different data types and formats.

[return to top](Development concepting-and-guidelines)

Source: Conversation with Bing, 5/19/2023

(1) AddRoutes | JPfeP. http://www.jpfep.net/pages/addroutes/.

(2) maybites/blender.NodeOSC: blender OSC addon to be used with nodes - GitHub. https://github.com/maybites/blender.NodeOSC.

(3) Midi to OSC to Blender Animation Nodes Armature Test - YouTube. https://www.youtube.com/watch?v=DLNieIAWClM.

(4) MIDI to OSC to Blender Animation Nodes Piano components. https://www.youtube.com/watch?v=vOWT3EHR4d0.



## Here are some potential ways that a custom blender add-on and a custom Reaper script or action could simplify the user experience for setting this up:

- A custom blender add-on that can automatically create and configure OSC nodes based on the VST parameters or Reaper actions that you want to control or receive feedback from. For example, the add-on could scan the ReaLearn mappings in Reaper and generate corresponding OSC input nodes and output nodes in Blender, with the correct data type, format, address pattern, and arguments. The add-on could also provide a user interface for selecting and editing the OSC nodes and connecting them to other nodes.

- A custom blender add-on that can automatically create and configure Blender data nodes based on the VST parameters or Reaper actions that you want to control or receive feedback from. For example, the add-on could scan the ReaLearn mappings in Reaper and generate corresponding compositor nodes, geometry nodes, material nodes, etc. in Blender, with the correct data type, format, value range, and name. The add-on could also provide a user interface for selecting and editing the Blender data nodes and connecting them to other nodes.

- A custom blender add-on that can automatically create and configure virtual MIDI ports for communicating with Reaper. For example, the add-on could detect the available MIDI devices on your system and create virtual MIDI ports that match them. The add-on could also set the input and output ports of NodeOSC to match the virtual MIDI ports.

- A custom Reaper script or action that can automatically create and configure ReaLearn mappings based on the OSC nodes or Blender data nodes that you want to control or receive feedback from. For example, the script or action could scan the OSC nodes or Blender data nodes in Blender and generate corresponding ReaLearn mappings in Reaper, with the correct source, target, mode, range, feedback, and other options. The script or action could also provide a user interface for selecting and editing the ReaLearn mappings.

- A custom Reaper script or action that can automatically create and configure VST parameters or Reaper actions based on the OSC nodes or Blender data nodes that you want to control or receive feedback from. For example, the script or action could scan the OSC nodes or Blender data nodes in Blender and generate corresponding VST parameters or Reaper actions in Reaper, with the correct data type, format, value range, and name. The script or action could also provide a user interface for selecting and editing the VST parameters or Reaper actions.

- A custom Reaper script or action that can automatically create and configure virtual MIDI ports for communicating with Blender. For example, the script or action could detect the available MIDI devices on your system and create virtual MIDI ports that match them. The script or action could also set the input and output ports of ReaLearn to match the virtual MIDI ports.

[return to top](Development concepting-and-guidelines)

## Here is a possible description of the features and design of each individual tool, as well as the workflow of using them together:

- The blender add-on would be called **BlenderOSC** and it would have the following features and design:

  - It would enable NodeOSC addon in the preferences panel and create a new node tree of type OSC.

  - It would add an OSC server node and an OSC client node and set their ports and address patterns. It would also add a panel in the N panel that shows the status and settings of the OSC server and client.

  - It would scan the ReaLearn mappings in Reaper and generate corresponding OSC input nodes and output nodes in Blender, with the correct data type, format, address pattern, and arguments. It would also connect the OSC input nodes to the OSC server node, and the OSC output nodes to the OSC client node.

  - It would scan the ReaLearn mappings in Reaper and generate corresponding Blender data nodes in Blender, such as compositor nodes, geometry nodes, material nodes, etc. with the correct data type, format, value range, and name. It would also connect the Blender data nodes to the OSC input nodes and output nodes.

  - It would detect the available MIDI devices on your system and create virtual MIDI ports that match them. It would also set the input and output ports of NodeOSC to match the virtual MIDI ports.

  - It would provide a user interface for selecting and editing the OSC nodes and Blender data nodes, as well as connecting them to other nodes. It would also provide options for saving and loading presets, refreshing and syncing with Reaper, and enabling or disabling feedback.

- The Reaper script or action would be called **ReaperOSC** and it would have the following features and design:

  - It would load ReaLearn plugin as an FX on a track or on the master track.

  - It would scan the OSC nodes or Blender data nodes in Blender and generate corresponding ReaLearn mappings in Reaper, with the correct source, target, mode, range, feedback, and other options.

  - It would scan the OSC nodes or Blender data nodes in Blender and generate corresponding VST parameters or Reaper actions in Reaper, with the correct data type, format, value range, and name.

  - It would detect the available MIDI devices on your system and create virtual MIDI ports that match them. It would also set the input and output ports of ReaLearn to match the virtual MIDI ports.

  - It would provide a user interface for selecting and editing the ReaLearn mappings, VST parameters, or Reaper actions. It would also provide options for saving and loading presets, refreshing and syncing with Blender, and enabling or disabling feedback.

- The workflow of using these tools together would be as follows:

  - The user would install both tools on their system and enable them in their respective applications.

  - The user would launch both applications and make sure they are connected via a network connection or a physical MIDI interface.

  - The user would run the ReaperOSC script or action in Reaper. This would create ReaLearn mappings and VST parameters or Reaper actions based on the OSC nodes or Blender data nodes in Blender. The user could then edit these mappings or parameters as needed.

  - The user would run the BlenderOSC add-on in Blender. This would create OSC nodes and Blender data nodes based on the ReaLearn mappings in Reaper. The user could then edit these nodes as needed.

  - The user could then control VST parameters or Reaper actions from Blender by sending OSC messages from Blender's OSC output nodes to Reaper's ReaLearn plugin via the virtual MIDI port. The user could also control Blender data from Reaper by sending MIDI messages from Reaper's ReaLearn plugin to Blender's OSC input nodes via the virtual MIDI port. The user could also receive feedback from both applications via MIDI/OSC feedback.



## Here are some detailed notes for the programmer who will create these tools:

### - For the blender add-on (BlenderOSC):

  - The add-on should be written in Python and use the Blender Python API and the NodeOSC addon API. It should also use the oscPy and python-osc modules for handling OSC messages and the rtmidi module for handling MIDI messages.

  - The add-on should register a new panel in the N panel that shows the status and settings of the OSC server and client. It should also register a new operator for running the add-on and a new property group for storing the add-on settings and presets.

  - The add-on should enable NodeOSC addon in the preferences panel and create a new node tree of type OSC. It should also add an OSC server node and an OSC client node and set their ports and address patterns. The ports and address patterns should be configurable by the user in the add-on settings.

  - The add-on should scan the ReaLearn mappings in Reaper by sending an OSC query message to Reaper's ReaLearn plugin via the virtual MIDI port. The ReaLearn plugin should respond with an OSC message containing the information about the mappings, such as the source, target, mode, range, feedback, address pattern, and arguments. The add-on should parse this message and store the information in a list or a dictionary.

  - The add-on should generate corresponding OSC input nodes and output nodes in Blender based on the ReaLearn mappings. It should also connect the OSC input nodes to the OSC server node, and the OSC output nodes to the OSC client node. The data type, format, address pattern, and arguments of each OSC node should match those of the ReaLearn mapping. The add-on should also generate corresponding Blender data nodes in Blender based on the ReaLearn mappings, such as compositor nodes, geometry nodes, material nodes, etc. The data type, format, value range, and name of each Blender data node should match those of the ReaLearn mapping. The add-on should also connect the Blender data nodes to the OSC input nodes and output nodes.

  - The add-on should detect the available MIDI devices on the system by using the rtmidi module. It should also create virtual MIDI ports that match them by using the rtmidi module. It should also set the input and output ports of NodeOSC to match the virtual MIDI ports by using the NodeOSC addon API.

  - The add-on should provide a user interface for selecting and editing the OSC nodes and Blender data nodes, as well as connecting them to other nodes. It should also provide options for saving and loading presets, refreshing and syncing with Reaper, and enabling or disabling feedback. The user interface should be intuitive and user-friendly.

  - The add-on should handle errors and exceptions gracefully by using try-except blocks and logging messages. It should also provide helpful messages and tooltips for the user.

### - For the Reaper script or action (ReaperOSC):

  - The script or action should be written in Lua or EEL2 and use the Reaper API and ReaScript API. It should also use the oscPy or python-osc modules for handling OSC messages and rtmidi module for handling MIDI messages.

  - The script or action should load ReaLearn plugin as an FX on a track or on the master track by using Reaper API functions such as TrackFX_AddByName or TrackFX_GetByName.

  - The script or action should scan the OSC nodes or Blender data nodes in Blender by sending an OSC query message to Blender's NodeOSC addon via the virtual MIDI port. The NodeOSC addon should respond with an OSC message containing the information about the nodes, such as the data type, format, value range, name, address pattern, and arguments. The script or action should parse this message and store the information in a table or a dictionary.

  - The script or action should generate corresponding ReaLearn mappings in Reaper based on the OSC nodes or Blender data nodes. It should set the source, target, mode, range, feedback, and other options of each mapping by using ReaScript API functions such as SetExtState or GetExtState. The source and target of each mapping should match those of the OSC node or Blender data node. The script or action should also generate corresponding VST parameters or Reaper actions in Reaper based on the OSC nodes or Blender data nodes. It should set the data type, format, value range, and name of each parameter or action by using Reaper API functions such as TrackFX_SetParamNormalized or Main_OnCommand.

  - The script or action should detect the available MIDI devices on the system by using rtmidi module. It should also create virtual MIDI ports that match them by using rtmidi module. It should also set

the input and output ports of ReaLearn to match

the virtual MIDI ports by using ReaScript API functions such as SetExtState or GetExtState.

- The script or action should provide a user interface for selecting and editing

the ReaLearn mappings,

VST parameters,

or Reaper actions.

It should also provide options for saving

and loading presets,

refreshing

and syncing with Blender,

and enabling

or disabling feedback.

The user interface

should be intuitive

and user-friendly.

- The script

or action

should handle errors

and exceptions gracefully

by using pcall

or xpcall functions

and logging messages.


h

h

h

It should also provide helpful messages

and tooltips

for

the user.
