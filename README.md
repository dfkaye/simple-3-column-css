simple-3-column-css
===================

A cross-browser flexible 3-column layout CSS plus required HTML.

goal
----

Given one set of markup, one set of CSS, change one CSS class name in the markup to re-order the columns.

example
-------

View the [working example](http://rawgithub.com/dfkaye/simple-3-column-css/master/index.html)

+ The basic layout works fine cross-browser, back to IE6.
+ Nesting 3-col inside another 3-col requires longer (more specific) CSS selectors to override widths, etc.

key factors
-----------

+ Solution requires float-based layouts (plus a clearfix) - makes IE6 harder because of the old "doubled margins
    in floated elements" bug we used to love.
+ Columns 1 and 2 need to be wrapped by an "intercolumn" element, with column 3 a sibling after that 
    (insight from Michael Bowers, 
        [Pro CSS and HTML Design Patterns](http://www.amazon.com/Pro-CSS-HTML-Design-Patterns/dp/1590598040/).
+ Change only the order-{XYZ} class in the "columns" div.
+ Specify actual widths of each column and intercolumn (which contains cols 1 and 2) in a separate 
    layout-specific or page-specific css file.

given this markup:
-----------------

    <div id="simple" class="clearfix columns order-xyz">
      <div class="intercolumn">
        <div class="col-1">
          <h1>1. main section</h1>
          <p>main paragraph</p>
        </div>
        <div class="col-2">
          <h1>2. more section</h1>
          <p>more paragraph</p>
        </div>
      </div>
      <div class="col-3">
        <h1>3. related section</h1>
        <p>related paragraph</p>
      </div>
    </div>


use this CSS to specify 3-column layout:
---------------------------------------

    .columns {
      /* set width to contain intercolumn and .col-3 */
    }
    .intercolumn {
      /* contains columns 1 and 2 */
      /* set width to contain col-1 and .col-2 */
      float: left;
    }
    .col-1 {
      float: left;
    }
    .col-2 {
      float: left;
    }
    .col-3 {
      float: left;
    }
    .order-132 .intercolumn {
      width: auto;  /* unset width for non-contiguous case in IE */
      float: none;
    }
    .order-132 .col-2 {
      float: right;
    }
    .order-213 .col-1 {
      float: right;
    }
    .order-231 .intercolumn {
      width: auto; /* unset width for non-contiguous case in IE */
      float: none;
    }
    .order-231 .col-1 {
      float: right;
    }
    .order-312 .intercolumn {
      float: right;
    }
    .order-321 .intercolumn {
      float: right;
    }
    .order-321 .col-1 {
      float: right;
    }

      
You'll need this for the floated layout clearing problems:

    .clearfix {
      clear: both;
    }
    .clearfix:after {
      content: ".";
      visibility: hidden;
      display: block;
      height: 0;
      clear: both;
    }
