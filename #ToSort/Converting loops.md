# Converting loops

_Captured: 2016-04-07 at 22:00 from [ericasadun.com](http://ericasadun.com/2016/04/07/converting-loops/)_

Just leaving this here.
    
    
    for var i = 0, j = 1; i < 5; i += 1, j = 1 < i, print("values", i, j) {
        print("2^\(i) is \(j)")
    }

Is basically:
    
    
    for **<variable declarations>**; **<end condition test>**; **<updates>** {
        **<body>**
    }
    

And you can change this to this:
    
    
    do {
        **<variable declarations>**
        while **<end condition test>** {
            **<body>**
            **<updates>**
        }
    }
    

Like this:
    
    
    do {
        var i = 0, j = 1
        while i < 5 {
            print("2^\(i) is \(j)")
            i += 1; j = 1 << i; print("values", i, j)
        }
    }

or this, if you'd like to keep the original bits all together:
    
    
    do {
        **<variable declarations>**
        while **<end condition test>** {
            defer { **<updates>** }
            **<body>**
        }
    }
    

like this:
    
    
    do {
        var i = 0, j = 1
        while i < 5 {
            defer { i += 1; j = 1 << i; print("values", i, j) }
            print("2^\(i) is \(j)")
        }
     }
