---
title: 0. Types
draft: True
---

# Types Lab
{{< devnote >}}
replace links to isf repo <br>
fix modulo link (functions lesson in unit 0)
{{< /devnote >}}

In this lab we'll explore the idea of functional programming and data types. In functional programming, we think of functions as transformations. They take any number of **parameters** and they change them into a **return value**.

Remember the structure of a Python function?

```python
def double(number):
  return 2 * number
```

> Here, `number` is the paramter and `2 * number` is the return value. 
>
> As its name suggests, this function returns twice, `number`.

Here is a visualization of the function `double`. We are not so focused on how the function gets its 
work done as we are on what goes in and what comes out:

![Functional view of the double function](fig1.png)

This unlocks a powerful new way of breaking down
problems: we can think about how functions could be connected together. How do
you quadruple a number? Just double it, and then double the result: 

![Functional view of the quadruple function](fig2.png)

>
> ```python
> double(double(5))
> ```
>
> Will output: `20`

You will soon see that much more **difficult problems can often be broken down into simpler functions by thinking about how each function transforms an input into an output**. 

## Part 1: Thinking about types

You have already met a bunch of different kinds of objects in Python: `1`,
`2.55`, `True`, `"pizza"`, `None`. Each of these has a **type**. When we
talk about what goes in to functions and what comes out, we won't talk about
particular inputs. 
> Who cares if you double `7` or `9`? The point is you can't double `False`.

We'll talk about the **types** of objects that functions operate on. **Everything has a type.** Here are a few types that you already know:

| Type     | Examples        | Description                                                                                                                          |
| -------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `int`    | 145, -200       | Integers, just like you know them from math class :)                                                                                 |
| `float`  | 1.1115, 9.08    | Decimal numbers. They're called `float` because of [how they are stored](https://en.wikipedia.org/wiki/Floating-point_arithmetic)    |
| `str`    | "apple", "x"    | Strings, or sequences of characters. Careful! `5` is an `int` but `"5"` is a `str`.                                                  |
| `bool`   | `True`, `False` | Booleans, or True/False values. Named for George Boole, who spent a lot of time thinking about them.                                 |
| `list`   | `[1, 2, 3]`     | A `list` holds other objects.                                                                                                        |

{{< expand "FYI, types can also be functions." >}}

Every type is also a function which turns its argument into that type, if it's possible. So,
* `int(3.33333)` becomes `3`
* `str(True)` becomes `"True"`, 
* `bool(0)` becomes `False`. 

But `list(False)` is an error, because there's no sensible way to turn `False` into a list. 

Python's attitude toward types is pretty casual; even if
something is not quite the right type, we'll make it work if we can. Other
languages are *much* stricter, requiring every variable to specify its type, and
requiring every function to specify what type it accepts and what type it
returns. There are tradeoffs, and you'll probably develop an opinion on which
you prefer once you learn a few more programming languages. 
{{< /expand >}}

<br>


{{< write-action >}} **Work with your group in your Google Slide to following table. For each function describe what type the function would take as an input, and what type the function would return as output.**

| Function                                                         | Input type(s) | Output type |
|------------------------------------------------------------------|---------------|-------------|
| Square root of a number                                          | float         | float       |
| Multiplication of two integers                                   |               |             |
| Average of a list of numbers                                     |               |             |
| A function that gives all the factors of a number                |               |             |
| A function to check if a word is a curse word                    |               |             |
| A function that assigns a friendliness score to a sentence       |               |             |
| A function that takes a website URL and returns the page content |               |             |
| A function that counts the number of sentences in a paragraph    |               |             |
| `>`                                                              |               |             |
| `not`                                                            |               |             |

Once you are confident in your answers (and confident everyone in your group can explain them) check with a teacher.

##  Part 2: Building sentences with grammar

You already know how to simplify arithmetic expressions like `(2 + 10) / (5 - 2)` by applying functions:

![Functional view of arithmetic](fig3.png)

In this lab, we're going to think about language in the same way. Instead of
functions like `add` and `subtract`, which combine numbers, we will use
functions like `noun_phrase`, which combines words into parts of speech. 

![Functional view of syntax](fig4.png)

Here's an example of how we can use these functions to build a sentence. 
These functions are very strict about what kinds of inputs they accept, because
we want to make sure we don't create ill-formed sentences like "The my mouse
hungry milk milk milk."

