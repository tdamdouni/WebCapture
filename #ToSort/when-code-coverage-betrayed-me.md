# When Code Coverage Betrayed Me

_Captured: 2017-04-13 at 01:43 from [dzone.com](https://dzone.com/articles/when-code-coverage-betrayed-me?oid=twitter&utm_content=buffer6d2f0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

I'm a fan of [code coverage](https://coding.abel.nu/2015/12/code-coverage-does-matter/) as a way to ensure that there are covering tests. One area that I tend to rely heavily on code coverage for is to catch any tests that are no longer working correctly due to changes in the production code. That often works out well -- but today, I got betrayed by the code coverage engine.

The code that I worked on contained an `if` statement with a multi-step `&&` expression.

    
    void IsAllWrong(int importantValue, bool b)
	{
	  bool a = importantValue == GetAnswer();
	  bool c = false;
	  bool d = false;
	  if (!a && !b && !c && !d)
	  {
    return true;
	  }
	  return false;
	}
      

Of course, I had tests that made the evaluation fail both because of `importantValue` and `b`. So, what happened later was that `GetAnswer()` was updated without the test for when the`importantValue` was being updated. Of course (my bad), that test had set `b` to `true`, causing the evaluation to fail on `b`, causing `true` to be returned.

So, the test passed, but not due to the thing I wanted to test. In a complex application, this is bound to happen every now and then. But usually, the code coverage scores will reveal that there is an execution path not covered. But not this time! The trustworthy code coverage analysis betrayed me!

## Into the IL Code

To understand why I was betrayed by code coverage, we'll have to look at the IL code generated. It looks like Visual Studios' code coverage doesn't check branch coverage, but rather just IL instruction coverage. In most cases that's the same, but not this time.

	// Initialize a, b, c & d
	IL_0000:  nop         
	IL_0001:  ldarg.1     
	IL_0002:  ldarg.0     
	IL_0003:  call        UserQuery.GetAnswer
	IL_0008:  ceq         
	IL_000A:  stloc.0     // a
	IL_000B:  ldc.i4.0    
	IL_000C:  stloc.1     // c
	IL_000D:  ldc.i4.0    
	IL_000E:  stloc.2     // d
	// Evaluate conditional expression
	IL_000F:  ldloc.0     // a
	IL_0010:  brtrue.s    IL_001E
	IL_0012:  ldarg.2     // b
	IL_0013:  brtrue.s    IL_001E
	IL_0015:  ldloc.1     // c
	IL_0016:  brtrue.s    IL_001E
	IL_0018:  ldloc.2     // d
	IL_0019:  ldc.i4.0    
	IL_001A:  ceq         
	IL_001C:  br.s        IL_001F
	IL_001E:  ldc.i4.0    // Run if expression was short circuited by a, b or c being true.
	IL_001F:  stloc.3     
	IL_0020:  ldloc.3     
	IL_0021:  brfalse.s   IL_0029
	IL_0023:  nop         
	IL_0024:  ldc.i4.1    
	IL_0025:  stloc.s     04 
	IL_0027:  br.s        IL_002E
	IL_0029:  ldc.i4.0    
	IL_002A:  stloc.s     04 
	IL_002C:  br.s        IL_002E
	IL_002E:  ldloc.s     04 
	IL_0030:  ret

We can see that the evaluation of the conditional expression takes the form of loading each of `a`, `b`, and `c`, and then short-circuiting the evaluation if the variable is `true`. The problem is that if either of `a`, `b`, or `c` is `true`, then the branch instruction points to the same target: `IL_001E`. So, to get all IL instructions to run, it is sufficient to test for two cases:

  1. `a=b=c=d=false`
  2. `a=true; b=c=d=false`

I still had both those cases covered. And because I was sloppy and passed in `true` for `b` when testing `importantValue`, the unit test still passed.

So what I've learned today is:

  * Don't rely on code coverage to accurately calculate branch coverage.
  * When writing tests for a complex if statement, it is risky to be sloppy with the parameters tested after the relevant one. Even though they are not relevant because of expression short-circuiting when everything works, bad values can make the test pass on the wrong premises.
