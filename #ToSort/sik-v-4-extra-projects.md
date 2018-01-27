# SIK v4.0 Extra Projects

_Captured: 2017-11-29 at 22:48 from [www.sparkfun.com](https://www.sparkfun.com/news/2538?utm_content=63775146&utm_medium=social&utm_source=twitter)_

One of the most exciting aspects of the new [SparkFun Inventor's Kit (SIK) v4.0](https://www.sparkfun.com/products/14265) is that the parts and experiments were chosen to create finished, functional projects. Because of this new, project-focused spin on our popular beginner's kit, I found that taking things further to create even more new projects was a breeze. If you've worked through the projects in the SIK (or if you're hoping to get one for the holidays), I've put together three additional projects that you can complete (with few or no extra parts required).

### Clap On Lamp

The phrase "Clap On! Clap Off!" might arouse fond nostalgia from [TV commercials of yesteryear](https://www.youtube.com/watch?v=Ny8-G8EoWOw). If not, don't worry! We'll use a [Sound Detector board](https://www.sparkfun.com/products/14262) and parts from the SIK to detect two successive, sharp noises to pull a chain on a lamp.

Adding a servo to a pull-chain lamp is an amusing way to create an automated lighting system. In addition to the sound detector board, you could use a [light sensor](https://www.sparkfun.com/products/9088) to pull the chain when the ambient room lighting falls below a certain level, or you could add an [ultrasonic sensor](https://www.sparkfun.com/products/13959) to work as a virtual trip wire so that the light turns on whenever something gets near the lamp.

A full walkthrough for building the sound detecting lamp system can be found here:

### Light-Seeking Robot

One of the final projects in the SIK v4.0 guide is a [fully autonomous robot](https://learn.sparkfun.com/tutorials/sparkfun-inventors-kit-experiment-guide---v40/circuit-5c-autonomous-robot) that detects and avoids obstacles. We can expand on the robot by replacing the ultrasonic sensor with the included photocell in order to detect areas of bright light.

For educators, this might be a useful project for showing how simple organisms, like [Euglena](https://en.wikipedia.org/wiki/Euglena), seek out light for assisting with photosynthesis. The tutorial shows how to perform a very simple search algorithm: look left, right and center; choose the direction with the most light; and move in that direction. Computer scientists (or anyone interested in learning about artificial intelligence) could take the project even further to implement a [Q-Learning algorithm](http://www.informit.com/articles/article.aspx?p=26423) with additional sensors to help the robot learn its environment.

![](https://cdn.sparkfun.com/c/500-282/assets/learn_tutorials/7/1/3/SIKv4_Projects-12.jpg)

> _Light-Seeking Robot_

### Endless Runner Game

Any gamers in the audience might remember the endless running (or endless flying, I suppose) games [Temple Run](https://en.wikipedia.org/wiki/Temple_Run) and [Flappy Bird](https://en.wikipedia.org/wiki/Flappy_Bird). The premise is simple in these endless-style games: your character moves forward, and the player must make one or more simple choices to avoid obstacles (turn left/right, jump, etc.). Instructables user [joshua.brooks](http://www.instructables.com/member/joshua.brooks/) created a wonderfully addicting endless runner game using an Arduino, a character LCD and a single button (the original project can be found [here](http://www.instructables.com/id/Arduino-LCD-Game/)).

We've updated the project to show how it can be made with parts from the SIK.

As the terrain flies by, players must time their jumps by pressing the button at the right moment to avoid hitting the rather rectangular hills. Points are awarded based on distance -- and if you hit something, it's game over. The circuit and code for the game can be found here:

![](https://cdn.sparkfun.com/assets/learn_tutorials/7/1/6/LCD-screen.gif)

> _Endless Runner Game_

These three projects should be fun additions to your SIK repertoire. What other simple Arduino projects have you seen that would be good for beginners and students? Let us know in the comments below.
