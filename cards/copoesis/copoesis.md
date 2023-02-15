# Copoesis
Hashing algorithm vs memory explosion problem in the memoization of deeply recursive structures:

We want to transfer a picture which can contain: objects, and object-graphs (with cycles), and even pictures of pictures of pictures and so on...

Inside of each of these pictures we can have many identical but necessarily unique objects.

=== Realization
**Javascript Sets:**
Set objects are collections of values. **A value in the Set may only occur once; it is unique in the Set's collection.** You can iterate through the elements of a set in insertion order. The insertion order corresponds to the order in which each element was inserted into the set by the add() method successfully (that is, there wasn't an identical element already in the set when add() was called).

The specification requires sets to be implemented "that, on average, provide access times that are sublinear on the number of elements in the collection". Therefore, it could be represented internally as a hash table (with O(1) lookup), a search tree (with O(log(N)) lookup), or any other data structure, as long as the complexity is better than O(N).
===

To reduce the memory-use, we can replace (all or most-commonly repeated) pure-objects and pure-pictures with their hashes and store the real objects inside of a hash-table.

Sounds great! But there's a catch: hash-collisions. Two pictures might have the same hash!

To avoid this over the past 30 years cryptographers have been creating hashing algorithms where the chances of a collision are negligble.

But these hashing algorithms offer this functionality at the expense of memory. Indeed even taking the hash of the letter "a" with SHA256 yields
"ca978112ca1bbdcafac231b39a23dc4da786eff8147c4e72b9807785afee48bb"

This proposes a problem if we want to replace potentially everything in the picture including deeply nested pictures with hashes... 

A hash of a picture with hash of a picture and a hash of picture ...

We can quickly see how we will begin to lose information about the hashes of pictures within our picture

One hash can corrspond to:
- several possible pictures
- several possible recognition streams about these possible pictures
- several possible meanings of the hashes in these picture

// repition of above
If every value inside the picture is a unique (which is what the Set ensures)
Then a hash of a picture in one picture can differ in meaning from an identical hash in another picture

This also means that of all the possible pictures stored at a hash and all the possible meanings for the pictures elements stored there as well.
These possible recognition streams could potentially point at any of these pictures!
// end of repitition

How do we know which of these possible streams is talking about which one of these pictures, if it's only referencing a hash?
Well the recognition streams should stream their perceptions of the positions in the array of the picture they are referencing.
Bob could say "I believe that the object you beleive I am referring to is in position 2"

Finding Common-ground at this level means that we can reason to find what we really mean

Find those parts of the object that contain non-symbolic representations and hash/memozie those to store them at an index in the pictures array this way we can take the hash of pictures in order to give them a location without worrying that these picture hashes are "dirty"

But how are we to approach memoizing so as to reduce the amount to information-loss that would come from taking the hash of a picture with another hash within it? Taking the hash of a picture with hashes inside of it, will likely lead to confusion as we lose our understanding of what those hashes are.

So we should start with taking the hash of pictures that contain no hashes, let's call these **pure pictures**.

These pure pictures serve as the skeletal structure of the more unknown **impure pictures**, which itself serves as a backdrop that allows us to reason about and ground perceptions of possible/impossible/necessary/contingent pictures and the relations between them and their hashes.

But we arrive here at another problem, were we to **memoize** these **pure pictures** and replace them with their hash, these sets of values turned hashes might find themselves scattered throughout pictures, meaning that all those that contain them are now **impure pictures**.

Memoization procedures for finding the optimal compression between pure and impure pictures, is crucial, and indeed **common ground about the picture of pure pictures can greatly reduce confusion for all**. 

When we look at it like that, there isn't even a need for a hashing algorithm, any convention could be adopted by which recognizers choose to attribute meaning to representations, indeed these conventions could be expressed, and those languages could be installed for dealing with precisely that level of interpretation (see AD4M). However such conventions would likely stand to benefit from being used in conjunction with hashing in order to decrease lookup-time and the necessity of grounding.

**To Recap**
We basically want to store the picture inside the hashtable based on it's hash
Then we later add significations to the picture
and when we memoize, we replace the picture with it's hash://2f0ien02f
which gives us an index, and then we see all the pictures that could possibly be at this hash
we then, see along side the pictures that have this hash, all the recognitions that point
to this hash
and each one of the recognitions inside of this bucket comes from a recognier
who has beliefs about which position in the bucket it's recognition is talking about.

**So grounding perceptions of what is being pointed at, allows for:**
- translating between our perceptions of reference
- reorganizing our pointers in a common order
-   to reduce the need for translation 
-   this aids us in memoization of the structure
-   and in fact reduces the pressure to avoid hash collisions!
-   Allowing us to adopt much smaller hashes all the way the picture structure, which increases the burden on grounding but interestingly enough decreases
the information-loss that we face when our hashes are too long in what can be deeply nested and even cyclic structures.


# Membranes
The recogntion streams surrounding a picture can be stored in a membrane.

# Categories
The recognition of symbols can also be interepreted as categories allowing certain transformation between morphisms

In brief, set theory is about membership while category theory is about structure-preserving transformations – but only about the relationships between those transformations.

Set theory is only about membership (i.e. being an element) and what can be expressed in terms of that (e.g. being a subset). It does not concern itself with any other properties of elements or sets.

Category theory is a way to talk about how mathematical structures of a given type1 can be transformed into one another2 by functions that preserve some aspect of their structure; it provides a uniform language for speaking of a great range of types1 of mathematical structure (groups, automata, vector spaces, sets, topological spaces, … and even categories themselves!) and the mappings within those types1. Although it formalises the properties of mappings between structures (really: between the sets on which the structure is imposed), it only deals with abstract properties of maps and structures, calling them morphisms (or arrows) and objects; the elements of such structured sets are not the concern of category theory, and nor are the structures on those sets. You ask “what is it a theory of”; it is a theory of structure-preserving mappings of mathematical objects of an arbitrary type1.

The theory of Abstract categories3, however, as just stated, totally ignores the sets, operations, relations and axioms that specify the structure of the objects in question; it just provides a language in which to talk about how mappings that do preserve some such structure behave: without knowing what structure is preserved, we know that the combination of two such maps also preserves structure. For that reason, the axioms of category theory require that there be an associative composition law on morphisms and, similarly, that there be an identity morphism from each object to itself. But it does not assume that morphisms actually are functions between sets, just that they behave like them.

In Concrete categories, however, the objects really do correspond to sets and the morphisms to mappings of those sets, or they correspond to objects and morphisms of some other ‘base category’ than Set
. Concrete categories model the idea of adding structure to the objects of the base category, although we still ignore that actual structure: we consider only the morphisms of the base category and the abstract behaviour of the morphisms of the concrete category. For example Grp, the category of groups, may be made into a concrete category (over Set

), by specifying the homomorphisms as mappings of the underlying sets of the groups; however, this tells us nothing about the group multiplication operations themselves.

As for the implications of your formulations, saying that “G
is a group”, that “G is an element of the set of groups” (actually a proper class) or that “G is (an object) in Grp” (or a “Grp-object”) mean the same thing logically, but talking about the category suggests you are interested in group homomorphisms (the morphisms in Grp) and perhaps in what they have in common with other morphisms. On the other hand, saying G is a group might suggest you are interested in the structure of the group (its multiplication operation) itself or perhaps in how the group acts on some other mathematical object. You would be unlikely to talk about G belonging to the class (not really “set”) of groups, though you could easily write G∈S for some particular collection S of groups you are interested in.
