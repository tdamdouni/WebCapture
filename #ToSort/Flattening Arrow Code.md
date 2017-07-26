# Flattening Arrow Code

_Captured: 2015-12-13 at 15:48 from [blog.codinghorror.com](http://blog.codinghorror.com/flattening-arrow-code/)_

I often encounter code like this:
    
    
    if (rowCount > rowIdx)  
        {
          if (drc[rowIdx].Table.Columns.Contains("avalId"))
          {
            do
            {
              if (Attributes[attrVal.AttributeClassId] == null)
              {
                // do stuff
              }
              else
              {
                if (!(Attributes[attrVal.AttributeClassId] is ArrayList))
                {
                  // do stuff
                }
                else
                {
                  if (!isChecking)
                  {
                    // do stuff
                  }
                  else
                  {
                    // do stuff
                  }
                }
              }
              rowIdx++;
            }
            while (rowIdx < rowCount && GetIdAsInt32(drc[rowIdx]) == Id);
          }
          else
            rowIdx++;
        }
        return rowIdx;
      }  

The excessive nesting of conditional clauses pushes the code out into an arrow formation:
    
    
    if
      if
        if
          if
            do something
          endif
        endif
      endif
    endif
    

  
  


And you know you're definitely in trouble when **the code you're reading is regularly exceeding the right margin on a typical 1280x1024 display**. This is the [Arrow Anti-Pattern](http://c2.com/cgi/wiki?ArrowAntiPattern) in action.

One of my primary refactoring tasks is "flattening" arrow code like this. Those sharp, pointy barbs are dangerous! Arrow code has a high [cyclomatic complexity](http://www.sei.cmu.edu/str/descriptions/cyclomatic_body.html) value - a measure of how many distinct paths there are through code:

> **Studies show a correlation between a program's cyclomatic complexity and its error frequency**. A low cyclomatic complexity contributes to a program's understandability and indicates it is amenable to modification at lower risk than a more complex program. A module's cyclomatic complexity is also a strong indicator of its testability.

Where appropriate, I flatten that arrow code by doing the following:

  1. **Replace conditions with guard clauses.** This code.. 
    
        if (SomeNecessaryCondition)
    {
      // function body code
    }
    

.. works better as a guard clause: 
    
        if (!SomeNecessaryCondition)
    {
      throw new RequiredConditionMissingException;
    }
    // function body code
    

  2. **Decompose conditional blocks into seperate functions.** In the above example, we're in a do..while loop which could be decomposed: 
    
        do
    {
      ValidateRowAttribute(drc[rowIdx]);
      rowIdx++;
    }
    while(rowIdx < rowCount && GetIdAsInt32(drc[rowIdx]) == Id);
    

  3. **Convert negative checks into positive checks.** As a broad rule, I prefer to put the positive comparison first and let the negative comparison fall out naturally into the else clause. I think this reads a lot better and, more importantly, avoids the "I ain't not never doing that" syndrome: 
    
        if (Attributes[attrVal.AttributeClassId] is ArrayList)
    {
      // do stuff
    }
    else
    {
      // do stuff
    }
    

  4. **Always opportunistically return as soon as possible from the function.** Once your work is done, get the heck out of there! This isn't always possible - you might have resources you need to clean up. But whatever you do, you have to abandon the ill-conceived idea that there should only be one exit point at the bottom of the function.

The goal is to have code that scrolls vertically a lot… but not so much horizontally.
