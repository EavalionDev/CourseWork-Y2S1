# Connor Howard's Learning Journal

## 13/10/20
I started off by programming the enemy spawner script. This was achieved by roatating an object around a centre point and then having a two integers be incrimented. once one integer hits a value of 60 to count for a second it would randomly set the value of another integer and then reset the value of the first to 0 to repeat this process once every second. I then have it set so that if the second integer that is being incremented becomes greater than or equal to the value of the randomly set variable it would spawn an enemy and then slightly increase the speed of the objects rotation to help keep the timing and location of spawning random.
![a](https://user-images.githubusercontent.com/72077595/105555741-f4e60d80-5d01-11eb-8b09-24949bce9ba6.PNG)

## 20/10/20
Lesson - Programming enemy movement script
Once the spawner script was in place I then moved on to creating the enemy movement script. The method I used for this was by using Ray casting while having the enemy look in the direction of the player, then applied force to move the enemy around. I ran into an issue with getting the enemy to contantly look at the player and originally had calculated the distance between the enemy and the player object, then tried to use this value as the axis values for a vector3 variable. I got around this by instead having the enemy locate the player object through "player = GameObject.Find("Player");" inside the start method. I then would use the raycast to hit the player and use "rb.AddForce(new Vector3(transform.forward.x * speed * Time.deltaTime, 0, transform.forward.z * speed * Time.deltaTime), ForceMode.Impulse);".
![b](https://user-images.githubusercontent.com/72077595/105568356-9a17da80-5d30-11eb-9b62-6df5b1684239.PNG)

## 27/10/20
Lesson - Started work on a player movement script

## 03/11/20
Free time - Researched programming shaders

## 4/11/20
Free time - Finished the materialise effect for 3D

## 10/11/20
Lesson - Reworked player movement script first half

## 12/11/20
Free time - Researched different methods to make objects move in Unity

## 13/11/20
Free time - Worked on shrinking enemies when they get pulled into a suction zone for my 3D game

## 17/11/20
Lesson - Finished player movement script

## 19/11/20
Free time - Researched how get the relative direction of a dynamic Vector3 from one script and use to direct force on to an enemy object in another script

## 24/11/20
Lesson - Set Up and worked on Pick up items script

## 28/11/20
Free time - Implemented a reference to a Vector3 direction to add force to an enemy in my 3D game

## 1/12/20
Lesson - Created a Score script then linked it to the pick up script to have them work together

## 10/12/20
Free time - Implemented scripts into project making sure to link them with the use of public static variables 
