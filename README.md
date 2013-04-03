simple-3-column-css
===================

Given this markup:

      <div id="" class="clearfix content_wrapper columns order-x-y-z">
        <div id="" class="intercolumn">
          <section id="" class="main_content">
            <h1>1. main section</h1>
            <p>main paragraph</p>
          </section>
          <section id="" class="more_content">
            <h1>2. more section</h1>
            <p>more paragraph</p>
          </section>
        </div>
        <section id="" class="related_content">
          <h1>3. related section</h1>
          <p>related paragraph</p>
        </section>
      </div>


Use this CSS to specify 3-column layout, changing only the order-x-y-z class in the content wrapper div:

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


/* main content area */
.content_wrapper {
width:100%; /* inherit page_wrapper width */
}
.intercolumn {
/* contains columns 1 and 2 */
}
.main_content {
background: red;
}
.more_content {
background: blue;
}
.related_content {
background: yellow;
}

/* 3-column layouts for content area */
.columns {}
.columns .intercolumn {
width:710px; /* set width to contain main and more */
}
.columns .main_content {
width:500px;
}
.columns .more_content {
width:210px;
}
.columns .related_content {
width:230px;
}

/* order-1-2-3 */
.order-1-2-3 {}
.order-1-2-3 .intercolumn {
float:left;
}
.order-1-2-3 .main_content {
float:left;
}
.order-1-2-3 .more_content {
float:right;
}
.order-1-2-3 .related_content {
float:right;
}

/* order-1-3-2 */
.order-1-3-2 {}
.order-1-3-2 .intercolumn {
width:auto; /* unset width for non-contiguous case in IE */
}
.order-1-3-2 .main_content {
float:left;
}
.order-1-3-2 .more_content {
float:right;
}
.order-1-3-2 .related_content {
float:right;
}

/* order-2-1-3 */
.order-2-1-3 {}
.order-2-1-3 .intercolumn {
float:left;
}
.order-2-1-3 .main_content {
float:right;
}
.order-2-1-3 .more_content {
float:left;
}
.order-2-1-3 .related_content {
float:right;
}

/* order-2-3-1 */
.order-2-3-1 {}
.order-2-3-1 .intercolumn {
width:auto; /* unset width for non-contiguous case in IE */
}
.order-2-3-1 .main_content {
float:right;
}
.order-2-3-1 .more_content {
float:left;
}
.order-2-3-1 .related_content {
float:right;
}

/* order-3-1-2 */
.order-3-1-2 {}
.order-3-1-2 .intercolumn {
float:right;
}
.order-3-1-2 .main_content {
float:left;
}
.order-3-1-2 .more_content {
float:left;
}
.order-3-1-2 .related_content {
float:left;
}

/* order-3-2-1 */
.order-3-2-1 {}
.order-3-2-1 .intercolumn {
float:right;
}
.order-3-2-1 .main_content {
float:right;
}
.order-3-2-1 .more_content {
float:left;
}
.order-3-2-1 .related_content {
float:left;
}
