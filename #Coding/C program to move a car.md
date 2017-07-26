# C program to move a car

_Captured: 2015-12-04 at 01:52 from [www.programmingsimplified.com](http://www.programmingsimplified.com/c/program/moving-car)_

Program in c using graphics move a car. A car is made using two rectangles and two circles which act as tyres of car. A for loop is used to move the car forward by changing the rectangle and circle coordinates and erasing the previous contents on screen using clearviewport, you can also use cleardevice. Speed of car can be adjusted using delay function, more the delay lesser will be the speed or lesser the delay your car will move fast. In this program color of the car also keeps on changing, this is accomplished by incrementing the color value by one each time in for loop, you can also use random function for this purpose. Before you see a car moving you will be asked to press a key.

## C programming code
    
    
    #include <graphics.h>
    #include <dos.h>
    #include <conio.h> 
     
    main()
    {
       int i, j = 0, gd = DETECT, gm;
     
       initgraph(&gd,&gm,"C:\\TC\\BGI");
     
       settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
       outtextxy(25,240,"Press any key to view the moving car");
     
       getch();
       setviewport(0,0,639,440,1);
     
       for( i = 0 ; i <= 420 ; i = i + 10, j++ )
       {
          rectangle(50+i,275,150+i,400);
          rectangle(150+i,350,200+i,400);
          circle(75+i,410,10);
          circle(175+i,410,10);
          setcolor(j);
          delay(100);
     
          if( i == 420 )
             break;
     
          clearviewport();
       }
     
       getch();
       closegraph();
       return 0;
    }
