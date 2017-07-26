# Sorting Tables with CSS & jQuery

_Captured: 2015-12-11 at 16:18 from [www.granneman.com](http://www.granneman.com/webdev/coding/css/sorting-tables/)_

On this page…

Tables can be incredibly useful when they are used to display data, but what can be even more useful is the ability to sort the data in the table by columns. On this page we're going to learn how to sort tables by simply clicking on the column headers. Click once to sort ascending (A-Z) and a second time to sort descending (Z-A).

To perform this magic, we're going to use [tablesorter.js](http://tablesorter.com/docs/), which builds off of jQuery. It's really not hard to do, and the effect is really neat. Best of all, it works in a lot of now pretty old browsers, including:

  * Firefox 2+
  * Internet Explorer 6+
  * Safari 2+
  * Opera 9+
  * Konqueror

## Download the necessary files[ ↩](http://www.granneman.com/webdev/coding/css/sorting-tables/)

Download tablesorter by going to <http://tablesorter.com/docs/#Download> and clicking on the full release. Unzip it.

## Create the necessary directory structure[ ↩](http://www.granneman.com/webdev/coding/css/sorting-tables/)

Create folders like this:

  * `projectname` [change this to the name of your project/client] 
    * `css`
    * `js`

## HTML[ ↩](http://www.granneman.com/webdev/coding/css/sorting-tables/)

Create a standard HTML 5 webpage inside the `projectname` folder. For the content, create some paragraphs with [Lorem Ipsum](http://www.granneman.com/webdev/coding/greeking/) or use the content on my [HTML & CSS Test Page](http://www.granneman.com/webdev/coding/htmlcsstestpage/).

Somewhere on the page, place the following table:
    
    
    <table class="tablesorter ws_data_table">
    <thead>
      <tr>
        <th>Congregation</th>
        <th>City</th>
        <th>County</th>
        <th>Web</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>All Saints' Episcopal Church</td>
        <td>St. Louis</td>
        <td>St. Louis City</td>
        <td><a href="http://allsaintsstl.org/">Web</a></td>
      </tr>
      <tr>
        <td>All Saints' Episcopal Church</td>
        <td>Farmington</td>
        <td>St. Francois</td>
        <td><a href="http://diocesemo.org">Web</a></td>
      </tr>
      <tr>
        <td>St. John’s</td>
        <td>St. Louis</td>
        <td>St. Louis</td>
        <td><a href="http://towergrovechurch.org">Web</a></td>
      </tr>
    </tbody>
    </table>
    

Go ahead & look at your webpage so far. Note that you cannot sort the table at all.

Our ultimate goal is to enable users to click on--& sort--columns 1-3:

  * Congregation
  * City
  * County

We do not want column 4 to be sortable:

  * Web

## CSS[ ↩](http://www.granneman.com/webdev/coding/css/sorting-tables/)

First let's take care of the CSS to make the table look nice.
    
    
    /* @group Data Tables */
    
    .ws_data_table {
      border-collapse: collapse;
      border-color: #537DB9;
      border-width: 1px;
      border-style: solid;
      margin-bottom: 15px;
    }
    
    .ws_data_table caption {
      text-align: left;
      font-weight: bold;
      margin-top: 10px;
    }
    
    .ws_data_table th {
      text-transform: inherit;
      white-space: nowrap;
      background-color: #3366CC;
      color: #FFFFFF;
      padding: 2px 10px 2px 10px;
      border-right: #FFFFFF;
      border-width: 1px;
      border-style: none dotted none none;
    }
    
    .ws_data_table td {
      padding: 5px 10px 5px 10px;
      border-right: #cccccc;
      border-width: 1px;
      border-style: none dotted none none;
      vertical-align: top;
    }
    
    .ws_data_table tr:nth-child(odd) {
      background-color: #FFFFFF;
    }
    
    .ws_data_table tr:nth-child(even) {
      background-color: #E6E6E6;
    }
    
    /* @end */
    

Now let's add the CSS specific to the `tablesorter` JavaScript. Note that at this point nothing will appear, as the JavaScript will dynamically insert the classes into the HTML.
    
    
    /* @group tablesorter */
    
    .header {
      cursor: pointer;
    }
    
    .headerSortDown:after {
      content: " ▾";
      font-family: Arial, sans-serif;
    }
    
    .headerSortUp:after {
      content: " ▴";
      font-family: Arial, sans-serif;
    }
    
    /* @end */
    

To get the second tier to appear, we use JavaScript, specifically jQuery.

For information on integrating jQuery, follow the instructions at [Adding jQuery to Your Projects](http://www.granneman.com/index.php?cID=775).

Go back to the files you downloaded. Find `jquery.tablesorter.min.js` & move it into the `js` folder.

In your `<head>`, add a link to the `tablesorter.js` file:
    
    
    <script src="js/jquery.tablesorter.min.js"></script>
    

In the `<body>` but before the `<table>`, add the following `<script>`[1](http://www.granneman.com/webdev/coding/css/sorting-tables/):
    
    
    <script>
      $(document).ready(function()
        {
          $("table").tablesorter({
            sortList: [[0,0]],
            headers: {3:{sorter:false}}
          });
        }
      );
    </script>
    

> **SIDENOTE**: Note that this line is what tells `tablesorter.js` to skip column 4: `headers: {3:{sorter:false}}`. "But wait," you're asking, "we're excluding column 4. So why does our code reference `3`?" Because JavaScript counts from 0 instead of 1, which means that column 4 is identified by `3`.

Save everything, reload the webpage, & you should now be able to click on columns to sort!

## More than one table on a page[ ↩](http://www.granneman.com/webdev/coding/css/sorting-tables/)

Take a look again at this line in the JavaScript: `$("table").tablesorter({`. It means that every `<table>` with a class of `tablesorter` on the page will be sorted the same way. But what if instead you had more than one table on a page, & you wanted to sort the data in those tables but ignore different columns in the tables? To do that, you would need to assign each table an `id` and create a new script block referencing that `id` for each table.

So let's say you have two tables on a webpage:

  * The first table is about personnel & you want to ignore the 4th column for sorting
  * The second is about services & you want to ignore the 2nd column for sorting

### Table 1: Personnel[ ↩](http://www.granneman.com/webdev/coding/css/sorting-tables/)

The first table would start like this:
    
    
    <table id="personnel" class="tablesorter ws_data_table">
    

Just before that table, you'd put this script:
    
    
    <script>
      $(document).ready(function()
        {
          $("#personnel").tablesorter({
            sortList: [[0,0]],
            headers: {3:{sorter:false}}
          });
        }
      );
    </script>
    

Note two things about this particular JavaScript:

  * You reference the `id` of `personnel` assigned to the table: `$("#personnel").tablesorter`
  * You specify the column you don't want to sort: `headers: {3:{sorter:false}}`

Now let's do the second table on the page. First the HTML for the table, which should start like this;
    
    
    <table id="services" class="tablesorter ws_data_table">
    

Just before that second table, you'd put this script:
    
    
    <script>
      $(document).ready(function()
        {
          $("#services").tablesorter({
            sortList: [[0,0]],
            headers: {1:{sorter:false}}
          });
        }
      );
    </script>
    

> Note that we don't want column 2 to be sortable, so we use this: `headers: {1:{sorter:false}}`. Remember earlier, when I said that JavaScript starts counting at 0 instead of 1, which is why we reference `1` in the code to exclude column 2.

Note two things about this particular JavaScript:

  * You reference the `id` of `services` assigned to the table: `$("#services").tablesorter`
  * You specify the column you don't want to sort: `headers: {1:{sorter:false}}`

## Disable sorting on more than one column[ ↩](http://www.granneman.com/webdev/coding/css/sorting-tables/)

So far I've shown you how to disable sorting on one column. But what if you don't want users to be able to sort columns 4 _and_ 5 (which JavaScript considers to be columns 3 and 4)?

Use this JavaScript block:
    
    
    <script>
      $(document).ready(function()
        {
          $("#services").tablesorter({
            sortList: [[0,0]],
            headers: {3:{sorter:false},4:{sorter:false}}
          });
        }
      );
    </script>
    
