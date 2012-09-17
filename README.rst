======================
CUSTOMIZATIONS FOR APL 
======================

1. Vertical scroll

   In  ``shellinabox/vt100.js``, ``min-height:350px`` has been changed.
   Look for the following snippet.

::

    '<div id="keyboard" unselectable="on">' +
    '</div>' +
    '<div id="scrollable" style="height:auto;min-height:350px;">'   +
    '<table id="kbd_button">' +
    '<tr><td width="100%">&nbsp;</td>' +
    '<td><img id="kbd_img" src="keyboard.png" /></td>' +


Also a line need to be commented in same ``vt100.js`` file.

::

    var partial = height % this.cursorHeight;
    // this.scrollable.style.height = (height > 0 ? height : 0) + 'px';  
    this.padding.style.height    = (partial > 0 ? partial : 0) + 'px';

2. Horizontal scroll

    In ``shellinabox/style.css`` add html attribute. As webview in android
    is having a definite width ,exceeding the html width make's it scroll horizontally.

:: 
    
    html
    {
        width:350%;
    }

3. Font size and bg color

    In ``shellinabox/style.css`` change the following attributes and add 
    ``font-size`` attribute to #vt100 #console.

::
 
    #vt100 #console{
    background-color:#330033;
    color:white;
    height:auto;
    min-height:420px;
    }   

    #vt100 #console, #vt100 #alt_console, #vt100 #cursor, #vt100 #lineheight, #vt100 .hidden pre { 
    font-family: "DejaVu Sans Mono", "Everson Mono", FreeMono, "Andale Mono", monospace;
    font-size: 11pt;
    }

4. ``Session Closed`` 
    
    In ``shellinabox/shell_in_a_box.js`` & ``shellinabox/shell_in_a_box.jspp`` 
    look for following code, and replace the strings in both ``this.vt100`` with empty string.

:: 

    if (this.cursorX > 0) {
    this.vt100('\r\n');
    }
    this.vt100('Session closed.');
    }
    
Also don't forgot to give ``--host=arm`` in ``./configure`` option. Set 
``export CC=arm-none-linux-gnueabi-gcc``


