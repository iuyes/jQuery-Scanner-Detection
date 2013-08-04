jQuery Scanner Detection
========================

jQuery Scanner Detection is a small plugin to detect when user use a scanner (barcode, QR Code...) instead of a keyboard, and call specific callbacks.


How use it
----------
To initialize the detection, 2 ways:

    $(selector).scannerDetection(); // Initiliaze with default options
    $(selector).scannerDetection({...}); // Initiliaze with an object that contains options
    $(selector).scannerDetection(function(){...}); // Initiliaze with a function that is onComplete callback
    
To simulate a scanning after initialisation:

    $(selector).scannerDetection('scanned string');


Options
-------
###onComplete
Default: false  
Callback after detection of a successfull scanning
###onError
Default: false  
Callback after detection of a unsuccessfull scanning (scanned string in parameter)
###onReceive
Default: false  
Callback after receive a char (original keypress event in parameter)
###timeBeforeScanTest
Default: 100  
Wait duration (ms) after keypress event to check if scanning is finished
###avgTimeByChar
Default: 30  
Average time (ms) between 2 chars. Used to do difference between keyboard typing and scanning
###minLength
Default: :6  
Minimum length for a scanning
###endChar
Default: [9,13]  
Chars to remove and means end of scanning
###stopPropagation
Default: false  
Stop immediate propagation on keypress event
###preventDefault
Default: false  
Prevent default action on keypress event


Events
------
All callbacks are of type function and can also be bound as event listeners.  
Like this, you can add multiple callbacks for each event.  
Of course, events exist only if plugin is initialized on selector.

    $(selector)
        .bind('scannerDetectionComplete',function(e,data){...})
        .bind('scannerDetectionError',function(e,data){...})
        .bind('scannerDetectionReceive',function(e,data){...})

###scannerDetectionComplete
Callback after detection of a successfull scanning  
Event data: {string: "scanned string"}
###scannerDetectionError
Callback after detection of a unsuccessfull scanning  
Event data: {string: "scanned string"}  
###scannerDetectionReceive
Callback after receive a char  
Event data: {evt: {original keypress event}}
