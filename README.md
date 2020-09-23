<div align="center">

## The Mapquest Code


</div>

### Description

Ever wanted to offer driving directions from your website instead of settling for a link to just a map? It's easier than you might think, no ASP or CGI involved, just plain old HTML. This also adds a whole new element to your website that's just plain neat.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Joe Maddalone](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/joe-maddalone.md)
**Level**          |Beginner
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |ASP \(Active Server Pages\), HTML
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__4-1.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/joe-maddalone-the-mapquest-code__4-8124/archive/master.zip)





### Source Code

<p>This is a technique I developed back in 2000-ish for one of my first
    commercial clients. I had actually offered it up before I was even sure
    I could do it, but nonetheless I found a way to tap into the mapquest.com
    driving directions<br />
    application.</p>
   <p>Ever wanted to offer driving directions from your website instead of
    settling for a link to just a map? It's easier than you might think, no
    ASP or CGI involved, just plain old HTML. This also adds a whole new element
    to your website that's just plain neat.</p>
   <p>The code here has been modified from my original version so that it is
    now XHTML 1.0 Valid.</p>
   <p>This is pretty much a simple copy and paste job, but I'll go over it
    once for you.</p>
   <p>When you go to mapquest and request driving directions from one point
    to another the URL you get is something like this:</p>
   <p><font color="#FF0000">http://www.mapquest.com/directions/main.adp?go=1<br />
    &amp;do=nw&amp;ct=NA&amp;1y=US&amp;1a=233+South+Wacker+Drive<br />
    &amp;1p=&amp;1c=Chicago&amp;1s=IL&amp;1z=60606&amp;1ah=&amp;2y=US<br />
    &amp;2a=1+Microsoft+Way&amp;2p=&amp;2c=Redmond&amp;2s=WA<br />
    &amp;2z=98052&amp;2ah=&amp;lr=2&amp;x=57&amp;y=15</font></p>
   <p>In this example I used Chicago's Wrigley Field as the &quot;From&quot;
    address</p>
   <p>233 S Wacker Dr<br />
    Chicago, IL<br />
    60606</p>
   <p>And the Microsft Headquartersas the &quot;To&quot; address</p>
   <p>1 Microsoft Way<br />
    Redmond, WA<br />
    20005</p>
   <p>Now the task is to break this long, long URL down. By breaking it at
    each ampersand we can get a better look at this it.</p>
   <p><br />
    <font color="#FF0000">http://www.mapquest.com/directions/main.adp?<br />
    go=1<br />
    &amp;do=nw<br />
    &amp;ct=NA<br />
    &amp;1y=US<br />
    &amp;1a=233+South+Wacker+Drive<br />
    &amp;1p=<br />
    &amp;1c=Chicago<br />
    &amp;1s=IL<br />
    &amp;1z=60606<br />
    &amp;1ah=<br />
    &amp;2y=US<br />
    &amp;2a=1+Microsoft+Way<br />
    &amp;2p=<br />
    &amp;2c=Redmond<br />
    &amp;2s=WA<br />
    &amp;2z=98052<br />
    &amp;2ah=<br />
    &amp;lr=2<br />
    &amp;x=57<br />
    &amp;y=15</font></p>
   <p><br />
    Now I make no allusion to understanding every single bit of that, I do
    however know what I need to know. Granted this is for US addresses only,
    if you want international values you'll have to look into that one on
    you own.</p>
   <p>So by further breaking the URL down we see that:</p>
   <p><br />
    <font color="#FF0000">http://www.mapquest.com/directions/main.adp?</font></p>
   <p>is the page that is being posted to by mapquest, so this is where we
    too must post to..</p>
   <p><br />
    and there are only 4 lines that seem particular to our &quot;to&quot;
    address</p>
   <p><br />
    <font color="#FF0000">&amp;2a=1+Microsoft+Way<br />
    &amp;2c=Redmond<br />
    &amp;2s=WA<br />
    &amp;2z=98052</font></p>
   <p>These are our constants, this is our address, basically<br />
    After we remove these we are left with</p>
   <p><br />
    <font color="#FF0000">go=1<br />
    &amp;do=nw<br />
    &amp;ct=NA<br />
    &amp;1y=US<br />
    &amp;1a=233+South+Wacker+Drive<br />
    &amp;1p=<br />
    &amp;1c=Chicago<br />
    &amp;1s=IL<br />
    &amp;1z=60606<br />
    &amp;1ah=<br />
    &amp;2y=US<br />
    &amp;2ah=<br />
    &amp;lr=2<br />
    &amp;x=57<br />
    &amp;y=15</font></p>
   <p>This is the information we want our website visitor to enter.</p>
   <p>So putting this into a form would look like this:</p>
   <p> <font color="#FF0000">&lt;form name=&quot;ddform&quot; action=http://mapquest.com/directions/main.adp
    target=_blank method=get&gt;</font></p>
   <p><br />
    &lt;!--hidden fields--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='go' value='1'&gt;<br />
    &lt;input type=&quot;hidden&quot; name='do' value='nw'&gt;<br />
    &lt;input type=&quot;hidden&quot; name='ct' value='NA'&gt;<br />
    &lt;input type=&quot;hidden&quot; name='1ah' value=''&gt;</font></p>
   <p><br />
    &lt;!--The From Street--&gt;<br />
    <font color="#FF0000">Street:&lt;input name='1a' type=text size=&quot;15&quot;&gt;&lt;br
    /&gt;</font></p>
   <p><br />
    &lt;!--hidden field--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='1p' value=''&gt;</font></p>
   <p>&lt;!--The From City--&gt;<br />
    <font color="#FF0000">City:&lt;input name='1c' type=text size=&quot;15&quot;&gt;&lt;br
    /&gt;</font></p>
   <p>&lt;!--The From State--&gt;<br />
    <font color="#FF0000">State: &lt;input name='1s' type=text size=&quot;5&quot;&gt;&lt;br
    /&gt;</font></p>
   <p>&lt;!--The From Zip Code--&gt;<br />
    <font color="#FF0000">Zip:&lt;input name=&quot;1z&quot; type=&quot;text&quot;
    size=&quot;15&quot;&gt;&lt;br /&gt;</font></p>
   <p>&lt;!--hidden field--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='z' value=''&gt;</font></p>
   <p>&lt;!--hidden field for From Country--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='1y' value='US'&gt;</font></p>
   <p>&lt;!--hidden field--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='2ah' value=''&gt;</font></p>
   <p><br />
    &lt;!--hidden field for To Street Address--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='2a' value=1+Microsoft+Way'&gt;</font></p>
   <p>&lt;!--hidden field--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='2p' value=''&gt;</font></p>
   <p>&lt;!--hidden field for To City--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='2c' value=Redmond'&gt;</font></p>
   <p>&lt;!--hidden field for To State--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='2s' value='WA'&gt;</font></p>
   <p>&lt;!--hidden field for To Zip Code--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='2z' value='98052'&gt;</font></p>
   <p>&lt;!--hidden field for the To Country--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='2y' value='US'&gt;</font></p>
   <p>&lt;!--hidden field--&gt;<br />
    <font color="#FF0000">&lt;input type=&quot;hidden&quot; name='lr' value='2'&gt;<br />
    &lt;input type=&quot;hidden&quot; name='x' value='75'&gt;<br />
    &lt;input type=&quot;hidden&quot; name='y' value='8'&gt;<br />
    &lt;br /&gt;<br />
    &lt;br /&gt;<br />
    &lt;input type=submit value='Submit'&gt;<br />
    &lt;/form&gt;</font></p>
   <p></p>
   <p>And there you have it.<br />
    If your business was located at the Ms headquarters anybody could get
    direction right from your website. Here's a working Example</p>
   <p>
    <form name=ddForm action=http://mapquest.com/directions/main.adp target=_blank method=get>
      <input type=hidden name='go' value='1'>
      <input type=hidden name='do' value='nw'>
      <input type=hidden name='ct' value='NA'>
      <input type=hidden name='1ah' value=''>
      Street:
      <input name='1a' type=text size="15">
      <input type=hidden name='1p' value=''>
      City:
      <input name='1c' type=text size="15">
      State:
      <input name='1s' type=text size="5">
      <input type=hidden name='z' value=''>
      <input type=hidden name='1y' value='US'>
      <input type=hidden name='2ah' value=''>
      <input type=hidden name='2a' value='1+Microsoft+Way'>
      <input type=hidden name='2p' value=''>
      <input type=hidden name='2c' value='Redmond'>
      <input type=hidden name='2s' value='WA'>
      <input type=hidden name='2z' value='98052'>
      <input type=hidden name='2y' value='US'>
      <input type=hidden name='lr' value='2'>
      <input type=hidden name='x' value='75'>
      <input type=hidden name='y' value='8'>
      <br>
      <br>
      <input type=submit value='Submit'>
    </form>
	 <p>In a follow up article to this I'll approach the same concept using databases
    for this process.</p>

