---
title: 0. Auto-Poetry
type: checkup
---

## Functional Programming with Grammar

In this challenge, we're going to think about language with a functional programming lens. Instead of
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



## Part 3: Auto-poetry


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



