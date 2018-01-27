# Python 3: Create Sparklines Using matplotlib

_Captured: 2017-10-12 at 16:55 from [dzone.com](https://dzone.com/articles/python-3-create-sparklines-using-matplotlib?edition=329562&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202017-10-12)_

I recently wanted to create [sparklines](https://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0001OR) to show how some values were changing over time. In addition, I wanted to generate them as images on the server rather than introducing a JavaScript library.

Chris Seymour's [excellent gist](https://github.com/iiSeymour/sparkline-nb/blob/master/sparkline-nb.ipynb), which shows how to create sparklines inside a Pandas DataFrame, got me most of the way there. But I had to tweak his code a bit to get it to play nicely with Python 3.6.

This is what I ended up with:
    
    
    def sparkline(data, figsize=(4, 0.25), **kwags):
    
    
    fig, ax = plt.subplots(1, 1, figsize=figsize, **kwags)
    
    
        for k,v in ax.spines.items():
    
    
    plt.plot(len(data) - 1, data[len(data) - 1], 'r.')
    
    
    ax.fill_between(range(len(data)), data, len(data)*[min(data)], alpha=0.1)
    
    
        plt.savefig(img, transparent=True, bbox_inches='tight')
    
    
    return base64.b64encode(img.read()).decode("UTF-8")

I had to change the class used to write the image from StringIO to BytesIO, and I found I needed to decode the bytes produced if I wanted it to display in an HTML page.

This is how you would call the above function:

And the HTML page looks like this:

![2017 09 23 07 49 32](http://www.markhneedham.com/blog/wp-content/uploads/2017/09/2017-09-23_07-49-32.png)

That was easy!
