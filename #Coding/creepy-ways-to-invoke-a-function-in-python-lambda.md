# Creepy Ways to Invoke a Function in Python: Lambda

_Captured: 2018-09-13 at 20:34 from [dzone.com](https://dzone.com/articles/creepy-ways-to-invoke-a-function-in-python-lambda?edition=391225&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-09-13)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

![Image title](https://dzone.com/storage/temp/10161436-computer-programming-languages-word-cloud-dp-336x2.jpg)

Whenever I begin learning a new language, I immediately get super cocky and say out loud, "I know everything, I'm a genius how hard can it be!?"

... before those beastly bus terminal cops come and ask me to leave.

But, as always, while snoozing under the bridge covered in my own soil, I perk up and realize that this particular language has handed me a challenge.

Python has a couple of very sexy ways of invoking a function.

Even the name is sexy, isn't it? _Python_.

I never digress.

Sure you can just define a function...

Then call it...

But that's is so 90's.

![Image title](https://dzone.com/storage/temp/10161449-beanie3.jpg)

"Hey nerd, did that function come with a free Beanie Baby?"

And, yeah, I know Python was invented in the '50s to defeat Hitler's Spanish Armada, but sometimes old things can still seem new.

Upon first exploring the **lambda** operator my brain contracted and shat out the word "No" several times.

(Shat is not a curse word.)

The lambda operator is a quick and useful way of declaring, using, and throwing away a small function...

The general expression of a lambda function is this...

The lambda operator is useful when you just want a simple calculation done on a set of data ONCE. You don't have to name it and you can use it with other operators like Map or Filter which makes it an extremely powerful tool...

The above code block will apply the map operator to your little lambda function, multiplying everything in your list by 2.

Some developers don't use this technique, mainly for readability reasons. Some will claim that it is more difficult to study code like this then code with obviously declared functions.

On the other hand, many will contest that the lambda function is MORE readable and constructive than its generic counterpart. In my opinion, it comes down to a situational question.

A lambda call could theoretically stretch out to hundreds or even thousands of characters. I'm not sure you're going to find anyone claiming that this makes code easier to follow. Quite to the contrary, and probably a good spot to construct a function in its original intended shape (or an entire Class, but let's not get into that just yet).

However you end up using it, lambda can be a fantastic, fast (and fun) alternative.

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)
