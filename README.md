#  AutoReload

**NOTE:** this doesn't really work yet!

AutoReload is a node.js auto refresher built atop socket.io. AutoReload watches for file system changes and refreshes a webpage that is connected to it. This allows front-end developers to see a live preview as they code.

To start the daemon simply run 

    // Usage: autoreload [directory/file to watch]
    autoreload ~/workspace/myproject
    
To setup the webpage you want to refresh add the following snippet (your host may differ depending on your individual setup). **NOTE:** this must be added to the bottom of webpage. before closing body tag.

    <script>
    (function(){
    var host = "http://localhost:1337";
    var s=document.createElement("script");s.src=host+"/socket.io/socket.io.js";document.body.appendChild(s);s.addEventListener("load",function(){io.connect(host).on("reload",function(){window.location.reload()})});        
    })();
    </script>
    
