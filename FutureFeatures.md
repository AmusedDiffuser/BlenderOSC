# Future Features Brainstorm

## General 

  - Android/iPhone OSC controller app
  
  - Android/iPhone remote/presenter app

  - Android/iPhone macro control and project overview app

  - text input box allowing the user to paste an algorithm or code snippet either from writting it themselves, an example from an official list of examples, or generated for them by AI. This would allow users with minimal experience to request a particular setup in plain English and have their friend or favorite AI chatbot write code that would make the necessary connections and labels.
  
  - extensive documentation allowing experienced users or AI chat box to review the documentation and write precise instructions/algorithms/code for the above mentioned text input box
  
  - a simple GUI app allowing the user to define their objectives and creative concepts, as well as document complex projects for future reference. this would provide clarity for the user regarding their vision and also help create a clear and concise explanation for any chatbot that was asked to assist in bringing these concepts to life.

## BlenderOSC

  - interface buttons in the panel for the following actions 
     - create new material node group 
     - create new geometry node group
     - create new compositor node group
     - create new simulation note group
     
  - each of these buttons should launch a pop-up window prompting the user to label the new grou and select either "leave unconnected", or identify an OSC device which will be connected.
  
  - each of these pop-up windows should allow the user to specify the number of connections for the node group input
  
  - each of these pop-up Windows should include a text input box that would allow a user to paste additional variables or argument
  
  
  
## ReaperOSC 

   - add basic "music visualizer" preset action that prompts a user for the number of frequency splits, then creates a corresponding number of channels, as well as a folder track that they can be collapsed into. the folder track should also include an additional "receive channel" that splits that frequency ranges for the corresponding channels, creates the necessary sends to those channels, and disables its own "master send". the action should then add unto each relevant channel a tool that will measure the volume of that frequency band and translate it to OSC signals that can be passed to Blender and create or update any relevant relearn instances
   
   - JSFX plugin with adjustable display, attack/hold/release times, trim/sensitivity knob, TCP/MCP display mode with draggable sensitivity adjustment, ond OSC output!
