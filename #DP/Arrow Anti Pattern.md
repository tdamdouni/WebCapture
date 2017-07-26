# Arrow Anti Pattern

_Captured: 2015-12-13 at 15:49 from [c2.com](http://c2.com/cgi/wiki?ArrowAntiPattern)_

Consists of code where nested if statements generate an arrow shape, like so: 
    
    
     if
       if
         if
           if
             do something
           endif
         endif
       endif
     endif
    

It often develops when a programmer applies the "[OneReturnPerFunction](http://c2.com/cgi/wiki?OneReturnPerFunction) rule" blindly and in poor taste, or when mixing both conditions and loops. The best fix is to [RefactorLowHangingFruit](http://c2.com/cgi/wiki?RefactorLowHangingFruit): simply splitting the entire function in half can lead to two big, ugly functions with lots of arguments and no concept. Instead, refactor the components of the code: often the conditions can be inverted and used as [GuardClause](http://c2.com/cgi/wiki?GuardClause)s, removing them from the structure; [ExtractMethod](http://c2.com/cgi/wiki?ExtractMethod) can convert the contents of loops into separate functions. And the [ExecuteAroundPattern](http://c2.com/cgi/wiki?ExecuteAroundPattern) is a magic wand with limitless charges. _Interestingly, Dr. LanceMiller[?](http://c2.com/cgi/wiki?edit=LanceMiller) of IBM contrasted this kind of structure with English, where you usually start with a verb and qualify it, e.g. "heat water until boiling". I guess that's an argument for the Perl syntax...?_ \-- [PaulMorrison](http://c2.com/cgi/wiki?PaulMorrison) In [CodeComplete](http://c2.com/cgi/wiki?CodeComplete), [SteveMcConnell](http://c2.com/cgi/wiki?SteveMcConnell) notes that comprehension decreases beyond three levels of nested 'if' blocks, according to 1986 study by [NoamChomsky](http://c2.com/cgi/wiki?NoamChomsky) and [GeraldWeinberg](http://c2.com/cgi/wiki?GeraldWeinberg). McConnell[?](http://c2.com/cgi/wiki?edit=McConnell) refers to the [AntiPattern](http://c2.com/cgi/wiki?AntiPattern) as "Dangerously Deep Nesting". _If the arrow is an [AntiPattern](http://c2.com/cgi/wiki?AntiPattern), consider a whole mountain range: <http://thedailywtf.com/Articles/Coding-Like-the-Tour-de-France.aspx>_ That expression above is bad, but not the worst of it... 
    
    
     if get_resource
       if get_resource
         if get_resource
           if get_resource
             do something
             free_resource
           else
             error_path
           endif
           free_resource
         else
           error_path
         endif
         free_resource
       else
         error_path
       endif
       free_resource 
     else
       error_path
     endif
    

This style puts much error recovery and clean-up code very far from the thing that spawned the error. [HoursOfFun](http://c2.com/cgi/wiki?HoursOfFun)! A good fix: Just make the code completely exception safe. This would ensure nobody cares who cleans up what or how. _Ahh, yes. "Just make the code completely exception safe," quotha. Like, how? This is a particularly tricky problem in embedded systems, where the resource being acquired is usually a piece of hardware with distinct setup/setdown conditions. Hmm._ How about: (with-resource-foo (foo ...) ... ) ? I guess that is cheating. :) _It's a good fix to make _one_ of those objects exception-safe at a time. [RefactorDaintily](http://c2.com/cgi/wiki?RefactorDaintily) would clean much of the function up, leaving the rest more obvious._ It is possible to implement resource-safe exception handling cleanly and elegantly if you have a language like [CeePlusPlus](http://c2.com/cgi/wiki?CeePlusPlus) which supports the [ResourceAcquisitionIsInitialization](http://c2.com/cgi/wiki?ResourceAcquisitionIsInitialization) technique (and this method is by no means exclusive for dealing with such things but just happens to be my personal favourite). However, suggesting that you "just" make the code exception-driven, while correct, is not particularly pragmatic ([JustIsaDangerousWord](http://c2.com/cgi/wiki?JustIsaDangerousWord)), as often such a refactor has a cascade effect as you shift the error handling around (and usually further up) the call stack. In my experience, [ArrowAntiPattern](http://c2.com/cgi/wiki?ArrowAntiPattern) code is symptomatic of code written without attention being paid to proper [ModularProgramming](http://c2.com/cgi/wiki?ModularProgramming) techniques, and hence was probably written by a [BadProgrammer](http://c2.com/cgi/wiki?BadProgrammer) (an opinion which would strengthen for me proportionally to the scale of the problem: [ThreeStrikesAndYouRefactor](http://c2.com/cgi/wiki?ThreeStrikesAndYouRefactor)). Often, a possible solution is to use [PolyMorphism](http://c2.com/cgi/wiki?PolyMorphism) to decouple the semantic from the control flow - i.e. you can partition all the bits inside all those if-else blocks into small functions that are called appropriately (polymorphically), while exceptions take care of all those error paths. The solution we adopted ages ago, and which has made our code clean, clear, short, elegant and largely bug-free is this. Require that each "get_resource" call returns "false" on failure and requires no further cleanup, or "true" on success and provides a clean-up resource release callback. The callback is added to a structure (list), and that's then called at the end. Code now looks like this: 
    
    
        callback_list = []
        if ( get_resource_A(&callback_list,...) &&
             get_resource_B(&callback_list,...) &&
             ...
             )
        {
            success_flag = do_work();
        }
        for closure in callback:
            eval(closure);
    
    

The true syntax is not too bad, but I've simplified it here to avoid obscuring the main point. Our more complex systems provide a structure that has both "success" and "failure" callback lists, to ensure that error reporting and error recovery are handled correctly, and are reasonably close to the place that caused them. For another solution, see [FunctionWrapper](http://c2.com/cgi/wiki?FunctionWrapper). See also: [BouncerPattern](http://c2.com/cgi/wiki?BouncerPattern), [TrivialDoWhileLoop](http://c2.com/cgi/wiki?TrivialDoWhileLoop), [ElseConsideredSmelly](http://c2.com/cgi/wiki?ElseConsideredSmelly) If you're using [JavaLanguage](http://c2.com/cgi/wiki?JavaLanguage), the [PeeEmDee](http://c2.com/cgi/wiki?PeeEmDee) code inspection tool can find deeply nested if statements. I've quite often written (C99-ish) code like the following: 
    
    
      bool open_some_object(Object *object)
      {
        assert(object);
        if(open_resource_a(&object->a))
        {
          if(open_resource_b(&object->b))
          {
            if(open_resource_c(&object->c))
            {
              return true;
            }
            close_resource_b(&object->b);
          }
          close_resource_a(&object->a);
        }
        return false;
      }
    
    

Which looks similar to the anti-pattern, with the exception of the 'return true' in the middle. If the function succeeds, it returns as soon as it's succeeded. If anything fails, the function closes anything which was opened, and then returns false. I've always thought this was quite an elegant way of initializing objects, but maybe I've mislead myself? Is this the anti-pattern, or does it just happen to look like it? Is there a better way of opening objects which are composed of sub-objects? Yes, this is still the arrow anti-pattern because it's hard to match up the open/close. In your example, it's only 3 deep, so it's not too bad. But consider if you have 10 or more resources to initialize. The real problem here is that the open_resource_X() functions fail to clean up after themselves on error. If it is at all possible, please put the cleanup_on_error handling inside the function responsible for the error. If you can't rewrite those functions, then consider wrapping them in a function that does properly cleanup on error. You could write N different functions to wrap all N open_resource_X(), but it might be easier to just do something like this: 
    
    
      typedef void (*Close)(void*);
      typedef bool (*Open)(void*);
    
      bool try_open(Open open, Close on_error, void* arg)
      {
          if(open(arg))
            return true;    
          on_error(arg);
          return false;
      }
    
      bool open_some_object(Object *object)
      {
        assert(object);  
        return try_open(open_a, close_a, &object->a) &&
               try_open(open_b, close_b, &object->b) &&
               try_open(open_c, close_c, &object->c);
      }
    
    

There are a multitude of cleaner/shorter alternatives in other languages, but this should work for C99. -- DerrickSoutherland[?](http://c2.com/cgi/wiki?edit=DerrickSoutherland) One of my favorite refactorings of the [ArrowAntiPattern](http://c2.com/cgi/wiki?ArrowAntiPattern), when the guard clause pattern doesn't work, is to unstack the blocks into smaller blocks, so each one takes the partial result of the preceding block, and produces a partial result for the next block. The nested loop... 
    
    
     use_items = []
     list.each do |item|
       if !item.nil? then
          if item.category == 'foo' then
            use_items << item
          end
       end
     end
    

...can be rewritten as... 
    
    
     non_nil_items = list.filter {|i| !i.nil?}
     use_items = non_nil_items.filter {|i| i.category == 'foo'}
    

This example is somewhat contrived, because the code is in Ruby, but Ruby has short circuiting for conditionals, so we didn't have to nest the 2 "if" statements inside the loop in the first place. It's hard to think of pathological starting points in Ruby, though :) I've often seen code like that when dealing with low-level services that must be gained incrementally, but saw no easy fix. One approach that at least avoids deep nesting is something like: 
    
    
      good = true;
      if (good) {
        if (! get_resource_1()) {
          error_handling...
          close_resource_1;  // if applicable (perhaps call it "clean up")
          good = false;
        }
      }
      if (good) {
        if (! get_resource_2()) {
          error_handling...
          close_resource_2;
          good = false;
        }
      }
      if (good) {
        if (! get_resource_3()) {
          error_handling...
          close_resource_3;
          good = false;
        }
      }
      ...
      if (good) {     
        regular_process...
        close_resource_1;
        close_resource_2;
        close_resource_3;
      }
      ...
    
    

It is easier to insert a new handling level since it is "linear" in nature. It seems a case where HOF may be handy, if you want to take on the issues of moving up the meta scale. _This can be improved if nested inside a method that returns after each failed acquisition, so that adding new attempts are wholly linear, and the flag checks vanish_ Would the calls be nested? I thought the idea was to remove nestedness. _I can't see how the above code releases resource_1 if the acquisition of resource_2 fails. Does each "close_resource_n" call "close_resource_m" for every m<=n? Isn't this potentially huge code duplication?_ I generally assumed **diverse resources**. For example, resource 1 may be a file, resource 2 a database, resource 3 a pipe, etc. There may be conceptual duplication, but not necessarily implementation duplication. Of course, if they are similar, then please do factor the commonality to a function/method/class/module. _How about the following:_
    
    
      function open_resources {
        failed_resource = 0;
        // For each resource
        if (! get_resource_N()) {
          close_resources(N);
          failed_resource = N;
        }
        return failed_resource;
      }
      function close_resources(int N) {
        for (rn=1; rn<=N; rn++) {
          close_resource(rn);
        }
      }
    
    

_PS: Gracefully handling failures when closing resources is left to the user._ Per above, this may not work well for diverse resources. A python class: 
    
    
      class Resources(object): 
        "Manages resource sequence acquisition and release" 
        def __init__(resources, *required): 
          resources.required = list(required) 
    
        def acquire(resources): 
          resources._acquired = [] 
          for Resource in resources.required: 
            resources._acquired.append(Resource()) 
    
        class Failures(Exception): 
          def __init__(exception, message, resources): 
            super(Failures, exception).__init__(message) 
            exception.resources = resources 
          def __repr__(exception): 
            reasons = []
            for resource, reason in exception.resources:
                reasons.append(resource+": "+reason)
            return exception.message + '\n'.join(reasons) 
    
        def release(resources): 
          "This can be retried upon failure" 
          failures = set() # try to close them all even if some fail to close 
          while resources._acquired: 
            resource = resources._acquired[0] 
            try: 
              resource.release() 
              resources._acquired.pop(0) # there must be one 
            catch Exception, exception: 
              failures.add((resource, exception)) 
          if failures: 
            raise Resources.Failures("Couldn't close the following:", failures) 
    
        def use(resources, do): 
          try: # note this is not catching exceptions, only ensuring cleanup 
            resources.acquire() 
            do(*resources._acquired) 
          finally: # this always runs 
            resources.release() 
    
    

\-- MikeAmy[?](http://c2.com/cgi/wiki?edit=MikeAmy) See also: [AvoidExceptionsWheneverPossible](http://c2.com/cgi/wiki?AvoidExceptionsWheneverPossible) There is a well-established pattern for C that solves this issue to some extent: 
    
    
      bool function(...) {
          FOO f = NULL;
          BAR b = NULL;
          bool res = false;
          f = allocate_foo();
          if(!f)
              goto cleanup;
          b = allocate_bar();
          if(!b)
              goto cleanup;
          res = ... // do something with f & b
      cleanup:
         if(b)
             release_bar(b);
         if(f)
             release_foo(f);
         return res;
      }
    
    

Note that this code is probably only applicable to C (and maybe to some extent to C++), most other languages can achieve similar or better results using automatic cleanup. In the presence of exceptions, this is even a must, as any function in between might throw already. For languages with lazy cleanup (e.g. Java and Python), using a try-finally clause for deterministic cleanup might be necessary. Newer Python (since 2.5, I think) also offers the 'with' statement which achieves similar things with a more friendly interface. -- UlrichEckhardt[?](http://c2.com/cgi/wiki?edit=UlrichEckhardt) _What about:_
    
    
     if (! a = allocate_a(...)) goto cleanup;
     if (! b = allocate_b(...)) goto cleanup;
     if (! c = allocate_c(...)) goto cleanup;
     if (! d = allocate_d(...)) goto cleanup;
     do_something_with(a, b, c, d, etc);
     ...
    
    

[Where the remaining code is something like the following, yes?]
    
    
       return;
     cleanup:
       if (a)
          free(a);
       if (b)
          free(b);
       if (c)
          free(c);
       if (d)
          free(d);
    

[CategoryAntiPattern](http://c2.com/cgi/wiki?CategoryAntiPattern) | [CategoryCodeSmell](http://c2.com/cgi/wiki?CategoryCodeSmell) | [CategoryException](http://c2.com/cgi/wiki?CategoryException)
