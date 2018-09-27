```javascript
document.body.onwheellock =
document.body
.	onwheel = function(e)
	{	on.event.preventDefault.call(e);
		if(app.mg.active)
			return;
		
		app.mg.active = Math.round
		((	app.mg.points.length-1)
		/	app.mg.children.length)
		;
		var velocity = V;
		var directed = [-1,1][+(e.deltaY>0)];
		var selected = app.selected.next(0 - directed);
		var interval = setInterval
		(	function()
			{	for(var j in app.mg.children)
				{	var node=app.mg.children[j];
					if (node.nodeType != 1)
						continue;
					
					node.point += directed * velocity;
					node.draw();
				}
							
				if((app.mg.active-=velocity) <= 0)
				{	clearInterval (interval);
					document.body.setAttribute("animate","true");
				}
			}
		,	5
		);
	}
;
document.body.onwheelfree =
document.body
.	onwheel = function(e)
	{	on.event.preventDefault.call(e);
		app.selected.z = 0;
		var next = 0;
		
		for(var j in app.mg.children)
		{	var node=app.mg.children[j];
				
			if (j != j/1)
				continue;
					
			node.point += Math.round(e.deltaY);
			node.draw();
			
		//	if (app.selected.index == j)
		//		overlay.style.top = node.style.top;
			
			if (app.selected.z < +node.style.zIndex)
			{	app.selected.z = +node.style.zIndex;
				next = j;
			}
		}
		
		if (app.selected.index != next)
			app.selected.set(next);
	}
;
```