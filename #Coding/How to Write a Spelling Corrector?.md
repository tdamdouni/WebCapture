# How to Write a Spelling Corrector?

_Captured: 2016-03-14 at 00:44 from [norvig.com](http://norvig.com/spell-correct.html)_

In the past week, two friends (Dean and Bill) independently told me they were amazed at how Google does spelling correction so well and quickly. Type in a search like [[speling]](http://www.google.com/search?q=speling) and Google comes back in 0.1 seconds or so with Did you mean: **_[spelling](http://www.google.com/search?q=spelling)_**. (Yahoo and Microsoft are similar.) What surprised me is that I thought Dean and Bill, being highly accomplished engineers and mathematicians, would have good intuitions about statistical language processing problems such as spelling correction. But they didn't, and come to think of it, there's no reason they should: it was my expectations that were faulty, not their knowledge.

I figured they and many others could benefit from an explanation. The full details of an industrial-strength spell corrector are quite complex (you can read a little about it [here](http://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/en/us/pubs/archive/36180.pdf) or [here](http://citeseerx.ist.psu.edu/viewdoc/download;jsessionid=52A3B869596656C9DA285DCE83A0339F?doi=10.1.1.146.4390&rep=rep1&type=pdf)). What I wanted to do here is to develop, in less than a page of code, a toy spelling corrector that achieves 80 or 90% accuracy at a processing speed of at least 10 words per second.

So here, in 21 lines of [Python 2.5](http://python.org) code, is the complete spelling corrector:
    
    
    import re, collections  
      
    def words(text):return re.findall('[a-z]+', text.lower())   
      
    def train(features):  
        model = collections.defaultdict(lambda:1)  
        for f in features:  
            model[f]+=1  
        return model  
      
    NWORDS = train(words(file('big.txt').read()))  
      
    alphabet ='abcdefghijklmnopqrstuvwxyz'def edits1(word):  
       splits     =[(word[:i], word[i:])for i in range(len(word)+1)]  
       deletes    =[a + b[1:]for a, b in splits if b]  
       transposes =[a + b[1]+ b[0]+ b[2:]for a, b in splits if len(b)>1]  
       replaces   =[a + c + b[1:]for a, b in splits for c in alphabet if b]  
       inserts    =[a + c + b     for a, b in splits for c in alphabet]  
       return set(deletes + transposes + replaces + inserts)def known_edits2(word):  
        return set(e2 for e1 in edits1(word)for e2 in edits1(e1)if e2 in NWORDS)def known(words):return set(w for w in words if w in NWORDS)def correct(word):  
        candidates = known([word])or known(edits1(word))or known_edits2(word)or[word]  
        return max(candidates, key=NWORDS.get)

The code defines the function correct, which takes a word as input and returns a likely correction of that word. For example:
    
    
    >>> correct('speling')'spelling'>>> correct('korrecter')'corrector'

The version of shown here is a variation on one proposed by [Darius Bacon](http://wry.me/~darius/); I think this is clearer than the version I originally had. Darius also fixed a bug in the function .

## How It Works: Some Probability Theory

How does it work? First, a little theory. Given a word, we are trying to choose the most likely spelling correction for that word (the "correction" may be the original word itself). There is no way to know for sure (for example, should "lates" be corrected to "late" or "latest"?), which suggests we use probabilities. We will say that we are trying to find the correction _c_, out of all possible corrections, that maximizes the probability of _c_ given the original word _w_:

> argmax_c_ P(_c_|_w_) 

By [Bayes' Theorem](http://en.wikipedia.org/wiki/Bayes'_theorem) this is equivalent to:

> argmax_c_ P(_w_|_c_) P(_c_) / P(_w_) 

Since P(_w_) is the same for every possible _c_, we can ignore it, giving:

> argmax_c_ P(_w_|_c_) P(_c_) 

There are three parts of this expression. From right to left, we have:

  1. P(_c_), the probability that a proposed correction _c_ stands on its own. This is called the **language model**: think of it as answering the question "how likely is _c_ to appear in an English text?" So P("the") would have a relatively high probability, while P("zxzxzxzyyy") would be near zero. 
  2. P(_w_|_c_), the probability that _w_ would be typed in a text when the author meant _c_. This is the **error model**: think of it as answering "how likely is it that the author would type _w_ by mistake when _c_ was intended?"
  3. argmax_c_, the control mechanism, which says to enumerate all feasible values of _c_, and then choose the one that gives the best combined probability score. 

One obvious question is: why take a simple expression like P(_c_|_w_) and replace it with a more complex expression involving two models rather than one? The answer is that P(_c_|_w_) is _already_ conflating two factors, and it is easier to separate the two out and deal with them explicitly. Consider the misspelled word _w_="thew" and the two candidate corrections _c_="the" and _c_="thaw". Which has a higher P(_c_|_w_)? Well, "thaw" seems good because the only change is "a" to "e", which is a small change. On the other hand, "the" seems good because "the" is a very common word, and perhaps the typist's finger slipped off the "e" onto the "w". The point is that to estimate P(_c_|_w_) we have to consider both the probability of _c_ and the probability of the change from _c_ to _w_ anyway, so it is cleaner to formally separate the two factors.

Now we are ready to show how the program works. First P(_c_). We will read a big text file, [big.txt](http://norvig.com/big.txt), which consists of about a million words. The file is a concatenation of several public domain books from [Project Gutenberg](http://www.gutenberg.org/wiki/Main_Page) and lists of most frequent words from [Wiktionary](http://en.wiktionary.org/wiki/Wiktionary:Frequency_lists) and the [British National Corpus](http://www.kilgarriff.co.uk/bnc-readme.html). (On the plane home when I was writing the first version of the code all I had was a collection of Sherlock Holmes stories that happened to be on my laptop; I added the other sources later and stopped adding texts when they stopped helping, as we shall see in the Evaluation section.)

We then extract the individual words from the file (using the function words, which converts everything to lowercase, so that "the" and "The" will be the same and then defines a word as a sequence of alphabetic characters, so "don't" will be seen as the two words "don" and "t"). Next we train a probability model, which is a fancy way of saying we count how many times each word occurs, using the function train. It looks like this:
    
    
    def words(text):return re.findall('[a-z]+', text.lower())   
      
    def train(features):  
        model = collections.defaultdict(lambda:1)  
        for f in features:  
            model[f]+=1  
        return model  
      
    NWORDS = train(words(file('big.txt').read()))

At this point, NWORDS[w] holds a count of how many times the word w has been seen. There is one complication: novel words. What happens with a perfectly good word of English that wasn't seen in our training data? It would be bad form to say the probability of a word is zero just because we haven't seen it yet. There are several standard approaches to this problem; we take the easiest one, which is to treat novel words as if we had seen them once. This general process is called **smoothing**, because we are smoothing over the parts of the probability distribution that would have been zero, bumping them up to the smallest possible count. This is achieved through the class collections.defaultdict, which is like a regular Python dict (what other languages call hash tables) except that we can specify the default value of any key; here we use 1.

Now let's look at the problem of enumerating the possible corrections _c_ of a given word _w_. It is common to talk of the **edit distance** between two words: the number of edits it would take to turn one into the other. An edit can be a deletion (remove one letter), a transposition (swap adjacent letters), an alteration (change one letter to another) or an insertion (add a letter). Here's a function that returns a set of all words _c_ that are one edit away from _w_:
    
    
    def edits1(word):  
       splits     =[(word[:i], word[i:])for i in range(len(word)+1)]  
       deletes    =[a + b[1:]for a, b in splits if b]  
       transposes =[a + b[1]+ b[0]+ b[2:]for a, b in splits if len(b)>1]  
       replaces   =[a + c + b[1:]for a, b in splits for c in alphabet if b]  
       inserts    =[a + c + b     for a, b in splits for c in alphabet]  
       return set(deletes + transposes + replaces + inserts)

This can be a big set. For a word of length _n_, there will be _n_ deletions, _n_-1 transpositions, 26_n_ alterations, and 26(_n_+1) insertions, for a total of 54_n_+25 (of which a few are typically duplicates). For example, len(edits1('something')) -- that is, the number of elements in the result of edits1('something') -- is 494.

The literature on spelling correction claims that 80 to 95% of spelling errors are an edit distance of 1 from the target. As we shall see shortly, I put together a development corpus of 270 spelling errors, and found that only 76% of them have edit distance 1. Perhaps the examples I found are harder than typical errors. Anyway, I thought this was not good enough, so we'll need to consider edit distance 2. That's easy: just apply edits1 to all the results of edits1:
    
    
    def edits2(word):  
        return set(e2 for e1 in edits1(word)for e2 in edits1(e1))

This is easy to write, but we're starting to get into some serious computation: len(edits2('something')) is 114,324. However, we do get good coverage: of the 270 test cases, only 3 have an edit distance greater than 2. That is, edits2 will cover 98.9% of the cases; that's good enough for me. Since we aren't going beyond edit distance 2, we can do a small optimization: only keep the candidates that are actually known words. We still have to consider all the possibilities, but we don't have to build up a big set of them. The function known_edits2 does this:
    
    
    def known_edits2(word):  
        return set(e2 for e1 in edits1(word)for e2 in edits1(e1)if e2 in NWORDS)

Now, for example, known_edits2('something') is a set of just 4 words: {'smoothing', 'seething', 'something', 'soothing'}, rather than the set of 114,324 words generated by edits2. That speeds things up by about 10%.

Now the only part left is the error model, P(_w_|_c_). Here's where I ran into difficulty. Sitting on the plane, with no internet connection, I was stymied: I had no training data to build a model of spelling errors. I had some intuitions: mistaking one vowel for another is more probable than mistaking two consonants; making an error on the first letter of a word is less probable, etc. But I had no numbers to back that up. So I took a shortcut: I defined a trivial model that says all known words of edit distance 1 are infinitely more probable than known words of edit distance 2, and infinitely less probable than a known word of edit distance 0. By "known word" I mean a word that we have seen in the language model training data -- a word in the dictionary. We can implement this strategy as follows:
    
    
    def known(words):return set(w for w in words if w in NWORDS)def correct(word):  
        candidates = known([word])or known(edits1(word))or known_edits2(word)or[word]  
        return max(candidates, key=NWORDS.get)

The function correct chooses as the set of candidate words the set with the shortest edit distance to the original word, as long as the set has some known words. Once it identifies the candidate set to consider, it chooses the element with the highest P(_c_) value, as estimated by the NWORDS model.

## Evaluation

Now it is time to evaluate how well this program does. On the plane I tried a few examples, and it seemed okay. After my plane landed, I downloaded Roger Mitton's [Birkbeck spelling error corpus](http://ota.ahds.ac.uk/texts/0643.html) from the Oxford Text Archive. From that I extracted two test sets of corrections. The first is for development, meaning I get to look at it while I'm developing the program. The second is a final test set, meaning I'm not allowed to look at it, nor change my program after evaluating on it. This practice of having two sets is good hygiene; it keeps me from fooling myself into thinking I'm doing better than I am by tuning the program to one specific set of tests. Here I show an excerpt of the two tests and the function to run them; to see the complete set of tests (along with the rest of the program), see the file [spell.py](http://norvig.com/spell.py).
    
    
    tests1 ={'access':'acess','accessing':'accesing','accommodation':  
        'accomodation acommodation acomodation','account':'acount',...}  
      
    tests2 ={'forbidden':'forbiden','decisions':'deciscions descisions',  
        'supposedly':'supposidly','embellishing':'embelishing',...}def spelltest(tests, bias=None, verbose=False):  
        import time  
        n, bad, unknown, start =0,0,0, time.clock()  
        if bias:  
            for target in tests: NWORDS[target]+= bias  
        for target,wrongs in tests.items():  
            for wrong in wrongs.split():  
                n +=1  
                w = correct(wrong)  
                if w!=target:  
                    bad +=1  
                    unknown +=(target notin NWORDS)  
                    if verbose:  
                        print'%r => %r (%d); expected %r (%d)'%(  
                            wrong, w, NWORDS[w], target, NWORDS[target])  
        return dict(bad=bad, n=n, bias=bias, pct=int(100.-100.*bad/n),   
                    unknown=unknown, secs=int(time.clock()-start))print spelltest(tests1)print spelltest(tests2)## only do this after everything is debugged

This gives the following output:
    
    
    {'bad':68,'bias':None,'unknown':15,'secs':16,'pct':74,'n':270}{'bad':130,'bias':None,'unknown':43,'secs':26,'pct':67,'n':400}

So on the development set of 270 cases, we get 74% correct in 13 seconds (a rate of 17 Hz), and on the final test set we get 67% correct (at 15 Hz).

> **Update:**_ In the original version of this essay I incorrectly reported a higher score on both test sets, due to a bug. The bug was subtle, but I should have caught it, and I apologize for misleading those who read the earlier version. In the original version of spelltest, I left out the if bias: in the fourth line of the function (and the default value was bias=0, not bias=None). I figured that when bias = 0, the statement NWORDS[target] += bias would have no effect. In fact it does not change the value of NWORDS[target], but it does have an effect: it makes (target in NWORDS) true. So in effect the spelltest routine was cheating by making all the unknown words known. This was a humbling error, and I have to admit that much as I like defaultdict for the brevity it adds to programs, I think I would not have had this bug if I had used regular dicts. _
> 
> _ **Update 2:** defaultdict strikes again. [Darius Bacon](http://wry.me/~darius/) pointed out that in the function correct, I had accessed NWORDS[w]. This has the unfortunate side-effect of adding w to the defaultdict, if w was not already there (i.e., if it was an unknown word). Then the next time, it _would_ be present, and we would get the wrong answer. Darius correctly suggested changing to NWORDS.get. (This works because max(None, i) is i for any integer i.) _

In conclusion, I met my goals for brevity, development time, and runtime speed, but not for accuracy.

## Future Work

Let's think about how we could do better. (I've done some more in a [separate chapter](http://norvig.com/ngrams/) for a book.) We'll again look at all three factors of the probability model: (1) P(_c_); (2) P(_w_|_c_); and (3) argmax
