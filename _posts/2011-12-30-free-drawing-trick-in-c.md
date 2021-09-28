---
id: 16
title: 'Free Drawing trick in C#'
date: 2011-12-30T19:33:25+00:00
author: alaa
layout: article
guid: 16
publicize_results:
  - 'a:1:{s:7:"twitter";a:1:{i:248646703;a:2:{s:7:"user_id";s:9:"AlaaAttya";s:7:"post_id";s:18:"152834711679537153";}}}'
categories:
  - 'C#'
tags:
  - move event
  - 'c#'
key: free-drawing-trick-16    
---
While studying C# ,one of my friends had an idea to write  a C# program that enables user to make a free drawing shapes using C# graphics

so i have open my compiler ,have a moment of silence and started to code

My idea was to get the point when the user first clicked on the form,then while he is holding down the mouse button & moving i have to get the distance between the first position the mouse was clicked & the current position (width& height argument).

Lest&#8217;s start coding,

to get the first moue click position here we got two data members to store the first position,also w have a boolean data member to know if the mouse is still down or not

```c#
bool paintThis = false;  
int x;  
int y;
```

then in the mouse down event we get these two guys x&y of the first position and set the paintThis to true

```c#
private void Form1_MouseDown(object sender, MouseEventArgs e)  
{  
	paintThis = true;  
	x = e.X;  
	y = e.Y;
}
```

then in the mouse up event we set the paintThis to false

```c#
private void Form1_MouseUp(object sender, MouseEventArgs e)  
{  
	paintThis = false;  
}
```

here in the mouse move event all the work will be done,we&#8217;ll calculate the width & the height of the rectangle we want to draw and start drawing when the mouse is down(actually when `paintThis=true`) at the first position the mouse was down (x & y)

```c#
private void Form1_MouseMove(object sender, MouseEventArgs e)  
{  
	if (paintThis)  
	{  
		Refresh();  
		Graphics gf = this.CreateGraphics();  
		gf.DrawRectangle(new Pen(Color.Black), x,y, e.X-x, e.Y-y);  
	}  
}
```

[here the source files](http://www.mediafire.com/?mbr69mixi76vimh)

hope you have enjoyed