![Building sentences](fig5.png)

{{< expand "A little bit of English grammar" >}}
The diagram above shows that the function `noun_phrase` combines an adjective
("little") and a noun phrase ("mouse") into another noun phrase
("little mouse"). You could apply the same function again to build a bigger noun
phrase with another adjective ("hungry little mouse"). 
`determine_noun_phrase` combines a `Determiner` with a `NounPhrase` to produce a
`DeterminedNounPhrase`. Determiners are words like "a", "the", "my", and "that",
which *determine* what the noun refers to. (Consider the difference between "a
hungry little mouse" and "my hungry little mouse.") 

`verb_phrase_transitive`
combines a `TransitiveVerb` with a `NounPhrase` to produce a `VerbPhrase`. Verbs
are action words, and transitive verbs are actions that have a subject and an
object, something that acts and something that gets acted upon. For example, you
can't just "annoy," you have to annoy someone or something. Same with "cancel"
and "chase." So to make a full `VerbPhrase`, we need to comine a
`TransitiveVerb` with the `NounPhrase` it acts on.
Finally, `sentence` makes a `Sentence` from a `NounPhrase` and a `VerbPhrase`.
Your chewing sounds annoy my hungry little mouse. 
{{< /expand >}}

### Checking types in Python

In order to write these functions in Python, we will need to check the types of
each function's inputs. We will use the built-in functions `isinstance` and `type` 
to check types, and `assert` to intentionally crash the program when a function
receives the wrong type. 

 `isinstance(thing, a_type)` checks whether `thing` is `a_type`, returning `True`
or `False`. Types exist in a hierarchy: `PluralNoun` is a special kind of
`Noun`, and `Noun` is a special kind of `NounPhrase`. When you use 
`isinstance`, you are checking whether `thing` belongs to `a_type` or any of its
subtypes. If you want to check whether `thing`'s type exactly, use `type` to get
its type. For example: 

```python3
>>> food = PluralNoun("potatoes")
>>> isinstance(food, PluralNoun)
True
>>> isinstance(food, Noun)
True
>>> isinstance(food, VerbPhrase)
False
>>> type(food)
<class 'PluralNoun'>
>>> type(food) == PluralNoun
True
>>> type(food) == Noun
False
```

`assert condition` will do nothing if `condition` is `True`, but it will crash
the program if `condition` is `False`. Try it out--Python will keep going after
an error in interactive mode, but an uncaught error will crash a script. 

```python3
>>> assert 1 + 2 == 3
>>> assert 1 + 2 == 4
AssertionError
>>> assert isinstance(13, int)
>>> assert isinstance("cowboy", int)
AssertionError
```

With these tools, we can start writing grammar functions like the ones we saw
above. For example: 

```python3
def noun_phrase(adjective, np):
    assert isinstance(adjective, Adjective)
    assert isinstance(np, NounPhrase)
    return NounPhrase(adjective + ' ' + np)
```

This is what you will do next. 

## Part 3: Auto-poetry

{{< devnote >}}
Do we want to bother with collaborative git on this lab? Students are only
editing functions in one file; they could probably collaborate effectively
without it. Depends when we want to cross that bridge.
{{< /devnote >}}

### *Working with Git*

For this lab, use the following link to create a repo for your lab work. This will be an individual assignment, but you will work in a team with your table group.

{{< code-action >}} **First, create a `unit_01` directory in your `cs9` folder and clone the lab repository in it.** 
To create a new directory use the command: `mkdir folder_name`. 

{{< code-action >}} Starter code for the lab is provided in the
`lab-types` repo. Download it *onto your laptop*.

```shell
$ cd cs9/unit_01
$ git clone https://github.com/the-isf-academy/lab-types-YOUR-GITHUB-USERNAME.git
```

{{< expand "Reminder: Basic Git Workflow" >}}
The basic workflow is still the same:

+ `git status` to determine what has change
+ `git add` to add the files you've edited
+ `git commit` to write a message about what you've changed
+ `git push` to push your changes to Github

{{< /expand >}}

<hr>

### 3a: Love poems

The repository you cloned contains four Python files:

- `grammar.py` has a bunch of functions for combining and transforming
  grammatical types. **These are unfinished; it's your job to write them.**
- `poetry.py` has functions for writing beautiful auto-poems. Once `grammar.py`
  is complete, you will be able to generate poems.
- `vocabulary.py` has a bunch of functions for picking random words. This is explored in the extension activity. 
- `grammatical_types.py` defines types like `Noun`, `Adjective`, and `TransitiveVerb`.
  You won't edit this file, but it is useful as a reference for parts of speech.


{{< code-action >}} **Open `grammar.py` in Atom.** This module is full of functions
which transform parts of speech. Let's look at the first function:

```python3 {linenos=table}
def pluralize(noun):
    "Noun -> PluralNoun"
    assert type(noun) == Noun
    if noun.endswith("s") or noun.endswith("ch") or noun.endswith("sh"):
        return PluralNoun(noun + 'es')
    else:
        return PluralNoun(noun + 's')
```

- The *docstring* (line 2) describes this function's *type signature*, or what goes in and
  what comes out. `pluralize` receives a `Noun` and returns a `PluralNoun`.
- Line 3 checks the input type. If it's not a `Noun`, the program crashes.
- Line 4 contains a conditional checking the final letters of the noun. Most English nouns 
  are pluralized by adding
  "s" ("tree" becomes "trees"). But nouns ending in "s", "ch", or "sh" are pluralized 
  by adding "es" ("beach" becomes "beaches").
- Lines 5 and 7 create a new `PluralNoun` using the appropriate ending. All the grammatical types are
  subclasses of `str`, so they can be combined like normal strings using the `+`
  operator. 

{{< code-action >}} **Now open `poetry.py` in Atom.** Let's look at `love_poem`:

```python3 {linenos=table}
def love_poem():
    "() -> Poem"
    poem = Poem()
    poem.append("roses are red")
    poem.append("violets are blue")
    poem.append(pluralize(random_word(Noun)) + " are " + random_word(Adjective))
    poem.append("and so are you.")
    return poem
```
- The docstring (line 2) says this function takes no inputs and returns a
  `Poem`.
- `pluralize` is already finished, and it's the only function other than
  `random_word` we'll need. So this function will work!
- See if you can predict what this function will do. 

{{< code-action >}} **Let's try it out! Run `python -i poetry.py` to load the
`poetry` module.** Now let's have some love poems!

```python3
>>> print(love_poem())
Roses are red
Violets are blue
Evenings are poisonous
And so are you.
```
<hr>

### 3b: Couplet

Before we can run `couplet`, the next kind of poem, we'll need to implement a
few more grammar rules in `grammar.py`. Your group will need to complete the following functions:
- `noun_phrase`
- `determine_noun_phrase`
- `make_definite`
- `make_indefinite`

{{< write-action >}} **Before coding, create a function diagram with an example use case for each grammar rule in your group's Google Slide.**


{{< code-action >}} **noun_phrase**

```python3
>>> noun_phrase(Adjective("spooky"), Noun("closet"))
"spooky closet"
```

- Check that the first argument is an `Adjective`.
- Check that the second argument is a `NounPhrase`.
- Return a `NounPhrase` containing the adjective added to the noun (don't forget a
  space between them).

{{< code-action >}} **determine_noun_phrase**

```python3
>>> determine_noun_phrase(Determiner("that"), Noun("eagle"))
"that eagle"
```

- Check that the first argument is a `Determiner`.
- Check that the second argument is a `NounPhrase`.
- Return a `DeterminedNounPhrase` containing the determiner added to the noun phrase 
  (again, don't forget a space between them).

{{< code-action >}} **make_definite**

```python3
>>> make_definite(NounPhrase("evil squirrel"))
"the evil squirrel"
```

- Check that the first argument is a `NounPhrase`.
- Use `determine_noun_phrase` to combine the noun phrase with 
  `Determiner("the")`.
- Return the `DeterminedNounPhrase` you created.

{{< code-action >}} **make_indefinite**

```python3
>>> make_indefinite(NounPhrase("evil squirrel"))
"an evil squirrel"
>>> make_indefinite(NounPhrase("squirrel"))
"a squirrel"
```
- Check that the first argument is a `NounPhrase`.
- Check whether the noun phrase starts with a vowel sound 
  (using `starts_with_vowel_sound`, described above). 
  - If so, use `Determiner("an")`
  - If not, use `Determiner("a")`
- Use `determine_noun_phrase` to combine the noun phrase with 
  the determiner.
- Return the `DeterminedNounPhrase` you created.

{{< code-action >}} **Once these functions are finished, run `python -i poetry.py`
again and try out the `couplet` function.**

```python3
>>> print(couplet())
```
<hr>

### 3c: Limerick

There's one more kind of poem, a limerick. We'll need to implement a few more
grammar rules. Your group will need to complete the following functions:
- `verb_phrase`
- `pase_tense_transitive`
- `past_tense_intrasitive`
- `verb_phrase_intrasitive`

{{< write-action >}}  **Before coding, create a function diagram with an example use case for each grammar rule in your group's Google Slide.**

{{< code-action >}} **verb_phrase**

```python3
>>> verb_phrase(Adverb("easily"), VerbPhrase("crushed her enemies"))
"easily crushed her enemies"
```

- Check that the first argument is an `Adverb`.
- Check that the second argument is a `VerbPhrase`.
- Combine them into a `VerbPhrase`.
- Return the `VerbPhrase` you created.

{{< code-action >}} **past_tense_transitive**

```python3
>>> past_tense_transitive(VerbTransitive("avoid")
"avoided"
```

- Check that the first argument is a `TransitiveVerb`. Make sure it's not a 
  `PastTenseTransitiveVerb` or you might accidentally conjugate a verb twice, 
  resulting in something like "avoideded".
- Choose an appropriate ending to conjugate the verb in the past tense. 
  If the verb ends in 'e', add 'd'. Otherwise, add 'ed'.
- This won't work for irregular verbs (e.g. the past tense of 'go' is 'went'), 
  but let's just ignore that for now. You can come back later and add logic for 
  some irregular verbs if you're feeling ambitious.
- Return a `PastTenseTransitiveVerb` consisting of the verb plus its new ending.


{{< code-action >}} **past_tense_intransitive**

```python3
>>> past_tense_intransitive(VerbTransitive("molt")
"molted"
```

- Check that the first argument is an `IntransitiveVerb`. Again, make sure it's not a 
  `PastTenseIntransitiveVerb`.
- Choose an appropriate ending to conjugate the verb in the past tense. 
  If the verb ends in 'e', add 'd'. Otherwise, add 'ed'. Again, don't worry
  about irregular verbs. The English language has only itself to blame for this
  mess.
- Return a `PastTenseIntransitiveVerb` consisting of the verb plus its new ending.

{{< code-action >}} **verb_phrase_transitive**

Intransitive verbs like "quit" are already verb phrases because they can
form complete sentences (I quit). But transitive verbs like "take" need a noun phrase.
You can't just take, you have to take something. 

```python3
>>> verb = past_tense_transitive(TransitiveVerb("transform"))
>>> np = make_definite(noun_phrase(Adjective("evil"), Noun("squirrel")))
>>> verb_phrase_transitive(verb, np)
"transformed the evil squirrel"
```
- Check that the first argument is a `TransitiveVerb`.
- Check that the second argument is a `NounPhrase`.
- Return a VerbPhrase consisting of the verb and the noun phrase.

{{< code-action >}} **Once these functions are finished, run `python -i poetry.py`
again and try out the `limerick` function.** Note that `limerick` has three
arguments, a name and two pronouns.

```python3
>>> print(limerick("Alex", "he", "his"))
```

<hr>

## Deliverables

You now have a powerful set of tools to write auto-poetry. See what else you can
come up with. We'll share the best poems your computers are able to come up
with!

For this lab, you should submit the following:
- The Git Repo
- Your Google Slide

*By the way, if you found this lab interesting, you might be interested in
exploring computational linguistics, or using CS to explore how language works.
This lab just scratched the tiniest layer of the surface of this wonderful
field. Here, we generated sentences. What about the reverse, trying to
understand language produced by humans?*  


<hr>

## Extention: A New Kind of Generator

Let's take a look at `poetry.py`. Each poem is its own function utilizing the functions from `grammar.py`. The extension activity to create a new phrase generator of your creation. It can be anything from a haiku generator, to a compliement generater, to an insult generator. It's up to you!

{{< code-action >}} **Create a new type of phrase generator by implementing the grammar rules in `grammar.py` and the random word functionality in `vocabulary.py`. Be sure to reference `poetry.py` for syntax and formatting tips.**


### Random Words

Takea look at the functions provided in `vocabulary.py`. Run `python -i vocabulary.py`. This loads everything in `vocabulary` and then enters interactive mode. Try the following. (You'll get different results, of course, because they are random.)

```python3
>>> random_word(Noun)
'bayonet'
>>> random_word(Noun, rhymes_with="soup")
'loop'
>>> random_word(Noun, syllables=6)
'microorganism'
>>> random_word(Noun, count=3, meter=Meter("1020"))
['territory', 'storyteller', 'motorcycle']
>>> random_word(Noun, rhymes_with="orange")
NoWordError: Couldn't find a Noun with conditions: rhymes with orange
>>>
```

Whoa! `random_word` is super powerful. Here is `random_word`'s type signature:

**random_word**

Returns one or more random words, matching the specified conditions.

#### Arguments
- **word_type** (*type*): Must be one of `Noun`, `TransitiveVerb`, `IntransitiveVerb`,
  `Adjective`, or `Adverb`.
- **count** (*int*): Optional. How many words you want. Normally, the result of
  `random_word` is a word of the requested type, but when `count` is provided,
  the result is a list of such words.
- **rhymes_with** (*string*): Optional. A word the result should rhyme with.
- **meter** (*Meter*): Optional. The pattern of stresses that should be in the result's 
  pronounciation. A *Meter* is a string of digits, where `1` represents a word's
  main stress, `2` represents secondary stress, and `0` represents unstressed
  syllables. The meter used above, `1020`, matches words whose sound is like
  "BUM-bah-Bum-bah." Try saying 'territory', 'storyteller', and 'motorcycle'
  out loud. TERR-i-Tor-y, STOR-y-Tell-er, MO-tor-Cy-cle.
- **syllables** (*int*): Optional. The number of syllables that should be in the result. 

#### Returns
- A word of `word_type`. If `count` is provided, returns a list of such words.

---

There are some other useful functions in `vocabulary.py`:

{{< expand "rhyming_pair" >}}


Returns two rhyming words of the specified types.

```python3
>>> rhyming_pair(TransitiveVerb, IntransitiveVerb, meter="10")
('fumble', 'grumble')
>>> adj, noun = rhyming_pair(Noun, Adjective, syllables=2)
>>> adj
'graphic'
>>> noun
'traffic'
```

#### Arguments

- **first_word_type** (*type*): Must be one of `Noun`, `TransitiveVerb`, `IntransitiveVerb`,
  `Adjective`, or `Adverb`.
- **second_word_type** (*type*): Must be one of `Noun`, `TransitiveVerb`, `IntransitiveVerb`,
  `Adjective`, or `Adverb`.
- **meter** (*Meter*): Optional. The pattern of stresses that should be in the result's 
  pronounciation. 
- **syllables** (*int*): Optional. The number of syllables that should be in the result. 

#### Returns

- Two words of *(first_word_type, second_word_type)*. See the example usage for
  how to capture each return value in a separate variable. 

{{< /expand >}}

{{< expand "count_syllables" >}}

```python3 
>>> count_syllables("bogus")
2
```

#### Arguments
- word (*str*)

#### Returns
- An *int*, the number of syllables

**get_meter**

```python3
>>> get_meter("animal")
'100'
>>> get_meter("helicopter")
'1020'
>>> get_meter("inexcusable")
'20100'
```
#### Arguments
- word (*str*)

#### Returns
- *Meter*, a string of digits representing stresses in the word's pronunciation.
  `1` represents a word's
  main stress, `2` represents secondary stress, and `0` represents unstressed
  syllables. The examples above show that the words are pronounced 'A-ni-mal'
  ('100'), 'HE-li-Cop-ter' ('1020'), and 'In-ex-CUS-a-ble' ('20100').

{{< /expand >}}


{{< expand "starts_with_vowel_sound" >}}

```python3
>>> starts_with_vowel_sound("horrible hounds")
False
>>> starts_with_vowel_sound("awesome owls")
True
```

#### Arguments
- text (*str*)

#### Returns
- *bool*, `True` when the first word of `text` starts with a vowel sound.
  `False` otherwise.
{{< /expand >}}



