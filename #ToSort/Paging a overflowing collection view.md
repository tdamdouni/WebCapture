# Paging a overflowing collection view

_Captured: 2016-02-28 at 00:29 from [khanlou.com](http://khanlou.com/2013/04/paging-a-overflowing-collection-view/)_

In [the last post](http://khanlou.com/2013/04/changing-the-size-of-a-paging-scroll-view/), I discussed how to make a paging scroll view with hints on either side. This is a pretty common effect to try to achieve, and it's nice to know that it can be done without too much effort now.

Of course, the natural progression of having many pages of views in a scrollview is to manage them with a `UICollectionView`. This complicates matters for us a lot, however. The collection view knows where all its cells are (no matter what layout you give it), so it automatically removes cells that are outside its visible bounds, the same way a tableview does. This breaks our `clipsToBounds` trick, because as soon as they move outside the bounds, they disappear.

But we are smarter than `UICollectionView`, and we will prevail.

## Technique

Below is the simplest way to get the job done. It involves a collection view and an extra secret scroll view.

### Set up your collection view

  1. Set up your collection view and all its data source methods.
  2. Frame the collection view; it should span the full width that you want to be visible.
  3. Set the collection view's `contentInset` :
    
         _collectionView.contentInset = UIEdgeInsetsMake(0, (self.view.frame.size.width-pageSize)/2, 0, (self.view.frame.size.width-pageSize)/2);  
    

This helps offset the cells properly.

### Set up your secret scrollview

  1. Create a scrollview, place it wherever you like. You can set it to `hidden` if you like. Turn `pagingEnabled` on.
  2. Set the size of the scrollview's bounds to the desired size of your page.
  3. Set yourself as the delegate of the scrollview.
  4. Set its `contentSize` to the expected content size of your collection view.

### Move your gesture recognizer

  1. Add the secret scrollview's gesture recognizer to the collection view, and disable the collection view's gesture recognizer:
    
         _collectionView addGestureRecognizer:_secretScrollView.panGestureRecognizer];  
     _collectionView.panGestureRecognizer.enabled = NO;  
    

### Delegate
    
    
    - (void) scrollViewDidScroll:(UIScrollView *)scrollView {  
    	if (scrollView == _secretScrollView) { //ignore collection view scrolling callbacks  
    		CGPoint contentOffset = scrollView.contentOffset;  
    		contentOffset.x = contentOffset.x - _collectionView.contentInset.left;  
    		_collectionView.contentOffset = contentOffset;  
    	}  
    }
    

As the scrollview moves, get its offset and set it to the offset of the collection view.

And you're done! It's a little less elegant than the previous solution, but this is the price we pay to get to use `UICollectionView`.

For extra credit: create a new `UICollectionLayout` subclass that overlaps the cells slightly and invisibly so that the collection view can't remove those cells. (ed. I think this is impossible.)
