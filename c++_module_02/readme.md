20 Expected files
10 .cpp (c++ files) and 10 .hpp (header files)

1️⃣ Warlock.cpp

2️⃣ Warlock.hpp

3️⃣ ASpell.cpp

4️⃣ ASpell.hpp

5️⃣ ATarget.cpp

6️⃣ ATarget.hpp

7️⃣ Fwoosh.cpp

8️⃣ Fwoosh.hpp

9️⃣ Dummy.cpp

1️⃣0️⃣ Dummy.hpp

1️⃣1️⃣ Fireball.cpp

1️⃣2️⃣ Fireball.hpp

1️⃣3️⃣ Polymorph.cpp

1️⃣4️⃣ Polymorph.hpp

1️⃣5️⃣ BrickWall.cpp

1️⃣6️⃣ BrickWall.hpp

1️⃣7️⃣ SpellBook.cpp

1️⃣8️⃣ SpellBook.hpp

1️⃣9️⃣ TargetGenerator.cpp

2️⃣0️⃣ TargetGenerator.hpp

Subject Text
In the Warlock, SpellBook and TargetGenerator classes, the switch statement is FORBIDDEN and its use would result in a -42.

Fwoosh, Fireball, Polymorph and BrickWall
Create the following two spells, on the same model as Fwoosh:

Fireball (Name: "Fireball", Effects: "burnt to a crisp")
Polymorph (Name: "Polymorph", Effects: "turned into a critter")
In addition to this, just so he won't have only dummy to attack, let's make a new target for him, which will be the BrickWall (Type: "Inconspicuous Red-brick Wall").

SpellBook and TargetGenerator
Now, make a SpellBook class, in canonical form, that can't be copied or instantiated by copy. It will have the following functions:

* void learnSpell(ASpell*), that COPIES a spell in the book
* void forgetSpell(string const &), that deletes a spell from the book, except
  if it isn't there
* ASpell* createSpell(string const &), that receives a string corresponding to
  the name of a spell, creates it, and returns it.
Modify the Warlock, now, make it have a spell book that will be created with him and destroyed with him. Also make his learnSpell and forgetSpell functions call those of the spell book.

The launchSpell function will have to use the SpellBook to create the spell it's attempting to launch.

Make a TargetGenerator class, in canonical form, and as before, non-copyable.

It will have the following functions:

* void learnTargetType(ATarget*), teaches a target to the generator

* void forgetTargetType(string const &), that makes the generator forget a
  target type if it's known

* ATarget* createTarget(string const &), that creates a target of the
  specified type
Main Function
Here's a test main:

int main()
{
  Warlock richard("Richard", "foo");
  richard.setTitle("Hello, I'm Richard the Warlock!");
  BrickWall model1;

  Polymorph* polymorph = new Polymorph();
  TargetGenerator tarGen;

  tarGen.learnTargetType(&model1);
  richard.learnSpell(polymorph);

  Fireball* fireball = new Fireball();

  richard.learnSpell(fireball);

  ATarget* wall = tarGen.createTarget("Inconspicuous Red-brick Wall");

  richard.introduce();
  richard.launchSpell("Polymorph", *wall);
  richard.launchSpell("Fireball", *wall);
}
Output

~$ ./a.out | cat -e
Richard: This looks like another boring day.$
Richard: I am Richard, Hello, I'm Richard the Warlock!!$
Inconspicuous Red-brick Wall has been turned into a critter!$
Inconspicuous Red-brick Wall has been burnt to a crisp!$
Richard: My job here is done!$
~$