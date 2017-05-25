# CodeCampUnity3D Workshop
set of assets to help build a rolling the ball tutorial.

![alt text](https://github.com/RodrigoFigueroaM/CodeCampUnity3D/screenshots)
```c#
source CurvesEnv/bin/activate
```
steps
1.- create new project
2.- add the assets folder to project
3.- save scene under scenes 
4.- create plane. 
	* GameObject->3D Object -> Plane
	* change dimensions of plane 
	* under inspector change scale  of plane x and z to 2.0
		(SCREENSHOT)
5.- create player 
	* GameObject-> 3D Object -> Sphere
	* change y position of sphere from 0 to 0.5 (SCREENSHOTS TO SHOW DIFFERENCE)
	* add rigid body through inspector 
6.- change color of plane.
	* drag and drop the Ground material onto the plane (gif)
7.- add script to player
	* under inspector add script to player(sphere)
8.- start scripting
	double click on PlayerController script
	I have provided a way to get the Rigid body already included in the sphere player
	*** we are using Fixed update because we will be calling this function every frame rate
	include input so we can move around.
——————————————————————————————————————————————————————————————————————————————————————————
	void FixedUpdate ()
	{	
float horizontal = Input.GetAxis ("Horizontal");
		float vertical = Input.GetAxis ("Vertical");

		Vector3 movement = new Vector3 (horizontal, 0.0f, vertical);

		rb.AddForce (movement * speed);
	}
——————————————————————————————————————————————————————————————————————————————————————————
	to get input we use Input get Axis this allows to use AWSD and arrows for movement

	we have o create a new vector to move out y is = 0 because we are not moving in the y direction
	
	add the movement force 
9.- change speed public field in inspector(GIF)
10.- test it out press play 
11.- camera need to follow ball 
	* position camera to above the player sphere position 
	* select camera and transform to position 0 , 10 , 0; then rotate 75 on x axis(GIF)
	* add script to camera to follow ball
	* inspector -> add component-> CameraController
	* explanation?

	* add sphere to public field on camera inspector (GIF)
——————————————————————————————————————————————————————————————————————————————————————————

void Start ()
	{
		distance = this.transform.position - go.transform.position;
	}

void LateUpdate ()
	{
		this.transform.position = go.transform.position + distance;
	}
——————————————————————————————————————————————————————————————————————————————————————————

	* test it out press play 

12.- Drag and drop walls 
	adjust walls slightly x =0.5193725 y = 1 z = 2.8385

13.- add targets (drag and drop gif )
14.- pick up targets 
	* add to PlayerController script
	*add tag to prefab (gif)
 	*add tag to public field——————————————————————————————————————————————————————————————————————————————————————————

	void OnTriggerEnter( Collider other)
	{
		if (other.gameObject.CompareTag (tag))
		{
			other.gameObject.SetActive (false);
		}
	}	 

——————————————————————————————————————————————————————————————————————————————————————————

	
we have a game!!!
