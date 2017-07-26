# Is Complexity Better Than Length When it Comes to Passwords?

_Captured: 2017-03-13 at 22:34 from [dzone.com](https://dzone.com/articles/is-complexity-better-than-length-when-it-comes-to?edition=281883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-13)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Most organizations have password policies that require users to change their passwords every XX days, and that they use a minimum (or sometimes fixed!) length, and a combination of capital and small letters, numbers and special symbols. But what exactly makes a password "strong" or difficult to guess?

Entropy can be used to measure the complexity of an information string - or the number of possible combinations within the given "rule" for constructing a string if you want. To calculate the information entropy of your password, use this formula:

> ENTROPY = LOG (Characters in set you make password from) / LOG (2) x (Length of password)

So, comparing a password using only lower case letters, and one with a combination of upper case and lower case, we get that the entropy in the first case is 37, and in the latter case it is 45. This means the latter case is harder to crack using brute-force attacks - but how much so? (Higher entropy is better). Open security research has made a calculator for [brute force time](http://calc.opensecurityresearch.com/) that we can use to estimate that. The estimate is based on benchmarks for common cracking tools on a regular consumer grade PC. Assuming an SHA-encrypted salted password we get about 7 hours to crack the first but 2000 hours to crack the latter - entropy is obviously a big deal. As we see from the formula above, increasing the character set length is one way to increase entropy, the other one is increasing the length of the password itself. Note that in terms of cracking - using some symbols or characters not normally found in words is necessary to avoid dictionary based attacks - these brute force times are "worst-case times" seen from the attacker perspective - the time it takes to exhaust the entire character space.

## What Is Better - More Characters or Longer Passwords?

Turning to some basic maths, we can use the formula for entropy to look at the effects of increasing character set size versus password length. The entropy is proportional to the logarithm of the character set size - that means entropy growth rate with character set size c is 1/c. When c is large, the derivative approaches zero; increasing the set size is efficient for small set sizes but the value of doing so becomes smaller as the set size grows larger.

![charset_entropy](https://safecontrols.files.wordpress.com/2017/03/charset_entropy.png?w=739)

The effect of increasing character set size on entropy is best when the charset is still small.

The effect of increasing password length, however, is linear and remains the same for a given charset size for each length of the password. What does this mean in practice?

  * Add complexity up to a certain level - that also takes away dictionary attacks as an efficient way to brute-force the password.
  * Increase length after that instead of including more complexity.

Using the brute force time calculator, we estimate the following exhaustion times:

  * Lower case letters, 8-character password: 7 hours to crack.
  * Lower case and upper case letters, 8-character password: 2000 hours to crack
  * Lower case letters, 16-character password: 189 million years to crack
  * Lower and upper case letters, 16-character password: 12 trillion years to crack

Logical conclusion: use passphrases with some added complexity. This makes a brute-force attack on your password extremely difficult.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
