# traffic light program in c, traffic light simulation

_Captured: 2015-12-04 at 01:53 from [www.programmingsimplified.com](http://www.programmingsimplified.com/c-traffic-light-program)_

Traffic light Simulation: Traffic light program in c presents what happens in our daily life at traffic light signals. Firstly user will press a key to start the traffic light simulation.

## C programming code
    
    
    #include<graphics.h>
    #include<conio.h>
    #include<dos.h>
    #include<stdlib.h>
     
    main()
    {
       int gd = DETECT, gm, midx, midy;
     
       initgraph(&gd, &gm, "C:\\TC\\BGI");
     
       midx = getmaxx()/2;
       midy = getmaxy()/2;
     
       setcolor(RED);
       settextstyle(SCRIPT_FONT, HORIZ_DIR, 3);
       settextjustify(CENTER_TEXT, CENTER_TEXT);
       outtextxy(midx, midy-10, "Traffic Light Simulation");
       outtextxy(midx, midy+10, "Press any key to start");
       getch();
       cleardevice();
       setcolor(WHITE);
       settextstyle(DEFAULT_FONT, HORIZ_DIR, 1);
       rectangle(midx-30,midy-80,midx+30,midy+80);
       circle(midx, midy-50, 22);
       setfillstyle(SOLID_FILL,RED);
       floodfill(midx, midy-50,WHITE);
       setcolor(BLUE);
       outtextxy(midx,midy-50,"STOP");
       delay(2000);
       graphdefaults();
       cleardevice();
       setcolor(WHITE);
       rectangle(midx-30,midy-80,midx+30,midy+80);
       circle(midx, midy, 20);
       setfillstyle(SOLID_FILL,YELLOW);
       floodfill(midx, midy,WHITE);
       setcolor(BLUE);
       outtextxy(midx-18,midy-3,"READY");
     
       delay(2000);
       cleardevice();
       setcolor(WHITE);
       rectangle(midx-30,midy-80,midx+30,midy+80);
       circle(midx, midy+50, 22);
       setfillstyle(SOLID_FILL,GREEN);
       floodfill(midx, midy+50,WHITE);
       setcolor(BLUE);
       outtextxy(midx-7,midy+48,"GO");
       setcolor(RED);
       settextstyle(SCRIPT_FONT, HORIZ_DIR, 4);
       outtextxy(midx-150, midy+100, "Press any key to exit...");
     
       getch();
       closegraph();
       return 0;
    }

Download [Traffic Light Simulation](http://www.programmingsimplified.com/toolsArea/executable/Traffic%20Light%20Simulation.EXE).
