# Changing the size of a paging scroll view

_Captured: 2016-02-28 at 00:28 from [khanlou.com](http://khanlou.com/2013/04/changing-the-size-of-a-paging-scroll-view/)_

There aren't really any good names for this effect, but at some point every app developer wants to make it. You can see it in Safari on iOS, when you zoom out to the tab switcher. You can swipe between the pages, and it's clearly a paging scroll view, but it becomes more complicated because of the hints of the next and previous pages.

A paging scrollview's page size is the size of the scrollview's bounds, with no way to adjust it. If you want to show hints of the next and previous "pages", you have to make the scrollview's width the width of the page you'd like and set `clipsToBounds` to `NO`. Then, the scrollview looks the way you expect, but the areas outside the scrollviews bounds are not user-interactable, so your app feels broken. There are pages begging to be touched on the left and right, but the user can't move them.

A lot of the things I blog about are not necessarily about how to do something that's never been done before, but rather better ways to do things we can do already. In other words, there's an old and busted way to do this, and there's the new hotness.

### The old way

The old way, thoroughly documented since 2009 on [Stack Overflow](http://stackoverflow.com/questions/2256081/uiscrollview-with-paging-enabled-can-i-change-the-page-width) and elsewhere, is to:

  1. turn off `clipsToBounds` on your scroll view,
  2. make size of the scroll view the intended size of your pages,
  3. make a custom UIView subclass,
  4. place the view over the area that you'd like to user to be able to touch to begin their scrolling events
  5. override the `- hitTest:withEvent:` function like so
    
         - (UIView *)hitTest:(CGPoint)point withEvent:(UIEvent *)event {  
         if ([self pointInside:point withEvent:event]) {  
             return _scrollView;  
         }  
         return nil;  
     }  
    

### The better way

This all changes in iOS 5.0, when Apple exposed the `panGestureRecognizer` property on `UIScrollView`. Suddenly, our life got a lot easier. Now, all we have to do is:

  1. turn off `clipsToBounds`
  2. put a `UIView` over the scrollview, wherever you want the user to be able to touch
  3. move the `panGestureRecognizer` to that view

[touchableView addGestureRecognizer:_scrollView.panGestureRecognizer];

Done!

This seems like it might be a hack that Apple could break at any time, but it's actually Apple-sanctioned. (cf WWDC Session 223, "Enhancing User Experience with Scroll Views". The second time they gave that talk, they specifically mentioned that `UIScrollView's` `panGestureRecognizer` and `pinchGestureRecognizer` were designed with the expectation that they could be moved.)

This seems like it is a pretty trivial new technique, but as we'll see in [the next blog post](http://khanlou.com/2013/04/paging-a-overflowing-collection-view/), it's actually crucial for use with more modern technologies.
