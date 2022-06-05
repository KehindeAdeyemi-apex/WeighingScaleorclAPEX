# WeighingScaleorclAPEX
Weighing Scale Integration with Oracle APEX


<h2>Prerequisites</h2>

<ul>
  <li>Weighing Scale connected to network or serial port </li>
  <li>Operating System: Windows 8 or Later </li>
  <li>Windows Powershell</li>
  <li>Nodejs</li>
  <li>Python (Optional)</li>
</ul>  


---------------------------------------------------STEP 1------------------------------
Download and Install NodeJS using the link below<br/>
<a href="https://nodejs.org/en/" target="_blank">Nodejs</a>
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shCore.js"></script>
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shBrushJScript.js"></script>
<link href="#APP_IMAGES#syntaxhighlighter/shCore.css" rel="stylesheet" type="text/css" />
<link href="#APP_IMAGES#syntaxhighlighter/shThemeDefault.css" rel="stylesheet" type="text/css" /><br/><br/>
<ol>
<li>Create a folder in your drive e.g c:\ScaleIntegration</li>
<li>Open your command line, navigate to step 1 and type command below</li>

<pre class="brush: js">npm init</pre> 
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>
<a href="https://drive.google.com/uc?export=view&id=1wXe07IvtWOaFcXmq1VGcDoAWlBUMU-DM"> <img src="https://drive.google.com/uc?export=view&id=1wXe07IvtWOaFcXmq1VGcDoAWlBUMU-DM" width="100%"/></a>
<li>while still on the command line, type command below</li>

<pre class="brush: js">npm i express</pre> 
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>
<a href="https://drive.google.com/uc?export=view&id=1sjHz6acDMc5_fy6k9vU5mnlisSbboZBh"> <img src="https://drive.google.com/uc?export=view&id=1sjHz6acDMc5_fy6k9vU5mnlisSbboZBh" width="100%"/></a>

</ol>

-----------------------------STEP 2 (OPTIONAL) ------------------------------------
Download and Install Python using the link below<br/>
<a href="https://www.python.org/downloads/" target="_blank">Python</a><br/><br/>
If the Weighing Scale is connected on a network port you may use sample python script and save as <b>getweight.py</b> in in folder c:\ScaleIntegration
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shCore.js"></script>
 
<!--
    At least one brush, here we choose JS. You need to include a brush for every
    language you want to highlight
-->
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shBrushJScript.js"></script>
 
<!-- Include *at least* the core style and default theme -->
<link href="#APP_IMAGES#syntaxhighlighter/shCore.css" rel="stylesheet" type="text/css" />
<link href="#APP_IMAGES#syntaxhighlighter/shThemeDefault.css" rel="stylesheet" type="text/css" />
 
<!-- You also need to add some content to highlight, but that is covered elsewhere. -->
<pre class="brush: js">
import socket, time
scalesocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
scalesocket.connect(('XXX.XXX.X.XX', XXXX))
#XXX.XXX.X.XX - I.P address XXXX - Port No

while True:
    time.sleep(0)
	#receive data from network port and limit to number of characters returned (20) in this example
    data = scalesocket.recv(20)
    #locate and print exact reading based on position in string
    print(repr(data)[10:-1])
    scalesocket.close()
    break
</pre>
 
<!-- Finally, to actually run the highlighter, you need to include this JS on your page -->
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>

-------------------------------------STEP 3------------------------------------------
Create and save Windows Powershell script<br/>
<br/>
create a powershell script called <b>readscale.ps1</b> and save in folder c:\ScaleIntegration

if you have decided to call a python script similar to STEP 2, use below script
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shCore.js"></script>
 
<!--
    At least one brush, here we choose JS. You need to include a brush for every
    language you want to highlight
-->
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shBrushJScript.js"></script>
 
<!-- Include *at least* the core style and default theme -->
<link href="#APP_IMAGES#syntaxhighlighter/shCore.css" rel="stylesheet" type="text/css" />
<link href="#APP_IMAGES#syntaxhighlighter/shThemeDefault.css" rel="stylesheet" type="text/css" />
 
<!-- You also need to add some content to highlight, but that is covered elsewhere. -->
<pre class="brush: js">
<#PSScriptInfo
.VERSION 1.0
#>

c:\path_to_pythonhome\python.exe c:\ScaleIntegration\getweight.py
</pre>
 
<!-- Finally, to actually run the highlighter, you need to include this JS on your page -->
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>
<br/><br/>
OR if you are capturing directly from a serial port and intend to call directly from powershell, you may use below sample script
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shCore.js"></script>
 
<!--
    At least one brush, here we choose JS. You need to include a brush for every
    language you want to highlight
-->
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shBrushJScript.js"></script>
 
<!-- Include *at least* the core style and default theme -->
<link href="#APP_IMAGES#syntaxhighlighter/shCore.css" rel="stylesheet" type="text/css" />
<link href="#APP_IMAGES#syntaxhighlighter/shThemeDefault.css" rel="stylesheet" type="text/css" />
 
<!-- You also need to add some content to highlight, but that is covered elsewhere. -->
<pre class="brush: js">
<#PSScriptInfo
.VERSION 1.0
#>

$port= new-Object System.IO.Ports.SerialPort COM3,9600,None,8,one
$port.Open()
$port.ReadLine()
</pre>
 
