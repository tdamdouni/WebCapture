# How Does Stencil Fit Into the Whole Micro Frontends Idea?

_Captured: 2017-12-05 at 13:48 from [dzone.com](https://dzone.com/articles/how-does-stencil-fit-into-the-whole-micro-frontend?edition=343093&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-04)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

In a post I published a few days ago I explained [why I'm betting on Web Components](https://dzone.com/articles/why-im-betting-on-web-components). In the post, I suggested you use Web Components as an infrastructure to create your Micro Frontends. It's no secret that in the last month or so I have invested a lot of time trying to understand how to use the [Stencil](http://stenciljs.com/) compiler and I even published a [few posts](https://medium.com/@gilfink/getting-started-with-stencil-7e331962a9f1) about it.

In this post, I want to shortly explain how Stencil can help you avoid the "Framework Catholic Wedding" and fit into Micro Frontends idea.

_Note: These are my own thoughts and they are definitely not the only solution out there._

In the post 'Why I'm betting on Web Components,' I suggested that one of the options to build your Micro Frontends is to use [Custom Elements API](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Custom_Elements). [Custom Elements API](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Custom_Elements) can help you build shared components infrastructure. Then, you can share those components across your company development teams. Those components should be agnostic of any framework or library and can be used by any framework or library. Making the components agnostic will help you avoid framework runtime coupling in your infrastructure.

How does Stencil fit into the picture? In a very straightforward way.

![](https://cdn-images-1.medium.com/max/800/1*ILz94Idx2CIX6SxJn7P_aA.png)

> _Stencil in a Micro Frontends Environment_

Stencil is a build-time tool that generates Custom Elements. The output of Stencil is 100% standards-compliant Custom Elements. It also includes a lot of nice and relevant features such as a virtual DOM, async rendering, and reactive data-binding. The features will help you to create performant and robust standalone components. Also, the features cost has a very small footprint -- currently around 6 kilobytes for a component collection. Once you created your component collection you can add it to npm, use it in a standalone script, or use it from a CDN like any other component collection.

If you aren't convinced yet, I suggest you play with [Stencil](http://stenciljs.com/) for a couple of hours or even to do a small proof of concept. Once you do that, you will be sure if you want to use Stencil in the future or not.

## Summary

Stencil generates custom elements with a small runtime footprint. This makes the Stencil compiler very suitable for building infrastructure components that align with the concept of Micro Frontends. This is the road that the Ionic Framework team took!

There are other solutions to create your Custom Elements such as [Angular Elements](https://github.com/robwormald/angular-elements), [SkateJS](https://github.com/skatejs/skatejs), and [SlimJS](http://slimjs.com/). All those solutions are cool, but I've chosen to use Stencil because, in the end, it's a Custom Elements compiler and not a library. In my opinion, the design-time environment is definitely a good edge on top of the other solutions. Will it be successful in the days to come? We will have to wait and see.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
