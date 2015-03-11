# Gantt-based-Schedule
A schedule displayed as a gantt chart.

## Installation
- Include JQuery & JQuery UI scripts
```html
<script src="js/jquery/jquery-1.4.1.min.js" type="text/javascript"></script>
<script src="js/jquery/jquery-ui.min.js" type="text/javascript"></script>
```
- Include ganttCalendar.js & ganttCalendar.css
```html
<script src="ganttCalendar.js" type="text/javascript"></script>
<link rel="stylesheet" href="ganttCalendar.css" />
```

## How it works
```html
<script type='text/javascript'>
			$(function() {
				// Definition : Event(ressourceId, eventId, startDay, endDay, label, startDate, endDate, color)
				
				var event1 = new Event(1, "event_1", 10, 17, "Free Days", "10/03/2015", "17/03/2015", #453896);
				var event2 = new Event(3, "event_2", 3, 8, "Work", "03/03/2015", "08/03/2015", #754125);
				var event3 = new Event(4, "event_3", 10, 17, "Free Days", "10/04/2015", "17/04/2015", #659542);
				
				var timeline = new TimeLineMonth('myGanttCalendar', ".$month.", ".$year.",
								{groups: 
								[  {name: 'Group1',
									id: 1,
									ressources: [{name:'Group1_Res1', id:1}, {name:'Group1_Res2', id:2}]
									}, {name: 'Group2',
									id: 2,
									ressources: [{name:'Group2_Res1', id:3}, {name:'Group1_Res3', id:4}, {name:'Group1_Res4', id:5}]
									}]
								},
								function(){
									switch(this.year){
										case 2015:
											switch (this.month) {
											  case 03:
											    event1.drawIn(this);
											    event2.drawIn(this);
											  case 04:
											    event3.drawIn(this);
												default:
													break;
											}
											break;
										default:
											break;
									}
								}
				);
				
				timeline.lang = 'en';
				timeline.cellWidth = 40;
				timeline.drawElements();
				timeline.updateMonthCallback();
</script>

<div id='myGanttCalendar'>
</div>
```
