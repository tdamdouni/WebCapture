# Getting the parent of a dynamically method as a function
__

This topic has been deleted. Only users with topic management privileges can see it.

  * [ ![](/uploads/profile/232-profileimg.png) ](/user/phuket2)

__ ** [Phuket2](/user/phuket2) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


Sorry, this is more likely a Python question than it is a Pythonista question. But I have searched else where and can not find the answer. It also could be particular to Pythonista, not sure.

What I would like to do is , add a function to a ui Element such as a ui.Button. Then from inside that function at runtime determine the calling classes instance. so self for short.

In the sample code below, I know, I could pass the instance object as a param. Just not ideal....  
I think the answer must be in the inspect module. I have tried with stack(), current(), outerframes(), I just can't seem to figure it out.  
If you do have a solution to share that would be great, but could you please also comment on how robust you think the solution is.
    
        import ui
    
    def test_func(msg):
        '''
        i would like to get a reference to the caller here
        being the btn. 
        i am pretty sure the answer lies with the inspect module,
        but i cant figure it out.
        MAYBE, its even easier than that... well that would be great
        '''
        print msg
        
    
    btn = ui.Button()
    btn.msg = test_func
    btn.msg('I am on to something...')
    
    

last edited by ****

* * *

  * [ parent 1](/tags/parent) [ attr 1](/tags/attr) [ dynamically 1](/tags/dynamically)

Loading More Posts __

49  
Posts

1314  
Views

Reply [Log in to reply](/login)

* * *

  * [ ![](/uploads/profile/232-profileimg.png) ](/user/phuket2)

__ ** [Phuket2](/user/phuket2) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


