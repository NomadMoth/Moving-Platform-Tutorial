# Moving Platform Tutorial

## 1. Variables

To start, create three variables, one public game object array for the waypoints, one private integer which will allow
the user to choose how many waypoints they wish to have in the inspector, and a public float to allow control
over the speed of movement for the platform.

You should have something like this:

	  public GameObject[] waypoints;
    private int currentWaypointIndex = 0;
    public float speed = 2f;

## 2. If Statements

In the update function, create an if statement. Within this statement will be the conditions that must be met
for the platform to travel between waypoints.

        // This checks whether the platform is close enough to the waypoint it is travelling toward
        if (Vector3.Distance(waypoints[currentWaypointIndex].transform.position,
            transform.position) < .1f)
        {
            // This adds one to the index, switching waypoint targets for the platform
            currentWaypointIndex++;
            
            // This resets the index to the beginning, resulting in the platform returning to the first waypoint
            if (currentWaypointIndex >= waypoints.Length)
            {
                currentWaypointIndex = 0;
            }
        }
        // This moves the platform to the currently designated waypoint
        transform.position = Vector3.MoveTowards(transform.position, waypoints[currentWaypointIndex].transform.position, Time.deltaTime * speed);
    }

## 3. In Unity

In Unity, create an empty game object and rename it to Moving Platform. Create three children; two more empty game objects (rename to Waypoint1 and Waypoint2) and a cube.

![Screenshot 2021-12-08 163407](https://user-images.githubusercontent.com/72862464/145250041-a7c81e3a-df09-4f84-86c0-13301961dfcb.jpg)

Attach the script to the cube, type 2 into the waypoint array and then drag and drop the two waypoints into the boxes in the inspector.

![Screenshot 2021-12-08 163347](https://user-images.githubusercontent.com/72862464/145250988-20828811-2ac2-40f4-b99b-d38eb3c4c697.jpg)

Move the second waypoint to specified location and test by running the game.
