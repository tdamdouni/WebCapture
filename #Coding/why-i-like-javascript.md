# Why I Like JavaScript

_Captured: 2018-01-18 at 15:16 from [dzone.com](https://dzone.com/articles/why-i-like-javascript?edition=355097&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-01-18)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Every programming language has its oddities and challenges. When it comes to JavaScript, it has probably more of those oddities. It's not the just language itself but also browser support. Different vendors implemented slightly different JavaScript engines for years. It resulted in a ton of challenges. I dealt with these challenges [myself](https://github.com/yusufaytas/upjs). Thanks to jQuery, we had a breath of fresh air. Anyway, this isn't the end of the story. Over the years, JavaScript improved a lot, really. In this post, I'll go over JavaScript weirdnesses first and then try to explain why I like JavaScript.

### The Weird Parts

I will go directly to the code as it's better to demonstrate than talk.
    
    
    typeof f1() === typeof f2(); //false

We can probably find more of these peculiarities, but I'll keep it short. Let's focus on the new syntax.

### The Good Parts

ES6 is a significant update to the language. It introduced a powerful syntax. I have been using JavaScript for quite some time but I like it more every time I get to use it. So, I'll go over my favorite features.

#### The Default Parameters

I've first used default parameters in Python, and it was charming. In JavaScript, however, it simplifies the code by removing extra logic to cover null cases.

#### The Arrow Functions

I guess it's not just me. Everbody loves arrows, it simplifies logic for filtering and mapping a lot. Note that we have some brand new functionalities, like `some` and `every`. They are wonderful. You simply write less.
    
    
    [1, 2, 3].map(i => i + 1).reduce((s, i) => s + i)
    
    
    [1, 2, 3].filter(i => i % 2 == 0).sort()
    
    
    [1, 2, 3].some(i => i % 2 == 0)
    
    
    [1, 2, 3].every(i => i % 2 == 0)

#### The Template Strings

The template string is just a better way of constructing strings. It removes the challenges inherent in formatting strings. It can also evaluate the logic inside, although it might not be a very good idea to do so.
    
    
    let name='Gulnihal', postId=3, commentId=5
    
    
    console.log(`Hello ${name}`)
    
    
    let url = `http://www.yusufaytas.com/posts/${postId}/comments/${commentId}`

#### Destructuring Assignment

This is truly magical. You can destruct objects and arrays. You can just get the property you are looking for easily.

I've gone through my favorites with the new JavaScript features. There are other great features like Promises, Classes, and additional object methods. However, the above features changed my daily coding significantly because I'm writing less code in a much more expressive way.

JavaScript has been the bad guy for a while but it gas significantly improved. One can simply accept the weird parts and avoid them.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
