10 Expected files
5 .cpp (c++ files) and 5 .hpp (header files)

1️⃣ Warlock.cpp

2️⃣ Warlock.hpp

3️⃣ ASpell.cpp

4️⃣ ASpell.hpp

5️⃣ ATarget.hpp

6️⃣ ATarget.cpp

7️⃣ Fwoosh.cpp

8️⃣ Fwoosh.hpp

9️⃣ Dummy.cpp

1️⃣0️⃣ Dummy.hpp

Subect Text
In the Warlock class, the switch statement is FORBIDDEN and its use would result in a -42.

Aspell
Create an abstract class called ASpell, in Coplien's form, that has the following protected attributes:

* name (string)
* effects (string)
Both will have getters (getName and getEffects) that return strings.

Also add a clone pure method that returns a pointer to ASpell.

All these functions can be called on a constant object.

ASpell has a constructor that takes its name and its effects, in that order.

ATarget
Now you will create an ATarget abstract class, in Coplien's form. It has a type attribute, which is a string, and its associated getter, getType, that return a reference to constant string.

In much the same way as ASpell, it has a clone() pure method.

All these functions can be called on a constant object.

It has a constructor that takes its type.

Now, add to your ATarget a getHitBySpell function that takes a reference to constant ASpell.

It will display :

<TYPE> has been <EFFECTS>!
is the ATarget's type, and is the return of the ASpell's getEffects function.

Finally, add to your ASpell class a launch function that takes a reference to constant ATarget.

This one will simply call the getHitBySpell of the passed object, passing the current instance as parameter.

Fwoosh
When all this is done, create an implementation of ASpell called Fwoosh. Its default constructor will set the name to "Fwoosh" and the effects to "fwooshed". You will, of course, implement the clone() method. In the case of Fwoosh, it will return a pointer to a new Fwoosh object.

Dummy
In the same way, create a concrete ATarget called Dummy, the type of which is "Target Practice Dummy". You must also implement its clone() method.

Add to the Warlock the following member functions:

learnSpell, takes a pointer to ASpell, that makes the Warlock learn a spell
forgetSpell, takes a string corresponding a to a spell's name, and makes the Warlock forget it. If it's not a known spell, does nothing.
launchSpell, takes a string (a spell name) and a reference to ATarget, that launches the spell on the selected target. If it's not a known spell, does nothing.
You will need a new attribute to store the spells your Warlock knows. Several types fit the bill, it's up to you to choose the best one.

Main Function
Below is a possible test main:

int main()
{
  Warlock richard("Richard", "the Titled");

  Dummy bob;
  Fwoosh* fwoosh = new Fwoosh();

  richard.learnSpell(fwoosh);

  richard.introduce();
  richard.launchSpell("Fwoosh", bob);

  richard.forgetSpell("Fwoosh");
  richard.launchSpell("Fwoosh", bob);
}
Output

~$ ./a.out | cat -e
Richard: This looks like another boring day.$
Richard: I am Richard, the Titled!$
Target Practice Dummy has been fwooshed!$
Richard: My job here is done!$