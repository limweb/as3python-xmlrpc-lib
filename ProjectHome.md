# AS3 Package: com.python.rpc.xmlrpc #

The AS3 package com.python.rpc.xmlrpc contains classes for easy access of python services provided by python's SimpleXMLRPCServer implementation.

The provided example is based upon tutorial: "Put a Flex UI on your application" by Bruce Eckel (mindview.net) published at: http://www.adobe.com/devnet/flex/articles/flex_ui.html



# Requires: #

  * AS3 package com.ak33m.rpc.xmlrpc.XMLRPCObject (Google code project: as3-rpclib), see http://code.google.com/p/as3-rpclib/

# Contains: #

## AS3 class PYTHONXMLRPCServer ##
  * init(host:String,port:uint):void
  * createService(name:String,...):PYTHONXMLRPCService

## AS3 class PYTHONXMLRPCService ##
  * init(server:PYTHONXMLRPCServer,name:String,...):void
  * apply(args:Array=null):void
  * call(...rest):void

# Ease of use: See the example! #

```
 +++ ActionScript code block +++
var pyServer:PYTHONXMLRPCServer=new PYTHONXMLRPCServer();
pyServer.init("127.0.0.1",9000);
var pyServiceName:String="toLowerCase";
var pyService:PYTHONXMLRPCService=pyServer.createService(pyServiceName,onFault,onResult);
pyService.call("Hello World!");
```

```
 +++ Python code block +++
import sys
from SimpleXMLRPCServer import SimpleXMLRPCServer

class MyPythonServices:	
	def toLowerCase(self, str):
		print "toLowerCase()";
		resultStr = str.lower();
		return resultStr;

server = SimpleXMLRPCServer(("localhost", 9000));
print "Local python server listening on localhost port 9000."
print " -> Close console window to stop the server and exit.";
server.register_instance(MyPythonServices());
server.serve_forever();
```
