# Code Isn’t Just Functional, It’s Poetic

_Captured: 2015-11-18 at 17:55 from [www.wired.com](http://www.wired.com/2013/04/code/)_

One night in 2011, several engineers were out drinking in a Copenhagen bar. After the second or third beer, one of them boasted that he could recognize the author of a computer program based purely on the writing style. To Ishac Bertran--an interaction designer who's studied Catalan poetry in school -- it sounded like they were discussing literature. "I realized code wasn't so different from any other language," he says. By the end of the evening, he'd proposed that his colleagues try composing poems in code. A genre was born. 

Bertran has since gone global, posting an online call for "code to speak about life or death, love or hate. Code meant to be read, not run" -- though the poems do compile. Hundreds of programmers have submitted poems written in C++, Python, DOS, Ruby, and HTML.

To help him judge the work, he enlisted four "code editors" -- hardcore programmers with literary chops. "Really good coders build entire universes out of ideas," says one of the editors, Jamie Allen, head of research at the Copenhagen Institute of Interaction Design. Consider Kenny Brown, whose poem "Creation?" (below) "plays out a reductionist origin story in Python, a language built on the idea that code should be beautiful, readable, and fun," Allen says. "He creates our solar system with the stroke of an eight-cycle 'for' loop. It evokes how simple rule sets and a few variables can be the start of very big things."
    
    
    Creation?
    
    
    # Creation
    def dstBit(mass,rot,vel):
            bMass=mass
            bRot=rot
            bVel=vel
    
    def dstCld(mass,rot):
            mass=mass
            rot=rot
    
    def Stir(dstBit1,dstBit2):
            CldMass=dstBit1.mass+dstBit2.mass
            CldRot=dstBit1.vel*dstBit2.vel
            return dstCld(CldMass,CldRot)
    
    def Sprk(dstCld):return StellarObject(dstCld.mass)
    
    def Life(planet,seed):return None
    
    dstBit1=dstBit(8.3,5.2,-7.1)
    dstBit2=dstBit(5.3,3.2,5.4)
    
    Cld=Stir(dstBit1,dstBit2)
    Planets=[]
    for i in range(8):
            Planets[i]=Stir(Cld,dstBit1)
    
    Sol=Sprk(Cld)
    
    Life(Planets[2])
    

--Kenny Brown // Python
