# Real Coding: A Grand Redesign

_Captured: 2017-10-30 at 20:08 from [dzone.com](https://dzone.com/articles/real-coding-a-grand-redesign?edition=334817&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-30)_

Welcome to the third installment of the Real Coding series, in which I'm solving a real-world coding problem to share my knowledge and way of thinking about programming with a wider audience. The series ([Part 1](https://dzone.com/articles/real-coding-quotenterprisequot-ranking-application) and [Part 2](https://dzone.com/articles/real-coding-joining-a-ranking-and-playing-a-match)) is split by individual Pomodori of work that I perform on the project. During this particular Pomodoro, I began a grand redesign of an application's domain. Let's have a closer look.

## What?! Why?

As some of you might recall, the application being built throughout the series is an "enterprise-grade" ranking system. Since I'm aiming for completing the whole system in around 15 Pomodori, doing one Pomodoro per day (The Pomodori days are not necessarily consecutive due to a tight schedule), I kind of rushed through the initial design phase with something like this:
    
    
                  val ratings: MutableMap<Player, Rating> = mutableMapOf(),
    
    
            if (!ratings.containsKey(player))
    
    
            val match = matches.find { it.id == id } ?: throw MatchNotFoundException(id)

My gut was telling me the whole time that this might not be the best design, but for the lack of a better alternative, I stuck with it.

A few days ago, I had a brief chance to take a look at Epic Games' newest production: Fortnite Battle Royale. As it turns out, Epic Games' developers are currently working on a ranking solution of their own. I conducted a super-short thought experiment: How would my design perform in a > 10 million player online game?

Well, I guess it goes without saying that it would completely fail and blow up the server each time it attempts to load a ranking. While my ranking system is more aimed at small groups, like my company's Ping Pong players, the complete lack of scaling feels bad. "Too bad."

## Looking For a Better Design

Having decided that to (at least partially) solve the problem, I had to come up with a better design. To do that, I had to answer the question: _Why exactly does the current design fail so badly?_

The answer to this question is not rocket science. We're loading all of the possible _matches_ and _ratings_ to the server's memory at once, while what we need is just a couple of _ratings_ to update (or a hundred in the battle royale case). The `Ranking` class in the form above is an example of a particularly bad aggregate pattern usage.

The solution to our scaling problem also lies in the answer above. Instead of loading all of the _ratings_, we need to load specific ones. This calls for promoting the `Rating` class from a mere value object to an aggregate root of its own and promoting the `Match` class to an aggregate root as well.
    
    
            if (!ranking.isRanked(player))
    
    
                  val ratings: Set<Rating> = mutableSetOf()) {
    
    
        fun isRanked(player: Player) = ratings.any { it.player == player }

## Wait, Where Did the Logic Go?

As you've probably noticed, the Ranking class is no longer a holder of all the use-case-related logic like joining a ranking or adding a match. As _ratings _and _matches_ are now aggregates, they are to be created and managed independently of the _rankings_. This calls for moving the use-case logic into domain services instead of stacking it all with the _ranking_.
    
    
            val player = players.byName(request.player)!!
    
    
            val ranking = rankings.byName(request.ranking)!!
    
    
            ratings.add(Rating(player, ranking))
    
    
            val player1 = players.byName(request.player1)!!
    
    
            val player2 = players.byName(request.player2)!!
    
    
            val ranking = rankings.byName(request.ranking)!!

As you can see, there's still some stuff to do, like handling the case of an invalid request, but that's for next time. Also, so far, I've put everything into a single class, but there's a high chance that each of the "use cases" will get a class of their own at one point.

As we moved the code from the domain layer to the service layer, we're now accessing domain objects via repositories rather than via fields. Since I don't have a clue about the data storage yet, these are just regular Kotlin interfaces.
    
    
        fun byName(name: String): Ranking?

## Uncle Bob Won't Be Proud, But…

Despite my attempts, I failed in the process of performing the redesign and keeping the tests working at all times. I didn't think the process through and I started by moving the `addMatch` method to the service while completely ignoring that joining is a prerequisite to adding a match. Having realized that, I decided to keep going and live with a red bar for a while.

(I decided to not show you the non-working tests. We'll look at them once they're finished.)

A glass of water for the burning torches of you Uncle Bob fans might be that I've resisted the temptation to use a mocking framework and implemented in-memory repositories by myself:

## Summary

There's a lot of work behind us and still quite a lot in front. In general, I believe that the redesign will make the application a better fit for larger companies and a better example of enterprise-grade code. This project aside, a lesson learned is worth noting for anyone: a big aggregate can cause BIG problems when good scaling is required.
