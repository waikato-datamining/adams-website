.. title: AbstractActor -> Actor
.. slug: abstractactor-actor
.. date: 2016-02-13 17:35:37 UTC+13:00
.. tags: refactoring
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

On Friday, I embarked on a major refactoring mission, something that I've put
off for years now.

A few years into the development of ADAMS, I introduced the *Actor* interface,
attempting to make it simpler with other derived frameworks, in order to
avoid casting etc underneath the hood. However, this required touching a lot
of classes, including a lot of production code. The reason why I shied away
from doing it.

But, things change and I'm in the process of developing some other commercial
frameworks from the ground up (but still based on ADAMS). Instead of using
AbstractActor in methods and member variables, I've switched to using the Actor
interface, getting rid of a lot of unnecessary (and potentially dangerous)
casts. There were about 6,500 occurrences of *AbstractActor* in the various
code bases (including unit tests), so It took a while going through all of
them and changing the ones where it made sense. At this stage (haven't
checked anything in yet), everything compiles and the unit tests pass.
I'll be making a lot more tests still, but I'm aiming for a massive commit on
Monday night with all those changes. So, the next time you update your code,
it might take a bit longer than usual... ;-)

I'll keep you posted!
