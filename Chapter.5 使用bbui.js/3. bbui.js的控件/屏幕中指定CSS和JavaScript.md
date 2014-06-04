屏幕中指定CSS和JavaScript
-

在应用中使用到的每个屏幕都可以有属于自己的CSS和JavaScript文件，在屏幕被显示和销毁时进行动态加载和卸载。

为你的屏幕加载CSS
-

如果你想要指定CSS同你的屏幕一起加载，，你可以用以下两种方式声明。

第一种方法是在你的屏幕内容内部声明它：

    <div data-bb-type="screen">
        <style type="text/css">
            .myclass {
                 background-color: White;
             }
        </style>
    </div>

另一种方法是在屏幕的stylesheet中声明一个链接（link）。要记住一点你的stylesheet中的路径会从你已经加载完毕的应用的根源也就是主HTML页面开始算起。所以你必须让你的路径是针对于根文档的一个相对路径。

    <div data-bb-type="screen">
        <link rel="stylesheet" type="text/css" href="css/tabs.css"></link>
    </div>
    
为了支持滑动动画特效，bbUI中的屏幕背景被默认设置为白色。否则屏幕会是透明的，并且当内容滑入的时候会显示在他们的下方。所以如果你想要设置诸如屏幕背景之类的属性，那么你必须对屏幕的样式理解的十分明确。

为你的屏幕加载JavaScript
-

最普通的场景之一就是为某个屏幕指定一个你想要使用的JavaScript文件。你绝对不想要在启动应用时加载你所有屏幕的JavaScript，同样你也不想在你不使用JavaScript时，它们生成的对象却占用了大量的内存。

bbUI允许你声明JavaScript包含到你的屏幕。工具包会在屏幕被显示时负责将JavaScript文件包含到你的应用中，并且在屏幕被销毁时移除JavaScript文件。要记住一点你的JS文件的路径会从你已经加载完毕的应用的根源也就是主HTML页面开始算起。所以你必须让你的路径是针对于根文档的一个相对路径。

    <div data-bb-type="screen">
        <script src="js/tabs.js"></script>
    </div>
    
这通过添加script元素到你的DOM，并且添加JavaScript文件的路径到script的属性src中来实现。

如果你有一些JavaScript来负责在屏幕销毁时执行一些日常的清理工作，你可以使用onunload属性来声明JavaScript，使其在屏幕销毁之前被调用。

    <div data-bb-type="screen">
        <script src="js/tabs.js" onunload="unloadPushListeners()"></script>
    </div>

你也可以在屏幕中使用内部script标签。bbUI框架将会一定范围内在屏幕显示和销毁时加载和卸载它们。

    <div data-bb-type="screen">
        <script type="text/javascript">
             function foo() {
                   alert('foo');
             }  
        </script>
    </div>
