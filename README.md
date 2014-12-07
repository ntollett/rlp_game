TODO
=====

###Door
--------------

	Struct {
			leadsTo *Room
			int positionX
			int positionY
			int landingPositionX
			int landingPositionY
	}

###ROOMS
--------------
Member Variables:

	int width
	int length
	[][] space
	[]Door doors


	// Rooms will be an array of arrays and will handle space like this
	 [[][-][-][]]
	 [|][][][|]
	 [|][][][|]
	 [[][-][-][]]

	which will then print out something like this:

	[--]
	|  |
	|  |
	[--]

Methods:

	buildRooms() // Probably the constructor
	populateRoom() // This will take an actor and add it at the appropriate x/y location
	printRoom() //Draw the room in the terminal



###ACTOR
--------------
Member Variables:

	int positionX
	int positionY
	int health
	int mana
	int intelligence
	int strength
	int dexterity

Methods:

	move(string direction) // move the character in the room
	takeDamage(int damage) // take damage
	castSpell(string spell) // cast a spell
	attack()


 -> PLAYER // Subclass of Actor

Member Variables:

	[]Loot inventory

Methods:

	void GameOver()

 -> ENEMIES // Subclass of Actor

Member Variables:

 	[]Loot drops

Methods:

	void Dies()


###LOOT
--------------
Member Variables:

	int strMod
	int intelMod
	int dexMod
	int range
	bool isEquipped
	string name

Methods:

	constructors for different items


###ENGINE
--------------

Member Variables:

	[]Rooms



Syntax for creating dungeons and items
========================================

	loot.table <- text file which looks like this:

	[item 1 name]
	strMod=#
	intelMod=#
	dexMod=#
	range=#

	example item

	[Draxor the Destroyer Axe]
	strMod=1000000000000000000000
	intelMod=-1000000000000000000
	dexMod=0
	range=1


and a room file will look like

	[Room Name]
	linksTo=RoomName1, RoomName2, etc.
	length=#
	width=#
	door1=RoomName1, x, y
	door2=RoomName2, x, y

and then our engine will be able to parse these files and build a dungeon out of them.