[@mikael](https://forum.omz-software.com/user/mikael) , but again for the idea to be relevant it has to compete with something like this. Looks like more code then we have been doing. But when you look at the one off code it's not.  
Just saying that's how I am trying to evaluate if it's worth while or not
    
        # coding: utf-8
    
    import ui
    
    def MyMother(sender):
        print 'I love my Mums cooking'
        
    _default_btn_style = \
        {
            'border_width' : .5,
            'corner_radius' : 3,
            'bg_color' : 'teal',
            'tint_color' : 'white',
            'action'  : MyMother,
        }
    
    _btn_style = _default_btn_style
    
    _extra_attrs = \
        {
            'myx' : 0,
            'myy' : 0,
        }
        
    
    def make_button(style = _btn_style, ext_attrs = _extra_attrs ,
                            *args, **kwargs):
        btn = ui.Button()
        
        # process the normal atttrs
        for k,v in kwargs.iteritems():
            if hasattr(btn, k):
                setattr(btn, k, v)
        
        # process a style dict
        for k,v in style.iteritems():
            if hasattr(btn, k):
                setattr(btn, k, v)
        
        # process addtional attrs...
        for k,v in ext_attrs.iteritems():
            setattr(btn, k, v)
    
        # if kwargs has a parent key, then we add the subview to the parent
        if kwargs.has_key('parent'):
            kwargs['parent'].add_subview(btn)
            
        btn.size_to_fit()
        # size to fit is too tight
        btn.frame = ui.Rect(*btn.bounds).inset(0, -5)
            
        return btn
            
    if __name__ == '__main__':
        f = (0,0,500,500)
        v = ui.View(frame = f)
        btn = make_button(title = 'What do I Like', parent = v)
        v.present('sheet')
    

last edited by ****

* * *

  * [ ![](/uploads/profile/746-profileimg.png) ](/user/tutorialdoctor)

__ ** [TutorialDoctor](/user/tutorialdoctor) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


I know this is an older post, but I am wondering why no one recommended using a button action?
    
        def test_func(sender):
        return sender
    
    v = ui.load_view()
    button = v['button1']
    button.action = test_func
    

Then the only question would be how to pass parameters to a button's action function.  
"sender" is the button that called the function.

last edited by ****

* * *

  * [ ![](https://s.gravatar.com/avatar/21d71ac20be1f1bad4e07cd4c4659f9c?size=128&default=identicon&rating=pg) ](/user/mikael)

__ ** [mikael](/user/mikael) **

posted  __ Reply Quote

__ 1

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


[@TutorialDoctor](https://forum.omz-software.com/user/tutorialdoctor), we are not focused on the button, but on reasonably elegant ways to get around the fact that we can not subclass ui components. Button is just being used as a shared sample, so to say.

last edited by ****

* * *

  * [ ![](https://s.gravatar.com/avatar/21d71ac20be1f1bad4e07cd4c4659f9c?size=128&default=identicon&rating=pg) ](/user/mikael)

__ ** [mikael](/user/mikael) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


[@Phuket2](https://forum.omz-software.com/user/phuket2), to exaggerate a bit, it looks like where I have been working towards the most object-oriented, legible and maintainable way to create custom components, emphasizing maybe a low number of complex components, you might have been working on the most flexible and time-saving functional-programming button maker, with a possible further focus on generating relatively many less-complex components easily.

Pretty opposite ends of the spectrum, one could say, but nevertheless this has been very instructive and interesting, and I have learned a lot about Python meta-programming in the process. Thanks!

Out of curiosity, I will try and see what a roughly similar generator would look like in "my style".

last edited by ****

* * *

  * [ ![](/uploads/profile/232-profileimg.png) ](/user/phuket2)

__ ** [Phuket2](/user/phuket2) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


[@mikael](https://forum.omz-software.com/user/mikael) , also thanks. I have also enjoyed it and learnt a lot. For me it's about remembering what I have learnt 😳

But I think I am starting to learn something that seems so obvious, but not really. We I guess depending on your experience. But that is to really get clear what you are trying to improve on. I can see I go off on all sort of tangents trying to solve problems that either don't exists, I just keep working on something without looking back and comparing the methods, basically having a bench mark.

I still have some years left in me to learn 😁 So all good.

last edited by ****

* * *

  * [ ![](/uploads/profile/232-profileimg.png) ](/user/phuket2)

__ ** [Phuket2](/user/phuket2) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


[@TutorialDoctor](https://forum.omz-software.com/user/tutorialdoctor) , yes this thread has been around the would and back.

last edited by ****

* * *

  * [ ![](https://s.gravatar.com/avatar/21d71ac20be1f1bad4e07cd4c4659f9c?size=128&default=identicon&rating=pg) ](/user/mikael)

__ ** [mikael](/user/mikael) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


[@Phuket2](https://forum.omz-software.com/user/phuket2), here's the latest. I went a bit further with the meta stuff and created an Extender base class for functionality wrappers.
    
        import types
    
    class Extender(object):
        def __new__(cls, target_instance, *args, **kwargs):
            if isinstance(cls.__init__, types.MethodType):
                cls.__init__.__func__(target_instance, *args, **kwargs)
            extender_instance = super(Extender, cls).__new__(cls)
            for key in dir(extender_instance):
                if key.startswith('__'): continue
                value = getattr(extender_instance, key)
                if callable(value):
                    setattr(target_instance, key, types.MethodType(value.__func__, target_instance))
                else:
                    setattr(target_instance, key, value)
            return target_instance

last edited by ****

* * *

  * [ ![](https://s.gravatar.com/avatar/21d71ac20be1f1bad4e07cd4c4659f9c?size=128&default=identicon&rating=pg) ](/user/mikael)

__ ** [mikael](/user/mikael) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


Using the Extender base, an attempt at apples-to-apples comparison code, matching the code you shared. ButtonFactory is perhaps not exactly how I would create it in isolation, but it acts as a useful test case for passing arguments through the custom **new**.
    
        # coding: utf-8
    import ui
    from extend import Extender
    
    def MyMother(sender):
        print 'I love my Mums cooking'
    
    class DefaultStyle(Extender):
        border_width = .5
        corner_radius = 3
        background_color = 'teal'
        tint_color = 'white'
        
    class ButtonFactory(Extender):  
        def __init__(self, parent = None, position = (0,0), **kwargs):
            if parent: parent.add_subview(self)
            self.size_to_fit()
            (self.x, self.y) = position
            self.width += 10
            self.action = MyMother
            for key, value in kwargs.iteritems():
                setattr(self, key, value)
            
            
    view = ui.View(frame = (0,0,500,500))
            
    button = ButtonFactory(
        DefaultStyle(
            ui.Button(title = 'What do I like?')),
        parent = view, tint_color = 'yellow')
    
    view.present('sheet')

last edited by ****

* * *

  * [ ![](https://s.gravatar.com/avatar/21d71ac20be1f1bad4e07cd4c4659f9c?size=128&default=identicon&rating=pg) ](/user/mikael)

__ ** [mikael](/user/mikael) **

posted  __ Reply Quote

__ 0

__
    * Favorite 0  __ __
    *     * Flag this post for moderation 

  


This version of the extension functionality now meets mostnof my design goals:

    * Use standard class syntax for encapsulating data and functionality - in my case, much preferred to the dict syntax
    * Can extend ui component functionality, "almost subclassing"
    * `self` always refers to the instance being extended, also in `__init__`
    * Constructor returns the instance being extended instead of the extender, which allows for chaining extenders
    * Since the original UI class instance is returned, can be used in `add_subclass` and `ObjCInstance`

These are still a fail:

    * Extra `__func__` is needed when calling overloaded methods from superclass, most often done in `__init__`:

`SuperClass.__init__.__func__(self, params)`

last edited by **mikael**

* * *


