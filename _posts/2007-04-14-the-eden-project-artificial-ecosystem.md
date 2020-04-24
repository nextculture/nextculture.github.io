---
layout: single
title: The Eden project - Artificial ecosystem
date: 2007-04-14 09:00
categories: Development
---
The <a href="http://www.csse.monash.edu.au/%7Ejonmc/projects/eden/eden.html">Eden</a> project was inspired by <a href="http://www.csse.monash.edu.au/%7Ejonmc/">Jon McCormack</a>'s time in the <a href="http://www.nt.gov.au/nreta/parks/find/litchfield.html">Litchfield National Park</a>, in Australia. The artwork is a self-generating, artificial ecosystem complete with rocks, biomass and sonic animals populated. The creatures evolve, move about the environment, emit and listen to sounds, forage for food, encounter predators and mate with each other.

<img src="/public/uploads/2007/04/3cormack.jpg" alt="3cormack.jpg" />

After reading about projects like <a href="http://www.csse.monash.edu.au/%7Ejonmc/projects/eden/">Eden </a>and other artificial ecosystem I started thinking about other artificial ecosystem and maybe creating my own.

Each creature has a few attributes,
<ul>
	<li>ID - A unique identifier for every creature</li>
	<li>Sex - Male or female of the species males can only mate with other females, ect.</li>
	<li>Age - Depending on there genetic material each creature will have a different max age, once this age is reached the creature dies. if the creature does not mate before that then they do not pass on there genetic history.</li>
	<li>Energy level - If the creature does not regularly eat it will die off, it can eat the fool found around the land or the dead bodies of the other creatures,</li>
	<li>X - Where it is located on the map in the X plane</li>
	<li>Y - Where the creature is located on the map in the Y plane</li>
	<li>Genetic material - A linked list history of every creature before it, all its parents and there attributes, this information is used to set up the creatures initial properties. if the creatures parents lived a long life then this creature has a better chance of living a longer life.</li>
</ul>
The land or world has a few things in it
<ul>
	<li>Walls or boarders that are no passable</li>
	<li>Natural Food that can be eaten and grows by its self once a every year.</li>
	<li>Poison food that will kill the creature if eaten. the creatures have a chance to detect that it is poison this chance will increase and decrease independently on there genetic material.</li>
	<li>Dead and Alive creatures</li>
</ul>
Base behaviored of the creatures
<ul>
	<li>Creature of the opposite sex who meet each other creatures will have the choice of having mating. The choice is random and depends on the Genetic material of the creatures.  Mating does not guarantee procreation its a random chance based off of the Genetic material. Mating consumes energy.  The creatures can mate as many times as you like with as many different partners as it finds.</li>
	<li>If no food can be found and the creature has less then 20% energy left it will attack other creatures, depending on its Genetic material and energy levels the creature will either die or kill the other creature. The creatures may eat other dead bodies.</li>
	<li>if a body of a creatures is dead, it may be eaten by other creatures. if a year has passed and the creatures body has not been eaten it disappears.</li>
	<li>Dead bodies of creatures that died because of poison are poisonousness</li>
	<li>Moving requires energy</li>
</ul>
It would make a pretty interesting project.
