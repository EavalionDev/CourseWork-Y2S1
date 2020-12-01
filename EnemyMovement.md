# Enemy Movement
This is the second tutorial in a small series and if you are reading this I can assume you have completed the previous. In this tutorial I am going over how to make your newly
instantiated enemies move around the level as they chase the player. To do this we will be using "ray casting" to know when the enemy is looking at the player then add force to
push the enemy towards the players position.

## Unity Set Up
This tutorial will run under the assumption that you already have a player Gameobject within your scene, if not here are some short stpes to get one set up:
- Create a Capsule within the Heirarchy window
- Name the object "Player"
- Add a Rigidbody and a Capsule Collider to the object inside the inspector tab
- Using the same method shown in the previous tutorial make the "Player" object a prefab

In order to start this we will first need to create a script and attach it to the enemy prefab, to do this go into your "Scripts" folder and right click within the project window,
select "Create" then "C# Script". Once done name the script "EnemyMovement" and press enter. Next all there is to do it locate the enemy prefab in the project winow, double click 
the prefab to open it up within the scene view and then drag and drop the new "EnemyMovement" script into the prefabs inspector window.

## The Code
### Declaring Variables
Now everything is in place we can begin programming our script, double click the scipt within either the project or inspector window to open it up within "Microsoft Visual Studios".
Just like the previous tutorial we will want to declair the variables we plan on using for our script. We only need one public variable for access outside the script and that 
relates to the enemies speed, in-between the "start" method and "public class" type "public float speed;". Next we will want a few private variables, each variable we declare you
will want to declare the next on the line below the previous, using this next we will declare these variables "private Gameobject player;" and "private Rigidbody rb;" If done 
correctly the code should look something like this:
```
public class EnemyMovement : MonoBehaviour
{
    public float speed;
    private GameObject player;
    private Rigidbody rb;
    private float dir;

    // Start is called before the first frame update
    void Start()

```

## The Start Method
Inside the start method we will need to complete our refferences to the player and the enemies Rigidbody so we can use them within our movement method, first we will want to create
a reference to the player Gameobject as soon as the enemy spawns in, to do this type "player = GameObject.Find("Player");". The reason we do this in "Start" method and not "Update"
is because "Start" runs only one frame when the Gameobject has instantiated and because "GameObject.Find" is a rather performance heavy function to run every frame we can simply do
it in the "Start" method for the same result without causing any performance issues. The second line of code needed within "Start" is "rb = GetComponent<Rigidbody>();", this creates
a link to the objects Rigidbody component in the inspector and is used in "Start" for the same reason "GameObject.Find" is. Once done the "Start" method should look lioke this:
```
  void Start()
    {
        player = GameObject.Find("Player");
        rb = GetComponent<Rigidbody>();    
    }
```

## The Update Method
For this script we are going to run the majority of our code through a "Movement" method and have that method continously run through the "Update" method. to do this we need to first set
up the "Movement" method before we run it through "Update", Under the "Update" method type "void Movement()" then under this line add these curly braces "{}" and press enter in between them
so the order themselves in a similar fashion shown within the curley braces inside the "Start" and "Update" method. Now that we have created the new method we can go back into the 
"Update" method where you will want to type "Movement();", this will now run the new method every frame. This is how it should look after:
```
 // Update is called once per frame
    void Update()
    {
        Movement();
    }

    void Movement()
    {

    }
```
### The Movement Method
