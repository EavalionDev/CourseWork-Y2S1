# Player Movement
This is the third in a four part tutorial series and if you are reading this, I am under the assumption that you have completed the two previous tutorials. Within this tutorial
we are going to give the player GameObject movement by detecting inputs and applying force to the player GameObject.

## Unity Set Up
To get started all we will need to do is give the player GameObject that should already be inside the scene from the previous tutorial, using the method shown in the previous
tutorials create a script within the "Scripts" folder and name it "PlayerMovement". As stated above you should already have the player GameObject due to the previous tutorial
requiring one, heres a quick check list of all components the GameObject should contain within the inspector window just to be sure:

 - Transform
 - Mesh Filer (only if using standard unity shapes for prefab model)
 - Mesh Renderer
 - Capsule Collider
 - Rigidbody

Once every thing is in place simply double click the script to open it up in Microsoft Visual Studio so we can begin going through the programming.

## The Code
### Declaring Variables

As shown in previous tutorials we will need to declare the variables we want to use for our script first. By now you should be familiar with where the variables go and how they
should be formatted, using the same method declare the following variables:

- public float speed;
- private Rigidbody rb;
- private bool forward;
- private bool backward;
- private bool left;
- private bool right;

If positioned and formatted correctly it should look something like this:

```
public class PlayerMovement : MonoBehaviour
{
    public float speed;

    private Rigidbody rb;
    private bool forward;
    private bool backward;
    private bool left;
    private bool right;


    // Start is called before the first frame update
    void Start()
```
### Start Method

Inside the start method we arew going to create the linkway between our private Rigidbbody variable and the component within the inspector, to do this we use a function known as "GetComponent". Type "rb = GetComponent<Rigidbody>();" and this will create the link between the two. Last thing to do within the start function is to set the states (we want them to be false) at which the booleans will start with when the script first runs, to do this simply type out the boolean names and type " = false;" after tyhe name. Here is an example of the first boolean: "forward = false;", using this method and example fill out the rest of the boolean states, once complete it should look something like this:
 
 ```
     // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody>();
        forward = false;
        backward = false;
        left = false;
        right = false;
    }
```

### Update Method

Here inside the update method we are going to check for key inputs that will determain which direction we want force to be applied to the player moving it into the corrospionding direction. To do this we will need to make use of a bunch of "if" statements and set the booleans within them accordingly. The most commonly used set of key inputs for player movement by todays games are "W,A,S,D". So the first thing we will need to check for is input, to do this type  "if" and tap the "Tab" key twice which will format the syntax of the "if" statement for you, then fill in the brackets of the "if" statement with this "(Input.GetKey(KeyCode.W))", this will check for continous input from the "W" key using the "GetKey" function. Inside the curley brackets ("{}") type "forward = true;" which will set the boolean to true when this condition is set. Now that we have set up the "forward" boolean to true under the correct condition we will also want a very similar condition that simply turns it back off again when the there is no registered input with the "W" key. To do this copy the same "if" statement we just created and paste it on the lines below, once done simple add a "!" before "Input" inside the brackets and then change the boolean inside the curley brackets from "true" to "false". This will make sure the boolean is set to "false"  when the condition is not met. Now using the same method as shown above to set up both the input check and non input check for the "W" key, do the same with the "A,S,D" keys making sure you use the "left" boolean for the "A" key, "right" boolean for the "D" key and "backward" boolean for the "S" key. Once finished if done correctly it should look something like this:

```
   // Update is called once per frame
    void Update()
    {
        if (Input.GetKey(KeyCode.W))
        {
            forward = true;
        }
        if (!Input.GetKey(KeyCode.W))
        {
            forward = false;
        }
        if (Input.GetKey(KeyCode.A))
        {
            left = true;
        }
        if (!Input.GetKey(KeyCode.A))
        {
            left = false;
        }
        if (Input.GetKey(KeyCode.S))
        {
            backward = true;
        }
        if (!Input.GetKey(KeyCode.S))
        {
            backward = false;
        }
        if (Input.GetKey(KeyCode.D))
        {
            right = true;
        }
        if (!Input.GetKey(KeyCode.D))
        {
            right = false;
        }

    }
```

### FixedUpdate Method

We will want to use the "FixedUpdate" method to help handle our physics calculations better, to get this method set up within Visual Studios just under the "Update" method type "private void FixedUpdate()" then Visual Studio should automatically add the curley brackets if not simply add them in. 
