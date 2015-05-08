Katharina Kristensen

#Research Assignment/Presentation

4/22/15


For my game, I was developing a portal system that included four distant "rooms" and a central hub.  In each of these rooms was a doorframe with an active portal (transporting the player to an empty object near the corresponding door in the hub).  What I needed was for the portal in the hub to only activate once the player had transported to it from the portal in the corresponding "room."  I already had my "PortalSpawn" script as such:

	#pragma strict

	var makeGate = true;

	var gate : GameObject;

	function OnTriggerEnter (other : Collider) {

		if (makeGate == true){
		Instantiate (gate);
		makeGate = false;
	}
	}

However, the issue I was running into was that Unity was not allowing me to drag an object into the "gate" box of the script (to assign the "transform" variable), which meant that while the gate would spawn, it would not lead anywhere.

The Unity Forum offered two solutions.  One was to add the following to a script:

	public GameObject anObject;
 	void Awake () {
    	 anObject = GameObject.Find("in-game_object_name");    
	 }

(http://answers.unity3d.com/questions/264742/putting-gameobject-to-the-script-of-prefab.html)

However, as a beginner with scripting, I wasn't confident on being able to integrate this script on my own (though I saved it for later, in case someone else could help me or there didn't end up being another way).

Luckily, I also found an alternate solution: according to a forum user, "You can reference to gameobjects that are either children of the prefab or the prefab itself."  By making the gameobject transportation destinations children of their respective doors, and then assigning them both to a single prefab, I was able to instantiate the doors with their destinations attached.  

(http://answers.unity3d.com/questions/11190/are-there-restrictions-on-assigning-gameobjects-to.html)

I argue that this is best practice, partly simply for my skill level, and partly because it cleans up the scripts and avoids any issues that might arise from forcing Unity to run a search of all gameobjects.  It furthermore combines what could be a multiple-step process into a single, simple step (Instantiate).  Therefore, this is the approach I chose to take in my project.


