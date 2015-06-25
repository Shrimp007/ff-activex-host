Example HTML:
```
<div><span id='log'></span></div> 

<OBJECT TYPE="application/x-itst-activex" id="control" logger="logger" debugLevel="5" height="0" width="0" clsid="{...whatever...}" ></OBJECT> 

<script type="text/javascript"> 
        function logger(msg) { 
                document.getElementById('log').innerHTML += msg + '<br/>'; 
        } 
</script>
```

The above example will call the logger function with each logging
message from the plugin, and it will add the new message to the 'log'
span.