# Scripts to set priority, and sort a project by priority

_Captured: 2016-11-11 at 00:59 from [support.hogbaysoftware.com](http://support.hogbaysoftware.com/t/scripts-to-set-priority-and-sort-a-project-by-priority/2279)_

My goal was to have projects in TaskPaper that had a priority tag and then to have a script that sorted the list by the priority.  
Requirements:  
* Set the priority tag based on the Pareto Principle found [here16](http://lifehacker.com/5914877/stop-wasting-time-by-applying-the-pareto-principle-to-your-task-list)  
** The @priority tag is composed of two values, an effort, and a result.   
** Effort is a number, 1-3, indicating the effort required to accomplish a task (higher = more effort)  
** Result is a number, 1-3, indicating the resulting benefit (higher = more benefit)  
** Priority is then set as @priority(effort/result) so that priority value = higher priority task (this is intuitive to me)  
* Sort all the tasks in each project according to priority

Solution:  
I wrote two scripts to do this.  
1\. The first one pops up a small dialog asking for a number for effort, and the second one for result. The script then inserts a @priority(effort/result) tag. I then attach this script to a hotkey in Alfred 3.  
2\. The second script sorts each project (including nested projects) by priority.

These were my first scripts so they are likely poorly written. But they are well documented and perfect for newbie consumption since I had no clue what I was doing and so make them as easy to read and digest as possible. Please enjoy. And if anyone has improvements PLEASE do share!!

As a sidenote, I've written a couple of Alfred 3 workflows to quickly add tasks to the "inbox" of my taskpaper files and could share if anyone is interested.

Script to set priority:
    
    
    (function () {
    // JavaScript for the Automation context
    var min = 1;
    var max = 4;
    var default_val = 2;
    
    // get the application TaskPaper
    TP = Application("TaskPaper");
    // get the standard additions which allow dialogs and other interactions with the system
    // if you don't want TP to be the focused app, use Application.currentApplication() and set
    // the standard additions to true in that app.
    TP.includeStandardAdditions = true;
    // note that JXA syntax is just weird, requiring the first parameter like normal, and
    // subsequent parameters to be in curly braces with the name of the parameter a colon, then the variable, then a comma. Seems silly to me.
    // get the effort required
    var effort = TP.displayDialog('Set Effort...('+min+'-'+max+')',{
    	withTitle: 'Set Effort for Task',
    	defaultAnswer: default_val,
    	buttons: ['OK','Cancel'],
    	defaultButton: 'OK',
    	cancelButton: 'Cancel'
    	});
    // convert to a number
    effort = Number(effort.textReturned);
    // check to see if input was valid
    if(effort < min || effort > max) {
    	return;
    }
    
    // get the result
    var result = TP.displayDialog('Set Result...('+min+'-'+max+')',{
    	withTitle: 'Set Result for Task',
    	defaultAnswer: default_val,
    	buttons: ['OK','Cancel'],
    	defaultButton: 'OK',
    	cancelButton: 'Cancel'
    	});
    // convert to a number
    result = Number(result.textReturned);
    if(result < min || result > max) {
    	return;
    }
    // calculate the priority
    var priority = (effort/result).toFixed(1);
    
    
    function TaskPaperContextScript(editor, options) {
    
    	// get the priority
    	var priority = options;
    
    	// sets the attribute
    	function setAttribute(editor, items, name, value) {
    	    var outline = editor.outline;
        	var selection = editor.selection;
    	    outline.groupUndoAndChanges(function() {
        		items.forEach(function (each) {
    		        each.setAttribute(name, value);
    			});
    		});
    		editor.moveSelectionToItems(selection);
    	}
    	// pass to setAttribute the editor, the selectedItems
    	setAttribute(editor, editor.selection.selectedItems, 'data-priority', priority);
    }
    
    // call the JavaScript
    Application("TaskPaper").documents[0].evaluate({
      script: TaskPaperContextScript.toString(),
      withOptions: priority
    })
    })();

Sorting Script:
    
    
    function TaskPaperContextScript(editor, options) {
    	var outline = editor.outline;
    	// group all the changes together into a single change and make it a single "undo" action
    	outline.groupUndoAndChanges(function () {
    		// all the projects
    		var projects_array = outline.evaluateItemPath('@type=project except archive:');
    		// for each project get the tasks with priority
    		projects_array.forEach(function(each) {
    			var has_children = each.hasChildren;
    			if(!has_children) {
    				return;
    			}
    			var children = each.children; 
    
    			// handle the case of only one item in a project
    			if(children.length < 2) {
    				return;
    			}
    
    			children.sort(function (a, b) {
    				// a and b are elements of the array
    				// get the priority value of task a, "getAttribute" takes the attribute name,
    				// and whether or not the value should be converted to something else (in
    				// this case a number)
    				//debugger;
    				var a_priority = a.getAttribute('data-priority', Number);
    				var b_priority = b.getAttribute('data-priority', Number);
    				//var a_has_done = a.hasAttribute('data-done');
    				//var b_has_done = b.hasAttribute('data-done');
    
    				// need to return negative, zero, or positive
    				// negative indicates a < b
    				// zero indicates a = b
    				// positive indicates a > b
    				
    				// Here null means the item didn't have a priority tag
    				// In this case b < a
    				if(a_priority == null && b_priority != null) {
    					return 1 ;
    				} // In this case a < b
    				else if (a_priority != null && b_priority == null) {
    					return -1;
    				} // In thise case a = b
    				else if (a_priority == null && b_priority == null) {
    					return 0;
    				} // In thise return a relative to b
    				else {
    					return a_priority - b_priority;
    				}
    			});	// end sort	
    			each.removeChildren(each.children);
    			each.appendChildren(children);
    		}); // end projects_array.forEach 
    	}); // end outline.groupUndoAndChanges
    } // end TaskPaperContextScript
    
    var string = Application("TaskPaper").documents[0].evaluate({
      script: TaskPaperContextScript.toString()
    });
