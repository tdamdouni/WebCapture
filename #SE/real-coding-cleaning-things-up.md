# Real Coding: Cleaning Things Up

_Captured: 2017-11-02 at 18:55 from [dzone.com](https://dzone.com/articles/real-coding-cleaning-things-up?edition=334828&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-02)_

Welcome to the [fourth installment of my _Real Coding _series](https://dzone.com/users/2776462/grzegorztj.html). In this part, we'll face the mess that we've made during the previous Pomodoro and make ourselves ready to implement the rest of our application's business logic. Let's dive straight into it!

## Moving Code Around

The first thing that I purposefully ignored at the beginning (and that has started annoying me already), was that I kept all of the code in a single source file. When you're just "sketching out" the initial design, creating a separate file for every single class is a waste of time, as classes are created and deleted very often in the process.

Now, as the design has matured a little bit (I hope), we can start extracting bits and pieces into separate files to avoid unnecessary distractions and an overall feeling of messiness. A good starting point is a single source file for each of the aggregates with their related classes and a separate file for the only service that we've got.

![Image title](https://dzone.com/storage/temp/7052147-new-structure.png)

At a later stage, when the aggregates themselves grow, these files might be further split into separate packages. I won't do this now, as I see no need to do so. Decisions like this one are easy to change later, so it's better not to overthink and just stick with what feels right at the moment.

## Unfinished Business

[In the previous part](https://dzone.com/articles/real-coding-a-grand-redesign), as I split a huge Ranking aggregate into a few smaller aggregates, I wrote a piece of code like this:
    
    
                  val ratings: Set<Rating> = mutableSetOf(),
    
    
                  val matches: MutableList<Match> = mutableListOf()) {
    
    
        fun isRanked(player: Player) = ratings.any { it.player == player }
    
    
            if (!ranking.isRanked(player))

As you can see, there's a "business" rule here that says that we cannot create a match if any of the players have not joined a given ranking. That decision was taken in [Part 2](https://dzone.com/articles/real-coding-joining-a-ranking-and-playing-a-match), and I'd like to stick to it for now.

The problem with this piece of code is the cyclic dependency between the _rating _and the _ranking_, which proved annoying when trying to update the tests according to the redesign. I've decided to tackle this problem by moving the check into a factory, which will base the decision based on the _ratings _rather than the _ranking _object itself:
    
    
        fun create(dateTime: LocalDateTime, player1: Player, player2: Player, ranking: Ranking, result: MatchResult): Match {
    
    
            return Match(dateTime, player1, player2, ranking, result)

This way, if I want to test any method that requires a _player_ to join a _ranking_, I can simply create the necessary _rating_ instead of also updating a related _ranking object._

## The Green Bar Is Back!

Now that I satisfied my desire to move things around and the testability has been improved, I got a chance to get the tests working again so that the project is fully on the right track.

The path to the Green Bar Heaven was relatively easy, as it just required me to instantiate the service with all necessary dependencies and invoke the service instead of the previously refactored aggregate:

There are a few smells here, which I'm not yet sure I'll act upon:

  * The service requires quite a few dependencies to do its job, and it's not settled that these are all that will be ever needed.

  * The in-memory repositories would probably benefit from some setup method so that I don't access their underlying collections directly.

  * The second test asserts _match _equality, which I'm not sure is a good idea. Semantically, I'd rather check that "a match with provided parameters has been added", rather than "that specific match has been added".

Anyways, the code above will suffice for now and I'm happy to be back in the green.

## Next Steps

At this point, I ran out of time for this Pomodoro, so here ends the article. The code appears to be clean enough to proceed and implement the rest of the application's use cases. The challenge for next time? Implement and test all of the remaining business logic for solo player games, so that I can finally have a working piece of software.