<!-- Finally, to actually run the highlighter, you need to include this JS on your page -->
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>

<br/>
<br/>
Create and save nodejs script<br/>
<br/>
create a nodejs script called <b>readscaleapp.js</b> and save in folder c:\ScaleIntegration,
Ensure the right parameter values are retrieved sent to the nodejs url e.g <b>http://localhost:8099/?appsession=&APP_SESSION .&record=&P7_RECORD_ID .</b> , use below script
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shCore.js"></script>
 
<!--
    At least one brush, here we choose JS. You need to include a brush for every
    language you want to highlight
-->
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shBrushJScript.js"></script>
 
<!-- Include *at least* the core style and default theme -->
<link href="#APP_IMAGES#syntaxhighlighter/shCore.css" rel="stylesheet" type="text/css" />
<link href="#APP_IMAGES#syntaxhighlighter/shThemeDefault.css" rel="stylesheet" type="text/css" />
 
<!-- You also need to add some content to highlight, but that is covered elsewhere. -->
<pre class="brush: js">
/*Author: Kehinde Adeyemi*/
var http = require('http');
var url = require('url');


var spawn = require("child_process").spawn,child;
  console.log("Powershell initializing: ");
child = spawn("powershell.exe",["c:\\ScaleIntegration\\readscale.ps1"]);
child.stdout.on("data",function(data){
    console.log("Powershell Data: " + data);
});
child.stderr.on("data",function(data){
    console.log("An Error occurred, please check if scale is connected and/or port is open");
});
child.on("exit",function(){
    console.log("Powershell Script initialized...");
});
child.stdin.end();


http.createServer(function (req, res) {

  res.writeHead(200, {'Content-Type': 'text/html'});
  /*Use the url module to turn the querystring into an object:*/
  var q = url.parse(req.url, true).query;
  var spawn = require("child_process").spawn,child;
  console.log("Powershell starting: ");
child = spawn("powershell.exe",["c:\\ScaleIntegration\\readscale.ps1"]);
child.stdout.on("data",function(data){
    console.log("Powershell Data in : " + data + q.appsession + " " + q.recordid);

  var txt =  data;
  res.write('<center><span style="font-size:50px">' + txt + '</span></center>&nbsp;<br><br><br>');
  res.write('<center><a href="https://apex.oracle.com/ords/f?p=100471:7:' + q.appsession + '::::P7_RECORD_ID,P7_WEIGHT:'+ q.recordid + "," + data + '" target="_parent" class="btn btn-primary">Record Weight</a></center>');
  res.end();
	
});
child.stderr.on("data",function(data){
    console.log("An Error occurred, please check if scale is connected and/or port is open");
	 var txt = "An Error occurred, please check if scale is connected and/or port is open";
  res.end(txt);
});

 
  child.on("exit",function(){
    console.log("Powershell Script finished");
});
child.stdin.end();
  
}).listen(8099);


</pre>
 
<!-- Finally, to actually run the highlighter, you need to include this JS on your page -->
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>

<br/>
<br/>
Create a batch file<br/>
<br/>
create a batch file to execute the nodejs script called readscaleapp.js and save as <b>readscale.bat</b> in folder c:\ScaleIntegration

<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shCore.js"></script>
 
<!--
    At least one brush, here we choose JS. You need to include a brush for every
    language you want to highlight
-->
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shBrushJScript.js"></script>
 
<!-- Include *at least* the core style and default theme -->
<link href="#APP_IMAGES#syntaxhighlighter/shCore.css" rel="stylesheet" type="text/css" />
<link href="#APP_IMAGES#syntaxhighlighter/shThemeDefault.css" rel="stylesheet" type="text/css" />
 
<!-- You also need to add some content to highlight, but that is covered elsewhere. -->
<pre class="brush: js">
cd  c:\ScaleIntegration
node readscaleapp.js
</pre>
 
<!-- Finally, to actually run the highlighter, you need to include this JS on your page -->
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>

<br/>
<br/>
<b>Create a scheduled task to launch the batch file and you may also create it as a windows service</b><br/>
<br/>

--------------------------------------STEP 4---------------------------------------

On your APEX application<br/>
<ol>
  <li>Create a page (I used page 7 in my scenario) </li>
  <li>Create a Static Content Region </li>
  <li>Add the following (copy only the iframe component and remove the spaces before the dots). <br/>
  <script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shCore.js"></script> 
<script type="text/javascript" src="#APP_IMAGES#syntaxhighlighter/shBrushJScript.js"></script>
 
<!-- Include *at least* the core style and default theme -->
<link href="#APP_IMAGES#syntaxhighlighter/shCore.css" rel="stylesheet" type="text/css" />
<link href="#APP_IMAGES#syntaxhighlighter/shThemeDefault.css" rel="stylesheet" type="text/css" />
 
<!-- You also need to add some content to highlight, but that is covered elsewhere. -->
<pre class="brush: js">
 <!--
 <iframe src="http://localhost:8099/?appsession=&APP_SESSION .&recordid=&P7_RECORD_ID ." title="description" onload="this.width=screen.width;"></iframe>"
 -->
</pre>
 
<!-- Finally, to actually run the highlighter, you need to include this JS on your page -->
<script type="text/javascript">
     SyntaxHighlighter.all()
</script>
 </li>
  <li>Create a button to reload page</li>
</ol>  
