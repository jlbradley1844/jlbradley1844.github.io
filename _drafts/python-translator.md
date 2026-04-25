---
title: A Python Translator for Modern C++
---
## A Python Translator for Modern C++

The following is for anyone investigating "modern c++". Rather than confuse you with
talk of move semantics and r-values, I'd like to make something useful by showing
how many of the useful things that can easily, fluently be done in python can also
be done under "modern" C++ (C++20).

r"string" or R"string"
u"string" or U"string"
b"string" or B"string"
f"string"

etc.
0bNNNN or 0BNNNNN
0xNNNN or 0XNNNN
0o or 0O OCTAL - DO NOT USE!
etc.

MMM + NNNj - imaginary

iterators:
[iterator].__next()

yield

StopIteration (exception)

coroutines:
async def

await

async width
async for

slicing
sequence[a:b:c]

comprehension:
[(expr) for (target_list) in (or_test) (iterator)]
(note: yield forbidden within)

generators:
((expr) for (target_list) in (or_test) (iterator))

membership:
in / not in

anonymous function:
lambda (param_list): (expression)
generic functions:
def func[T](arg: T)

iterator unpacking:
*

assert

type aliases:
type

context management:
with (item_list)

deorators:
@f1(arg)
@f2
def func():
   ...
is same as
func <- f1(arg)(f2(func))

frozenset:
a read-only set which can be used as a key
to a dict, etc.; as in, unordered tuple


containers:
tuple
list
dict
set
frozenset
collections.dequeue
collections.defaultDict
collections.OrderedDict
collections.Counter                         std::multiset
collections.ChainMap                        no equivalent?? ("view" for multiple maps)

async containers:
collections.abc.(container)

itertools: infinite iterators
itertools.count()
itertools.cycle()
itertools.repeat()

itertools: terminating iterators
range() - create immutable sequence of numbers
iter(object, [sentinal])
itertools.accumulate()
itertools.batched()
itertools.chain()
itertools.chain.from_iterable()
itertools.compress()
itertools.dropwhile()
filter(function, iterable)
itertools.filterfalse() - compliment of filter
itertools.groupby()
itertools.islice() - like slice() but returns iterator
itertools.pairwise()
itertools.starmap()
itertools.takewhile()
itertools.tee()
zip() - create pairs from two iterables
itertools.zip_longest()

itertools:combinatoric generators
itertools.product()
itertools.permutations()
itertools.combinations()
itertools.combinations_with_replacement()

higher order function assistance:
map(function, iterable, *iterables)
functools.cache(user_funtion) - memoize
functools.cached_property(user_function)
functools.cmp_to_key()
@functools.lru_cache - decorator for memoization
functools.partial(func, /, *args, **keywords) - currying
functools.partialmethod(func, /, *args, **keywords) - method currying
functools.reduce()
@functools.singledispath() - dispatch on first argument only
@fun.register - add overloaded implementation to function
functools.update_wrapper() - for wrapping decorator functions
@functools.wraps - generally how update_wrapper() is used

### Incompatible features

Metaclasses:

Slice object:
returned by slice(). They are read-only and are not full generator objects,
but they are hashable and can be used as keys if desired.

Futures:
python futures are for enabling code intended for future versions;
they are treated differently by the compiler.Uh oh, this link is not active
This link is only active on the day of your appointment. 

Variable scope:
global - for raising to class at implrt level
nonlocal - force rebind of variable to an outside scope

Match statement (python 3.10+):
match (expr) case (pattern)
there is not yet an equivalent under c++
The expr may bind to variables, which are then used in the logic.
It is powerful and nontrivial.
TODO: study python pattern-match
TODO: study type annotation/hinting. Type hinting can be used on decorators parameters as well.
Python 3.12 has most developed type hinting.
NOTE: generic functions and classes are mechanisms for adding type hinting
in a "template-style" manner.
Types GenericAlias and Union are new core types used by type annotation.
TODO: class decorators are new
abc: import library to create abstract base classes

ChainMap (added 3.4) is a shortcut for chaining multiple maps together. Example
pylookup = ChainMap(locals(), globals(), vars(builtins))   # python variable binding
Updates to ChainMap generally go to the first contained map only.
