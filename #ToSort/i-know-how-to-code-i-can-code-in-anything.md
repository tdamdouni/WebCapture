# I Know How to Code, I Can Code in Anything

_Captured: 2017-11-11 at 00:41 from [dzone.com](https://dzone.com/articles/i-know-how-to-code-i-can-code-in-anything?edition=334862&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-10)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Every time I talk to a recent grad I hear a variation of the phrase, "I know how to code, I can code in anything." This is, on the surface, true for some bits like boolean logic and loops. Where it starts to fail for me is when I need to leverage a language's ecosystem. I'm a Ruby programmer at heart (for the last 10+ years), yet I'm being forced to write in other languages through my CS Masters classes at Georgia Tech. I know I'm a competent coder, but can I really "code in anything"? How much does skill in one language translate to another?

First a story about not knowing a programming language. In 2012, I was working for [Gowalla](https://en.wikipedia.org/wiki/Gowalla) (THE major competitor to Foursquare). When the company went under, I started looking for a new job right away. I had two great phone interviews with another social networking company, whose name will be withheld for dramatic suspense. The team was small, but I talked to both founders and we hit it off.

The company only had a mobile app and no website but wanted to build one. If hired, I would be given that task. The only hitch: the API and therefore the future website were written in Python and I didn't know Python.

I expressed my lack of knowledge in the language and both founders were very insistent that they only cared that I **could** program, not **what** (language) I could program. I decided to pick up "Learn Python the Hard Way" and dig in. The language was very similar to Ruby (which I had been coding with for years at the time). Yet it was just so subtly different it hurt. As if someone came into your house and moved every piece of furniture over to the right by 3 inches without telling you.

Philosophies for the two languages are very different as well. One of my favorite examples is looking for an element in an array (list in Python). In Ruby, if you find nothing in the array, it returns `nil` (the equivalent of `None` for Python). In the example in LPTHW, if Python did not find the element in the list, it raised an exception.

I liken this to telling each language to go get some milk from the grocery store. Ruby goes to the store, finds no milk and returns no milk ( `nil`). Python goes to the store, finds no milk and BURNS THE STORE TO THE GROUND (raises an exception)!

> Note: I'm sure someone coming from Python to Ruby would have similar growing pains. I'm not picking on Python here.

Okay, so that's not totally fair to Python, but it's how it felt to me. I ended up being so worried about not being productive in the language I never reached out to schedule my second series of interviews onsite (located in SF). The company was so small I wasn't going through a recruiter, I was going directly through the founders. We basically fell out of touch. I ended up taking a job at [Heroku](https://heroku.com/) instead ( a remote position that let me stay in Austin).

A while later, this small social networking company was in the news, they were bought by Facebook for a BILLION dollars. The name?

Instagram.

Would I have gotten the job for sure if I had followed up? Who knows. Would I have had enough stocks from the sale to matter if I had been hired? Probably at least a little.

I tell you this not as a story of my bad luck or judgment. It's not a story about sour grapes, how I'm so much happier at Heroku, and had I left Austin I likely wouldn't have married my wife (whose name is also Ruby, by the way). The point to take away really is that I didn't feel like I could actually work at a professional level in another language then. What about now?

I've spent one entire semester coding with Python for a Robotics course with the Georgia Tech Online CS Masters program. I'm now in the middle of an Artificial Intelligence course which also uses Python. I'm still not comfortable with the language the way a warm sweater feels in the winter, but I'm proficient at it.

The fun thing about the current AI course I'm in now is it requires not just any Python code, it requires FAST Python code. I love optimizing for performance and I do it all the time in Ruby.

Before I started the course I asked, can I, as someone who spent 3 months half-a-year ago writing Python, write fast Python code? As it turns out, yes. With considerable time and difficulty, I can optimize the crap out of some Python code. I was able to make my slowest bottleneck (code provided by the teachers) 5x faster. However, could someone who has 3 years of experience with Python do better? Likely. You can read about the experience at [Lifelong Rubyist makes some Python code 5x Faster](https://schneems.com/2017/10/02/lifelong-rubyist-makes-some-python-code-5x-faster/).

Another of my strong programming skills is in object-oriented design. I feel very comfortable building and using classes for performance, readability, and cleanliness. Yet there are base assumptions that matter when designing your interfaces at the beginning that make a world of difference in the end. Not knowing the constraints of Python or what patterns were preferred means that I inherently shipped a worse product than I would have if it had been done in Ruby.

What's the point of all of this? I guess it's to say that while programming skills acquired in one language do extend to others, it takes time and patience working with them to be able to fully realize the benefits. Things like best practices and common patterns might seem second nature to you in your preferred language, but take a large amount of time to pick up (at least for me) when moving to a new language. I'm constantly having to balance getting the task done at hand (exploiting my existing knowledge) versus learning more about the language and ecosystem to write better code (exploring the ecosystem). Until I hit a point where I can exploit more than explore, I don't really feel comfortable with a new language or toolchain.

At the end of the day, this statement is fairly universally true: "I know how to code, I can code in anything," therefore it doesn't set you apart from all the other programmers in the world. When I was talking to Instagram and they said "we don't care if you know Python," they also said they cared that I had social network experience and that would make up for it. At the time I felt that my productivity (and therefore value) would be drastically reduced if I had to switch over to using Python full time. I thought that there was no way my experience working on Gowalla could possibly be valuable enough to overcome my inexperience with the language. I imagined my first week on the job would go okay as I asked a bunch of silly questions, but on month three when they really figured out just how little of the language I knew, surely they would kick me to the curb. Right?

I think that had I taken the job I would have built what can be fairly described as "a web app" and likely it would have not totally failed. The acquisition would have still happened. I might have written a sloppy or awful web app, but it likely would have still worked. From their perspective, if that was all they wanted, then I think they were right. I could have done the job to the completeness which they required. On the flip side, I don't think I would have been happy with the code I wrote, or with the maintenance burden of the ball of mud I would have created.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
