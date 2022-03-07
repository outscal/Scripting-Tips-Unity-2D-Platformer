## Scripting in Unity

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

```C#
public float acceleration;
public float maxSpeed;
private Rigidbody rigidBody;
private KeyCode[] inputKeys;
private Vector3[] directionsForKeys;

void Start () {
  inputKeys = new KeyCode[] { KeyCode.W, KeyCode.A, KeyCode.S, KeyCode.D };
  directionsForKeys = new Vector3[] { Vector3.forward, Vector3.left, Vector3.back, Vector3.right };
  rigidBody = GetComponent<Rigidbody>();
  Debug.Log("Player is Moving"+ rigidBody);
}
```

- Update() : While the game is running and the script is enabled, this method will get fired every frame
    - Here you can give the input methods to your player character in 2D platformer game
- Awake() : Awake function is called when the script instance is being loaded. Unity calls Awake only once during the lifetime of the script instance. A script's lifetime lasts until the Scene that contains it is unloaded. If the Scene is loaded again, Unity loads the script instance again, so Awake will be called again

```C#
void Awake()
    {
        // Awake is called even if the script is disabled. 
    }
```
- OnDestroy() : This method gets called right before the GameObject this script is attached to gets destroyed
    - Here you can write the code for any special powerups that you want to destroy in few seconds in your 2D platformer game
- OnCollisionEnter() : When the collider or rigidbody this script is attached to touches another collider or rigidbody, this method gets called
    - Here you can use any line of code for different types of enemies in your 2D platformer game
- FixedUpdate() : It is frame rate independent and should be used when working with Rigidbodies. Instead of running as fast as possible, this method will be fired at a constant interval
    - Here you can write all your physics-related codes such as Player jump, Player movement etc.

```C#
void FixedUpdate () {
  for (int i = 0; i < inputKeys.Length; i++){
    var key = inputKeys[i];

    // 2
    if(Input.GetKey(key)) {
      // 3
      Vector3 movement = directionsForKeys[i] * acceleration * Time.deltaTime;
      movePlayer(movement);
      Debug.Log(movePlayer);
    }
  }
}

void movePlayer(Vector3 movement) {
  if(rigidBody.velocity.magnitude * acceleration > maxSpeed) {
    rigidBody.AddForce(movement * -1);
  } else {
    rigidBody.AddForce(movement);
  }
}
```
### Difference between Start(), Awake() & Update() functions

```C#

using UnityEngine;

Make sure that your Player Gameobject is assigned this script and is inactive at the start of the game.

public class Example1 : MonoBehaviour
{
    void Awake()
    {
        Debug.Log("Example1.Awake() was called");
    }

    void Start()
    {
        Debug.Log("Example1.Start() was called");
    }

    void Update()
    {
        if (Input.GetKeyDown("b"))
        {
            Debug.Log("b key was pressed");
        }
    }
}
```
