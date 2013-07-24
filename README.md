simple-3-column-css
===================

A cross-browser flexible 3-column layout CSS plus required HTML.

Working examples
----------------

[simple 3 column layout](http://rawgithub.com/dfkaye/simple-3-column-css/master/index.html)


Given this markup:

    <div id="" class="clearfix columns order-XYZ">
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


Use this CSS to specify 3-column layout, changing only the order-x-y-z class in the content wrapper div:

    /* inherit page_wrapper width */
    .columns {
      width: 100%; 
    }
    .intercolumn {
      /* contains columns 1 and 2 */
    }
    .col-1 {
      background: #ffccff;
    }
    .col-2 {
      background: #cff9f9;
    }
    .col-3 {
      background: #fff0c0;
    }
    

    /* 3-column layouts for content area */
    .columns .intercolumn {
      width:710px; /* set width to contain main and more */
    }
    .columns .col-1 {
      width:500px;
    }
    .columns .col-2 {
      width:210px;
    }
    .columns .col-3 {
      width:230px;
    }


    /* order-123 */
    .order-123 {}
    .order-123 .intercolumn {
      float:left;
    }
    .order-123 .col-1 {
      float:left;
    }
    .order-123 .col-2 {
      float:right;
    }
    .order-123 .col-3 {
      float:right;
    }


    /* order-132 */
    .order-132 {}
    .order-132 .intercolumn {
      width:auto; /* unset width for non-contiguous case in IE */
    }
    .order-132 .col-1 {
      float:left;
    }
    .order-132 .col-2 {
      float:right;
    }
    .order-132 .col-3 {
      float:right;
    }


    /* order-213 */
    .order-213 {}
    .order-213 .intercolumn {
      float:left;
    }
    .order-213 .col-1 {
      float:right;
    }
    .order-213 .col-2 {
      float:left;
    }
    .order-213 .col-3 {
      float:right;
    }


    /* order-231 */
    .order-231 {}
    .order-231 .intercolumn {
      width:auto; /* unset width for non-contiguous case in IE */
    }
    .order-231 .col-1 {
      float:right;
    }
    .order-231 .col-2 {
      float:left;
    }
    .order-231 .col-3 {
      float:right;
    }


    /* order-312 */
    .order-312 {}
    .order-312 .intercolumn {
      float:right;
    }
    .order-312 .col-1 {
      float:left;
    }
    .order-312 .col-2 {
      float:left;
    }
    .order-312 .col-3 {
      float:left;
    }


    /* order-321 */
    .order-321 {}
    .order-321 .intercolumn {
      float:right;
    }
    .order-321 .col-1 {
      float:right;
    }
    .order-321 .col-2 {
      float:left;
    }
    .order-321 .col-3 {
      float:left;
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
