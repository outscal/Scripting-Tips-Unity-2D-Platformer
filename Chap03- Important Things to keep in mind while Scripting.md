## Important things to keep in mind while Scripting

- The Update function is the place to put code that will handle the frame update for the GameObject. This might include movement, triggering actions and responding to user input, basically anything that needs to be handled over time during gameplay.
- To enable the Update function to do its work, it is often useful to be able to set up variables, read preferences and make connections with other GameObjects before any game action takes place.
- The Start function will be called by Unity before gameplay begins (i.e, before the Update function, is called for the first time) and is an ideal place to do any initialization.
