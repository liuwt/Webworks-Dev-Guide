屏幕中指定CSS和JavaScript
-

Each screen used in the application can have its own CSS and JavaScript files that will be loaded/unloaded dynamically when the screen is pushed and popped.

Loading CSS for your screen

If you have screen specific CSS that you would like to load with your screen, you can declare that CSS in one of two ways.

First is by declaring it inline with your screen contents:

    <div data-bb-type="screen">
        <style type="text/css">
            .myclass {
                 background-color: White;
             }
        </style>
    </div>

An alternative is to declare a linked in style sheet within your screen's content. Just remember that the path to your style sheet will start from the main HTML page that you have loaded as the root of your application. So you should make your paths relative to that root document.

    <div data-bb-type="screen">
        <link rel="stylesheet" type="text/css" href="css/tabs.css"></link>
    </div>
    
To support the slide animation effects, screens in bbUI have their backgrounds set to "white" by default. Otherwise the screens would be transparent and show the content underneath them as they slide in. You must explicitly set the style of your screen if you want to set properties such as screen background.

Loading JavaScript for your screen

One of the more common scenarios is to have specific JavaScript files that you want to use for a certain screen. You really don't want to load up all of your screen's JavaScript on launch of your application, nor do you want to continue to use tons of memory to have your JavaScript objects sitting around while you're not using them.

bbUI allows you to declare JavaScript files to include with your screen. The toolkit will actually take care of including this JavaScript into your application when the screen is pushed onto the stack, and it will remove this JavaScript when the screen is popped back off of the stack. Just remember that the path to your JS file will start from the main HTML page that you have loaded as the root of your application. So you should make your paths relative to that root document.

    <div data-bb-type="screen">
        <script src="js/tabs.js"></script>
    </div>
    
This is accomplished by adding the <script> element into your DOM and the src path to the JavaScript file itself.

If you have JavaScript that needs to perform some cleanup routines when your screen gets popped off of the stack, you can also declare JavaScript to be called before the screen is popped off of the stack using the onunload attribute.

    <div data-bb-type="screen">
        <script src="js/tabs.js" onunload="unloadPushListeners()"></script>
    </div>

You can also use in-line script tags with your screen. The bbUI framework will load and unload these from scope when the screen is pushed or popped.

    <div data-bb-type="screen">
        <script type="text/javascript">
             function foo() {
                   alert('foo');
             }  
        </script>
    </div>
