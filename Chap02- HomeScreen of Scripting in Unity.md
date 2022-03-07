## HomeScreen of Scripting in Unity

Once your editor of choice opens up, you’ll be greeted by the following:

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour{

//use this for initialization
void Start(){

}

//update is called once per frame
void Update(){

}
```

This is the default class Unity generates for new scripts. It’s derived from the base class MoniBehavious which makes sure this script will be running in the game loop and has additional functionality to react to certain events. If you come from the iOS world, this object is the equivalent of a UIViewController. Unity calls several methods in a predetermined order as the script is running. Here are a few of the most common ones:

- Start() : This method will get called once right before the script gets its first update.
    - Here you can initialize prefabs from your 2D platformer game
- Update() : While the game is running and the script is enabled, this method will get fired every frame
    - Here you can give the input methods to your player character in 2D platformer game
- OnDestroy() : This method gets called right before the GameObject this script is attached to gets destroyed
    - Here you can write the code for any special powerups that you want to destroy in few seconds in your 2D platformer game
- OnCollisionEnter() : When the collider or rigidbody this script is attached to touches another collider or rigidbody, this method gets called
    - Here you can use any line of code for different types of enemies in your 2D platformer game
- FixedUpdate() : It is frame rate independent and should be used when working with Rigidbodies. Instead of running as fast as possible, this method will be fired at a constant interval
    - Here you can write all your physics-related codes such as Player jump, Player movement etc.
