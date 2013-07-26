simple-3-column-css
===================

A cross-browser flexible 3-column layout CSS plus required HTML.

The basic (not nested) layout works fine cross-browser.

There are complications when nesting 3-col inside another 3-col.

View the [working example](http://rawgithub.com/dfkaye/simple-3-column-css/master/index.html)


__TODO: UPDATE EXPLANATION BELOW - WAY OUT OF DATE__


Explanation
-----------

nod to michael bowers
basis for the markup, class rules, etc.

Given this markup:

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


Use this CSS to specify 3-column layout, changing only the order-{XYZ} class in the "columns" div.
Then you can specify the actual widths of each column and intercolumn (which contains cols 1 and 2)
in a separate layout-specific or page-specific css file:

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
