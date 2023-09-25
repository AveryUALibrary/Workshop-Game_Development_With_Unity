# Game Development in Unity PT 1

## Necessary Tools
* Unity (We will be using 2022.3.9f1)
* VS Code
* Git (Optional) (This will be used to backup code)
* Sprite Creation Software (Optional) (We will be using Piskel)

## Todo List

[ ] Create and Setup Game
[ ] Create a Player and Add Movement
[ ] Create a Platform and Implement Jumping

---

## Before We Start

Please make sure you have the following installed:
* Unity Hub
* Unity 2022.3.9f1
* VS Code

### Installing Unity Hub
* [Unity Hub](https://unity.com/download)
* [Linux Users](https://docs.unity3d.com/hub/manual/InstallHub.html#install-hub-linux)

Then install Unity 2022.3.9f1

### Installing VS Code
* [VS Code](https://code.visualstudio.com/download)

#### Installing VS Code Extensions
1. Open VS Code
2. Click on the Extensions icon (Ctrl + Shift + X) or (Cmd + Shift + X)
3. Search for C# and install the one by Microsoft

---

## Creating and Setting Up a Game

1. Open Unity Hub
2. Click on New Project
3. Name the project
4. Set the location to where you want to save the project
5. Set the template to 2D

### Configure Unity To Use VSCode

1. Inside of the unity project, go to Window > Package Manager
2. Change `Packages:` from `In Project` to `Unity Registry`
3. Search for `Visual Studio Code Editor`
4. Click on `Install`
5. Go to Edit > Preferences > External Tools
6. Change `External Script Editor` to `Visual Studio Code`

---

## Player Movement Code

### Variables

```csharp
// Inside Player Script
// Inside of class {Player} : MonoBehaviour

// frivate: Only accessible inside of this script
// float: A number with a decimal point
// variableName: The name of the variable (speed)
// '=': Assigns a value to the variable
// 5f: The value we are assigning to the variable (5) which is a float (f)
private float speed = 5f;
```

### Detect if key is pressed

```csharp
// Outputs true if the A key is pressed
// Outputs false if the A key is not pressed
Input.GetKey(KeyCode.A)
```

### Increment Player Position

```csharp
// Inside Player Script
// Inside of void Update()

// transform.position: The location of the player
// Vector3.left: A 3D vector (-1, 0, 0)
// speed: The speed of the player
// Time.deltaTime: The time between each frame
transform.position += Vector3.left * speed * Time.deltaTime;
```

### Grab Player Location

```csharp
// Inside Player Script
// Inside of void Update()

// transform.position: The location of the player
transform.position

// Grab the x position of the player
transform.position.x

// Grab the y position of the player
transform.position.y
```

### Change Player Location

```csharp
// Inside Player Script
// Inside of void Update()

// transform.position: The location of the player
// Vector3: A 3D vector (x, y, z)
// 8.5f is the new x position
// transform.position.y is the current y position
// transform.position.z is the current z position
transform.position = new Vector3(8.5f, transform.position.y, transform.position.z);
```

### Grab Player Velocity

```csharp
// Inside Player Script
// Inside of void Update()

// rb: The Rigidbody2D component
// rb.velocity: The velocity of the player
rb.velocity

// Grab the x velocity of the player
rb.velocity.x

// Grab the y velocity of the player
rb.velocity.y
```

### Grab Camera Location

```csharp
// Inside Player Script
// Inside of void Update()

// Camera.main: The main camera
// Camera.main.transform: The location of the main camera
Camera.main.transform

// Grab the position of the camera
Camera.main.transform.position

// Grab the x position of the camera
Camera.main.transform.position.x

// Grab the y position of the camera
Camera.main.transform.position.y
```

### Destroy GameObject

```csharp
// Inside Player Script
// Can be used inside of any function

// Destroy the GameObject
Destroy(gameObject);
```

---

## Platform Code

### Find GameObject

```csharp
// Inside Platform Script
// Inside of void Update()

// Find the GameObject with the tag Player
// GameObject.FindWithTag("Player"): The GameObject with the tag Player
GameObject.FindWithTag("Player")
```

### Disable Box Collider (or any component)

```csharp
// Inside Platform Script
// Inside any function

// Disable the Box Collider 2D component
// GetComponent<BoxCollider2D>(): The Box Collider 2D component
// .enabled: The enabled property of the Box Collider 2D component
GetComponent<BoxCollider2D>().enabled = false;
```

---

## Player Jumping Code

### Detect collision with GameObject

```csharp
// Inside Player Script

// OnCollisionEnter2D: When the player collides with a GameObject
// collision: The collision data
void OnCollisionEnter2D(Collision2D collision)
{
    // collision.gameObject: The GameObject that the player collided with
    collision.gameObject
}
```

### Grab GameObject Tag

```csharp
// Inside Player Script
// Inside any function

// collision.gameObject: The GameObject that the player collided with
// .tag: The tag of the GameObject
collision.gameObject.tag
```