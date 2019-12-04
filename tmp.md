


<div class=WordSection1>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1001: Hello,
world!</span></b><span lang=EN-US style='font-size:16.0pt;font-family:宋体;
color:blue'><o:p></o:p></span></p>

<div style='margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>26</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>13:11<o:p></o:p></span></p>

</div>

<div style='margin-top:24.1pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:宋体;color:blue'>Description</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt'>This is the first problem for test. Since all we know the ASCII code,
your job is simple: Input numbers and output corresponding messages. <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:宋体;color:blue'>Input</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt'>The input will contain a list of positive integers separated by
whitespaces(spaces, newlines, TABs). Please process to the end of file (EOF).
The integers will be no less than 32.<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:宋体;color:blue'>Output</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt'>Output the corresponding message. Note there is NOT a newline character
in the end of output. <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:宋体;color:blue'>Sample Input</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
13.5pt;background:#8DB8FF'>72 101 108 108 111 44<br>
32 119 111 114 108 100 33</span><span lang=EN-US style='font-size:13.5pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:宋体;color:blue'>Sample Output</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
13.5pt;background:#8DB8FF'>Hello, world!</span><span lang=EN-US
style='font-size:13.5pt'><o:p></o:p></span></p>

</div>

<div style='margin-top:85.2pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;</span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'><span style='mso-spacerun:yes'> 
</span>//</span><span style='font-size:16.0pt;font-family:宋体'>输入</span><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri'>ASCII</span><span
style='font-size:16.0pt;font-family:宋体'>码，输出相应的字符</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int ch;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>while(scanf(&quot;%d&quot;,&amp;ch)!=EOF)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%c&quot;,ch);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:18.0pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1009: A+B for
Input-Output Practice (VII)</span></b><span lang=EN-US style='font-size:16.0pt;
font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:18.0pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>26</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>8:22<o:p></o:p></span></p>

</div>

<div style='margin-left:16.4pt;margin-top:22.55pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shapetype id="_x0000_t75" coordsize="21600,21600"
 o:spt="75" o:preferrelative="t" path="m@4@5l@4@11@9@11@9@5xe" filled="f"
 stroked="f">
 <v:stroke joinstyle="miter"/>
 <v:formulas>
  <v:f eqn="if lineDrawn pixelLineWidth 0"/>
  <v:f eqn="sum @0 1 0"/>
  <v:f eqn="sum 0 0 @1"/>
  <v:f eqn="prod @2 1 2"/>
  <v:f eqn="prod @3 21600 pixelWidth"/>
  <v:f eqn="prod @3 21600 pixelHeight"/>
  <v:f eqn="sum @0 0 1"/>
  <v:f eqn="prod @6 1 2"/>
  <v:f eqn="prod @7 21600 pixelWidth"/>
  <v:f eqn="sum @8 21600 0"/>
  <v:f eqn="prod @7 21600 pixelHeight"/>
  <v:f eqn="sum @10 21600 0"/>
 </v:formulas>
 <v:path o:extrusionok="f" gradientshapeok="t" o:connecttype="rect"/>
 <o:lock v:ext="edit" aspectratio="t"/>
</v:shapetype><v:shape id="图片_x0020_1" o:spid="_x0000_i1048" type="#_x0000_t75"
 alt="算机生成了可选文字: 题目描述&#10;YOU比task15toCalCU恤tea一b_&#10;输入&#10;Themput从也consistofasenesofp盯5ofint恨ersaandb,s即arated勿aspace,onepairofint吧ersper如e-&#10;输出&#10;Foreachpairofinputint嗯ersaandbyoushouldoutPutthesumofaandb:andfollowedbyabl肚水line&#10;样例输入&#10;15&#10;1020&#10;样例输出&#10;6&#10;30"
 style='width:846pt;height:474pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image001.png" o:title="andfollowedbyabl肚水line&#10;样例输入&#10;15&#10;1020&#10;样例输出&#10;6&#10;30"/>
</v:shape><![endif]--><![if !vml]><img width=846 height=474
src="ACM.fld/image001.png"
alt="算机生成了可选文字: 题目描述&#10;YOU比task15toCalCU恤tea一b_&#10;输入&#10;Themput从也consistofasenesofp盯5ofint恨ersaandb,s即arated勿aspace,onepairofint吧ersper如e-&#10;输出&#10;Foreachpairofinputint嗯ersaandbyoushouldoutPutthesumofaandb:andfollowedbyabl肚水line&#10;样例输入&#10;15&#10;1020&#10;样例输出&#10;6&#10;30"
v:shapes="图片_x0020_1"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-top:9.95pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int a,b,sum;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>while(scanf(&quot;%d%d&quot;,&amp;a,&amp;b)!=EOF)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>sum=a+b;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%d\n\n&quot;,sum);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1010: A+B for
Input-Output Practice</span></b><span lang=EN-US style='font-size:16.0pt;
font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>20</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>23:35<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='mso-no-proof:
yes'><!--[if gte vml 1]><v:shape id="图片_x0020_2" o:spid="_x0000_i1047" type="#_x0000_t75"
 alt="算机生成了可选文字: Description&#10;task15tocalc山tethesuxnofsomeint馆ers&#10;Input&#10;cont抑5anint吧erNinthe份stljne,andthenNlines&#10;Each如estarts认ithaintegerM,andthenM&#10;fono认护inthes习nle如e&#10;Output&#10;ForeachgrouPofinputintegersyoushould&#10;th比suminoneline,andyoumustnotethatthere15ab恤nk枷ebetw散outPuts&#10;SampleInput&#10;3&#10;41234&#10;45&#10;33&#10;22&#10;l1&#10;53&#10;Sampleoutput&#10;05&#10;116"
 style='width:932pt;height:540pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image002.png" o:title=" Description&#10;task15tocalc山tethesuxnofsomeint馆ers&#10;Input&#10;cont抑5anint吧erNinthe份stljne,andthenNlines&#10;Each如estarts认ithaintegerM,andthenM&#10;fono认护inthes习nle如e&#10;Output&#10;ForeachgrouPofinputintegersyoushould&#10;th比suminoneline,andyoumustnotethatthere15ab恤nk枷ebetw散outPuts"/>
</v:shape><![endif]--><![if !vml]><img width=932 height=540
src="ACM.fld/image002.png"
alt="算机生成了可选文字: Description&#10;task15tocalc山tethesuxnofsomeint馆ers&#10;Input&#10;cont抑5anint吧erNinthe份stljne,andthenNlines&#10;Each如estarts认ithaintegerM,andthenM&#10;fono认护inthes习nle如e&#10;Output&#10;ForeachgrouPofinputintegersyoushould&#10;th比suminoneline,andyoumustnotethatthere15ab恤nk枷ebetw散outPuts&#10;SampleInput&#10;3&#10;41234&#10;45&#10;33&#10;22&#10;l1&#10;53&#10;Sampleoutput&#10;05&#10;116"
v:shapes="图片_x0020_2"><![endif]></span><span lang=EN-US><o:p></o:p></span></p>

</div>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=883
 style='width:882.7pt;margin-left:1.5pt;border-collapse:collapse;mso-yfti-tbllook:
 1184;mso-padding-alt:0cm 0cm 0cm 0cm' cols=3>
 <tr style='mso-yfti-irow:0;mso-yfti-firstrow:yes;height:.75pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  .75pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=396 valign=top style='width:396.3pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=180 valign=top style='width:179.55pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=307 valign=top style='width:306.7pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
 </tr>
 <tr style='mso-yfti-irow:1;height:499.95pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  499.95pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=396 rowspan=2 valign=top style='width:396.3pt;padding:0cm 0cm 0cm 0cm;
  height:499.95pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;</span><span
  lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
  style='mso-spacerun:yes'>       </span></span><span lang=EN-US
  style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>int a,b,i,j,l[1000],k;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>scanf(&quot;%d&quot;,&amp;i);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>getchar();<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(j=1;j&lt;=i;j++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>l[j]=0;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(j=1;j&lt;=i;j++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>getchar();<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(k=1;k&lt;=a;k++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>scanf(&quot;%d&quot;,&amp;b);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>getchar();<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>l[j]+=b;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(j=1;j&lt;=i-1;j++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:11.0pt;font-family:
  微软雅黑'>&nbsp;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>printf(&quot;%d<b><span style='color:red'>\n\n</span></b>&quot;,l[j]);</span><span
  lang=EN-US style='font-size:16.0pt;font-family:Calibri'> //</span><span
  style='font-size:16.0pt;font-family:宋体'>一个</span><span lang=EN-US
  style='font-size:16.0pt;font-family:Calibri'>\n</span><span style='font-size:
  16.0pt;font-family:宋体'>不行。。</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:11.0pt;font-family:
  微软雅黑'>&nbsp;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>printf(&quot;%d\n&quot;,l[i]);<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>}<o:p></o:p></span></p>
  </td>
  <td width=180 valign=top style='width:179.55pt;padding:0cm 0cm 0cm 0cm;
  height:499.95pt'></td>
  <td width=307 valign=top style='width:306.7pt;padding:0cm 0cm 0cm 0cm;
  height:499.95pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;</span><span
  lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
  style='mso-spacerun:yes'>  </span></span><span lang=EN-US style='font-size:
  16.0pt'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>int a,b[10],c[10][10],d=0,i,j;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(j=0;j&lt;a;j++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>scanf(&quot;%d&quot;,&amp;b[j]);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(i=0;i&lt;b[j];i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>scanf(&quot;%d&quot;,&amp;c[i][j]);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(j=0;j&lt;a;j++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span
  style='mso-spacerun:yes'>         </span>for(i=0;i&lt;b[j];i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'><span style='mso-spacerun:yes'> </span>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'><span style='mso-spacerun:yes'>     </span>d=d+c[i][j];<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'><span style='mso-spacerun:yes'> </span>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'><span style='mso-spacerun:yes'> </span>printf(&quot;%d&quot;,d);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'><span style='mso-spacerun:yes'> </span>printf(&quot;</span><span
  lang=EN-US style='font-size:16.0pt;font-family:黑体;color:red'>\n\n</span><span
  lang=EN-US style='font-size:16.0pt;font-family:宋体'>&quot;);</span><span
  lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'><span style='mso-spacerun:yes'> </span>d=0;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>}<o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:2;mso-yfti-lastrow:yes;height:58.45pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  58.45pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=180 valign=top style='width:179.55pt;padding:0cm 0cm 0cm 0cm;
  height:58.45pt'></td>
  <td width=307 valign=top style='width:306.7pt;padding:0cm 0cm 0cm 0cm;
  height:58.45pt'></td>
 </tr>
</table>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:"方正静蕾简体","serif";color:blue'>OneNoteTitle 1013:
The 3n + 1 problem</span></b><span lang=EN-US style='font-size:16.0pt;
font-family:"方正静蕾简体","serif";color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2014</span><span style='font-size:9.0pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:gray'>年</span><span
lang=EN-US style='font-size:9.0pt;font-family:Calibri;color:gray'>8</span><span
style='font-size:9.0pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:gray'>月</span><span lang=EN-US
style='font-size:9.0pt;font-family:Calibri;color:gray'>19</span><span
style='font-size:9.0pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:gray'>日</span><span lang=EN-US
style='font-size:9.0pt;color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>19:50<o:p></o:p></span></p>

</div>

<div style='margin-top:3.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Description</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>Consider the following algorithm to generate a sequence of
numbers. Start with an integer n. If n is even, divide by 2. If n is odd,
multiply by 3 and add 1. Repeat this process with the new value of n,
terminating when n = 1. For example, the following sequence of numbers will be
generated for n = 22: 22 11 34 17 52 26 13 40 20 10 5 16 8 4 2 1 It is
conjectured (but not yet proven) that this algorithm will terminate at n = 1
for every integer n. Still, the conjecture holds for all integers up to at
least 1, 000, 000. For an input n, the cycle-length of n is the number of
numbers generated up to and including the 1. In the example above, the cycle
length of 22 is 16. Given any two numbers i and j, you are to determine the
maximum cycle length over all numbers between i and j, including both
endpoints.<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Input</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>The input will consist of a series of pairs of integers i
and j, one pair of integers per line. All integers will be less than 1,000,000
and greater than 0.<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Output</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>For each pair of input integers i and j, output i, j in the
same order in which they appeared in the input and then the maximum cycle
length for integers between and including i and j. These three numbers should
be separated by one space, with all three numbers on one line and with one line
of output for each line of input.<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Sample
Input</span></b><span lang=EN-US style='font-size:18.0pt;font-family:SimSun;
color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
13.5pt;color:black;background:#8DB8FF'>1 10 100 200 201 210 900 1000 </span><span
lang=EN-US style='font-size:13.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Sample
Output</span></b><span lang=EN-US style='font-size:18.0pt;font-family:SimSun;
color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
13.5pt;color:black;background:#8DB8FF'>1 10 20 100 200 125 201 210 89 900 1000
174 </span><span lang=EN-US style='font-size:13.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>HINT</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>输入中的</span><span
lang=EN-US style='font-size:10.5pt;color:black'>i</span><span style='font-size:
10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:
DengXian;mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;
color:black'>可能大于</span><span lang=EN-US style='font-size:10.5pt;color:black'>j</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>，并且输出中，要求输出的是原本的</span><span
lang=EN-US style='font-size:10.5pt;color:black'>i</span><span style='font-size:
10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:
DengXian;mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;
color:black'>和</span><span lang=EN-US style='font-size:10.5pt;color:black'>j<o:p></o:p></span></p>

</div>

<div style='margin-top:34.7pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>int a,n,c,x,y,b,i,m,g,h;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>while(scanf(&quot;%d %d&quot;,&amp;x,&amp;y)!=EOF)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>b=0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>g=x;h=y;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>if(x&gt;y)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>m=x;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>x=y;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>y=m;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>for(i=x+1;i&lt;=y;i++){<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>n=i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>c=1;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>while(n-1)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>if(n%2!=0) n=3*n+1;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>else n=n/2;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>c++;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>if(c&gt;b) b=c;}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>printf(&quot;%d %d %d\n&quot;,g,h,b);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:SimSun;color:blue'>OneNoteTitle 1043: </span></b><b><span
style='font-size:16.0pt;font-family:SimSun;color:blue'>球</span></b><span
lang=EN-US style='font-size:16.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>13</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>16:57<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='mso-no-proof:
yes'><!--[if gte vml 1]><v:shape id="图片_x0020_3" o:spid="_x0000_i1046" type="#_x0000_t75"
 alt="算机生成了可选文字: Description &#10;设 圆 半 径 島 圆 柱 高 h 求 圆 周 长 &#10;、 圆 面 积 &#10;、 圆 琳 表 面 积 &#10;、 圆 琳 体 积 &#10;、 圆 柱 体 积 &#10;用 &#10;俞 入 据 ， 输 出 计 算 结 果 ， 输 出 时 要 求 文 字 说 明 ， 取 小 点 后 两 位 字 。 话 編 程 序 。 &#10;Input &#10;两 个 浮 点 鬢 r 和 h &#10;Output &#10;圆 周 长 Cl 、 圆 面 积 &#10;、 圆 琳 表 面 积 &#10;、 圆 琳 体 积 &#10;、 圆 柱 体 积 &#10;保 留 两 位 小 鬢 每 个 结 果 后 换 行 。 &#10;Sample Input &#10;Sample Output &#10;tn tn &#10;rU 12 rU &#10;6 "
 style='width:1237pt;height:490pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image003.png" o:title=" Description &#10;设 圆 半 径 島 圆 柱 高 h 求 圆 周 长 &#10;、 圆 面 积 &#10;、 圆 琳 表 面 积 &#10;、 圆 琳 体 积 &#10;、 圆 柱 体 积 &#10;用 &#10;俞 入 据 ， 输 出 计 算 结 果 ， 输 出 时 要 求 文 字 说 明 ， 取 小 点 后 两 位 字 。 话 編 程 序 。 &#10;Input &#10;两 个 浮 点 鬢 r 和 h &#10;Output &#10;圆 周 长 Cl 、 圆 面 积 &#10;、 圆 琳 表 面 积 &#10;、 圆 琳 体 积 &#10;、 圆 柱 体 积 &#10;保 留 两 位 小 鬢 每"/>
</v:shape><![endif]--><![if !vml]><img width=1237 height=490
src="ACM.fld/image003.png"
alt="算机生成了可选文字: Description &#10;设 圆 半 径 島 圆 柱 高 h 求 圆 周 长 &#10;、 圆 面 积 &#10;、 圆 琳 表 面 积 &#10;、 圆 琳 体 积 &#10;、 圆 柱 体 积 &#10;用 &#10;俞 入 据 ， 输 出 计 算 结 果 ， 输 出 时 要 求 文 字 说 明 ， 取 小 点 后 两 位 字 。 话 編 程 序 。 &#10;Input &#10;两 个 浮 点 鬢 r 和 h &#10;Output &#10;圆 周 长 Cl 、 圆 面 积 &#10;、 圆 琳 表 面 积 &#10;、 圆 琳 体 积 &#10;、 圆 柱 体 积 &#10;保 留 两 位 小 鬢 每 个 结 果 后 换 行 。 &#10;Sample Input &#10;Sample Output &#10;tn tn &#10;rU 12 rU &#10;6 "
v:shapes="图片_x0020_3"><![endif]></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>float r,h;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>double a=3.14;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>scanf(&quot;%f%f&quot;,&amp;r,&amp;h);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;C1=%.2f\n&quot;,2*r*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;Sa=%.2f\n&quot;,r*r*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;Sb=%.2f\n&quot;,4*r*r*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;Va=%.2f\n&quot;,4.0/3*a*r*r*r);<span
style='mso-spacerun:yes'>                   </span>//</span><span
style='font-size:10.5pt;font-family:SimSun'>必须为</span><span lang=EN-US
style='font-size:10.5pt;font-family:Calibri'>4.0</span><span style='font-size:
10.5pt;font-family:SimSun'>，如果是</span><span lang=EN-US style='font-size:10.5pt;
font-family:Calibri'>4</span><span style='font-size:10.5pt;font-family:SimSun'>会当成整型</span><span
lang=EN-US style='font-size:10.5pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;Vb=%.2f\n&quot;,r*r*a*h);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>return 0;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:Calibri'>OneNoteTitle 1044: </span><span style='font-size:
16.0pt;font-family:宋体'>℉℃</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>15</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>14:06<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='mso-no-proof:
yes'><!--[if gte vml 1]><v:shape id="图片_x0020_4" o:spid="_x0000_i1045" type="#_x0000_t75"
 alt="算机生成了可选文字: Description&#10;输入一个华氏温度，要求输出摄氏温度。公式为c=5吓一32)9输出要求有文字说明，取位2小数。&#10;Input&#10;一个华氏温度，浮点数&#10;output&#10;摄氏温度，浮点两位小数&#10;SampleInput&#10;一40&#10;Sampleoutput&#10;C＝一40。00"
 style='width:688pt;height:400pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image004.png" o:title=" Description&#10;输入一个华氏温度，要求输出摄氏温度。公式为c=5吓一32)9输出要求有文字说明，取位2小数。&#10;Input&#10;一个华氏温度，浮点数&#10;output&#10;摄氏温度，浮点两位小数&#10;SampleInput&#10;一40&#10;Sampleoutput&#10;C＝一40。00"/>
</v:shape><![endif]--><![if !vml]><img width=688 height=400
src="ACM.fld/image004.png"
alt="算机生成了可选文字: Description&#10;输入一个华氏温度，要求输出摄氏温度。公式为c=5吓一32)9输出要求有文字说明，取位2小数。&#10;Input&#10;一个华氏温度，浮点数&#10;output&#10;摄氏温度，浮点两位小数&#10;SampleInput&#10;一40&#10;Sampleoutput&#10;C＝一40。00"
v:shapes="图片_x0020_4"><![endif]></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>#include&lt;stdio.h&gt; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>int main() <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>{ <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;&nbsp;&nbsp;&nbsp;float F; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;&nbsp;&nbsp;&nbsp;scanf(&quot;%f&quot;,&amp;F);
<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;&nbsp;&nbsp;&nbsp;printf(&quot;c=%.2f&quot;,5*(F-32)/9);
<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri;color:blue'>OneNoteTitle 1048: </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>几位数，分别输出每一位数，倒序</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>15</span><span style='font-size:9.0pt;
font-family:SimSun;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>14:04<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='mso-no-proof:
yes'><!--[if gte vml 1]><v:shape id="图片_x0020_5" o:spid="_x0000_i1044" type="#_x0000_t75"
 alt="算机生成了可选文字: Description&#10;给出一个不多于5位的整数，要求1、求出它是几位数2、分别输出每一位数字3、按逆序输出各位数字，例如原数为321：应输出123&#10;Input&#10;一个不大于5位的数字&#10;output&#10;三行第一行位数第二行用空格分开的每个数字，注意最后一个数字后没有空格第三行按逆序输出这个数&#10;SampleInput&#10;12345&#10;Sampleoutput"
 style='width:865pt;height:435pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image005.png" o:title=" Description&#10;给出一个不多于5位的整数，要求1、求出它是几位数2、分别输出每一位数字3、按逆序输出各位数字，例如原数为321：应输出123&#10;Input&#10;一个不大于5位的数字&#10;output&#10;三行第一行位数第二行用空格分开的每个数字，注意最后一个数字后没有空格第三行按逆序输出这个数&#10;SampleInput&#10;12345&#10;Sampleoutput"/>
</v:shape><![endif]--><![if !vml]><img width=865 height=435
src="ACM.fld/image005.png"
alt="算机生成了可选文字: Description&#10;给出一个不多于5位的整数，要求1、求出它是几位数2、分别输出每一位数字3、按逆序输出各位数字，例如原数为321：应输出123&#10;Input&#10;一个不大于5位的数字&#10;output&#10;三行第一行位数第二行用空格分开的每个数字，注意最后一个数字后没有空格第三行按逆序输出这个数&#10;SampleInput&#10;12345&#10;Sampleoutput"
v:shapes="图片_x0020_5"><![endif]></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>#include &lt;math.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>int a,x,i,j,y,z,n;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>y=a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>for(j=0;j&lt;5;j++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>y=y/10;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'><span style='mso-spacerun:yes'>    </span>if(y&lt;10)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>n=j+2;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;%d\n&quot;,n);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>break;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>z=a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>for(i=n;i&gt;0;i--)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>for(j=0;j&lt;i;j++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>z=z/10;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>z=z%10;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'><span style='mso-spacerun:yes'>        </span>printf(&quot;%d&quot;,z+1);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>if(i==1)break;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot; &quot;);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>z=a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:11.0pt;font-family:
微软雅黑'>&nbsp;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;\n&quot;);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'><span style='mso-spacerun:yes'>   
</span>for(i=0;i&lt;n;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>x=a%10;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>printf(&quot;%d&quot;,x);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>if(i==(n-1))break;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>a=a/10;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:10.5pt;font-family:
Calibri'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;font-family:Calibri'>&nbsp;<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri;color:blue'>OneNoteTitle *</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'>1050: </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>最大公约数最小公倍数</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>19</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>14:00<o:p></o:p></span></p>

</div>

<div style='margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_6" o:spid="_x0000_i1043"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;输入两个正整数研口n，求其最大公约数和最小公倍数。&#10;Input&#10;两个整数&#10;Output&#10;最大公约数，最小公倍数&#10;SampleInput&#10;57&#10;Sampleoutput&#10;135"
 style='width:717pt;height:405pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image006.png" o:title=" Description&#10;输入两个正整数研口n，求其最大公约数和最小公倍数。&#10;Input&#10;两个整数&#10;Output&#10;最大公约数，最小公倍数&#10;SampleInput&#10;57&#10;Sampleoutput&#10;135"/>
</v:shape><![endif]--><![if !vml]><img width=717 height=405
src="ACM.fld/image006.png"
alt="算机生成了可选文字: Description&#10;输入两个正整数研口n，求其最大公约数和最小公倍数。&#10;Input&#10;两个整数&#10;Output&#10;最大公约数，最小公倍数&#10;SampleInput&#10;57&#10;Sampleoutput&#10;135"
v:shapes="图片_x0020_6"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=422
 style='width:422.2pt;margin-left:1.5pt;border-collapse:collapse;mso-yfti-tbllook:
 1184;mso-padding-alt:0cm 0cm 0cm 0cm' cols=3>
 <tr style='mso-yfti-irow:0;mso-yfti-firstrow:yes;height:.75pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  .75pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=264 valign=top style='width:263.75pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=42 valign=top style='width:42.2pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=116 valign=top style='width:116.2pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
 </tr>
 <tr style='mso-yfti-irow:1;height:22.1pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  22.1pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=264 rowspan=3 valign=top style='width:263.65pt;padding:0cm 0cm 0cm 0cm;
  height:22.1pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>#include &lt;stdio.h&gt;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>void main() <o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>{<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
  </span>int a, b, m, n ,t;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
  </span>scanf(&quot; %d %d&quot;, &amp;m, &amp;n);<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
  </span>a=m , b=n;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
  </span>while (0 != n)<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
  </span>{<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span
  style='mso-spacerun:yes'>        </span>t = m % n;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span
  style='mso-spacerun:yes'>        </span>m = n;<span
  style='mso-spacerun:yes'>    </span><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span
  style='mso-spacerun:yes'>        </span>n = t;<span
  style='mso-spacerun:yes'>    </span><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
  </span>}<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
  </span>printf(&quot;%d %d&quot;,m,a*b/m);<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>}<o:p></o:p></span></p>
  </td>
  <td width=42 valign=top style='width:42.2pt;padding:0cm 0cm 0cm 0cm;
  height:22.1pt'></td>
  <td width=116 valign=top style='width:116.2pt;padding:0cm 0cm 0cm 0cm;
  height:22.1pt'></td>
 </tr>
 <tr style='mso-yfti-irow:2;height:82.65pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  82.65pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=42 valign=top style='width:42.2pt;padding:0cm 0cm 0cm 0cm;
  height:82.65pt'></td>
  <td width=116 valign=top style='width:116.2pt;padding:0cm 0cm 0cm 0cm;
  height:82.65pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span style='font-size:10.5pt;
  font-family:宋体;color:#333333'>求最小公倍数，则先求最大公约数</span><span style='font-size:
  10.5pt;font-family:DengXian;mso-ascii-font-family:Arial;mso-fareast-font-family:
  DengXian;mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:Arial;
  mso-bidi-font-family:Arial;color:#333333'>，最后所有数之积再除</span><span
  style='font-size:10.5pt;font-family:宋体;color:#333333'>最大公约数</span><span
  style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:Arial;
  mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
  mso-hansi-font-family:Arial;mso-bidi-font-family:Arial;color:#333333'>即为最小公倍数</span><span
  lang=EN-US style='font-size:10.5pt;color:#333333'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span style='font-size:10.5pt;
  font-family:宋体;color:#333333'>求两个数最大公约数</span><span style='font-size:10.5pt;
  font-family:DengXian;mso-ascii-font-family:Arial;mso-fareast-font-family:
  DengXian;mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:Arial;
  mso-bidi-font-family:Arial;color:#333333'>原理：利用</span><span style='font-size:
  10.5pt;font-family:Arial;color:#333333'> </span><span style='font-size:10.5pt;
  font-family:宋体;color:#333333'>辗转相除法</span><span lang=EN-US style='font-size:
  10.5pt;color:#333333'><o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:3;mso-yfti-lastrow:yes;height:187.15pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  187.15pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=42 valign=top style='width:42.2pt;padding:0cm 0cm 0cm 0cm;
  height:187.15pt'></td>
  <td width=116 valign=top style='width:116.2pt;padding:0cm 0cm 0cm 0cm;
  height:187.15pt'></td>
 </tr>
</table>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1051: </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>统计中英文字母空格数字其他</span></b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>19</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>15:02<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_7" o:spid="_x0000_i1042"
 type="#_x0000_t75" alt="算机生成了可选文字: Dcscription&#10;输入一行字符，分别统计出其中英文字母、空格、数字和其他字符的个数。&#10;Input&#10;一行字符&#10;output&#10;统计值&#10;SampleInput&#10;aklsjflj123sadfglsu324asdfglu32oasdf/.&quot;;123&#10;Sampleoutput&#10;231624"
 style='width:782pt;height:400pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image007.png" o:title=" Dcscription&#10;输入一行字符，分别统计出其中英文字母、空格、数字和其他字符的个数。&#10;Input&#10;一行字符&#10;output&#10;统计值&#10;SampleInput&#10;aklsjflj123sadfglsu324asdfglu32oasdf/.&quot;;123&#10;Sampleoutput&#10;231624"/>
</v:shape><![endif]--><![if !vml]><img width=782 height=400
src="ACM.fld/image007.png"
alt="算机生成了可选文字: Dcscription&#10;输入一行字符，分别统计出其中英文字母、空格、数字和其他字符的个数。&#10;Input&#10;一行字符&#10;output&#10;统计值&#10;SampleInput&#10;aklsjflj123sadfglsu324asdfglu32oasdf/.&quot;;123&#10;Sampleoutput&#10;231624"
v:shapes="图片_x0020_7"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=1134
 style='width:40.0cm;margin-left:1.5pt;border-collapse:collapse;mso-yfti-tbllook:
 1184;mso-padding-alt:0cm 0cm 0cm 0cm' cols=3>
 <tr style='mso-yfti-irow:0;mso-yfti-firstrow:yes;height:.75pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  .75pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=540 valign=top style='width:540.0pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=54 valign=top style='width:54.0pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=540 valign=top style='width:540.0pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
 </tr>
 <tr style='mso-yfti-irow:1;height:18.0pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  18.0pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=540 valign=top style='width:540.0pt;padding:0cm 0cm 0cm 0cm;
  height:18.0pt'></td>
  <td width=54 valign=top style='width:54.0pt;padding:0cm 0cm 0cm 0cm;
  height:18.0pt'></td>
  <td width=540 rowspan=3 valign=top style='width:540.0pt;padding:0cm 0cm 0cm 0cm;
  height:18.0pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体;color:red'>#</span><span lang=EN-US
  style='font-size:16.0pt;font-family:Calibri;color:red'>include&lt;string.h&gt;</span><span
  lang=EN-US style='font-size:16.0pt;color:red'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>int i,</span><span lang=EN-US style='font-size:16.0pt;font-family:Calibri;
  color:red'>x,</span><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>a=0,b=0,c=0,d=0;</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>char ch[200];<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>gets(ch);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  Calibri;color:red'>x=strlen(ch);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(i=0;</span><span lang=EN-US style='font-size:16.0pt;font-family:Calibri;
  color:red'>x</span><span lang=EN-US style='font-size:16.0pt;font-family:宋体'>;i++)</span><span
  lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>if((ch[i]&gt;='a'&amp;&amp;ch[i]&lt;='z')||(ch[i]&gt;='A'&amp;&amp;ch[i]&lt;='Z'))
  a++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>else if(ch[i]&gt;='0'&amp;&amp;ch[i]&lt;='9') b++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>else if(ch[i]==' ') c++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>else d++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>printf(&quot;%d %d %d %d&quot;,a,b,c,d);<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>}<o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:2;height:312.7pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  312.7pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=540 valign=top style='width:540.0pt;padding:0cm 0cm 0cm 0cm;
  height:312.7pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>int i,a=0,b=0,c=0,d=0;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>char ch[200];<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>gets(ch);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(i=0;ch[i]!='\0';i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>if((ch[i]&gt;='a'&amp;&amp;ch[i]&lt;='z')||(ch[i]&gt;='A'&amp;&amp;ch[i]&lt;='Z'))
  a++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>else if(ch[i]&gt;='0'&amp;&amp;ch[i]&lt;='9') b++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>else if(ch[i]==' ') c++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>else d++;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>printf(&quot;%d %d %d %d&quot;,a,b,c,d);<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>}<o:p></o:p></span></p>
  </td>
  <td width=54 valign=top style='width:54.0pt;padding:0cm 0cm 0cm 0cm;
  height:312.7pt'></td>
 </tr>
 <tr style='mso-yfti-irow:3;mso-yfti-lastrow:yes;height:22.3pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  22.3pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=540 valign=top style='width:540.0pt;padding:0cm 0cm 0cm 0cm;
  height:22.3pt'></td>
  <td width=54 valign=top style='width:54.0pt;padding:0cm 0cm 0cm 0cm;
  height:22.3pt'></td>
 </tr>
</table>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1052: </span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>2+22+222+2222</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>19</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>15:34<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_8" o:spid="_x0000_i1041"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;求S,a--aa--～一aa…aaa（有n个：）之值，其中堤一个数字。例如：2+22十222十2222+22222(,5),n由键盘输入。并且已知，2.&#10;Input&#10;output&#10;和&#10;SampleInput&#10;Sampleoutput&#10;24690"
 style='width:890pt;height:415pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image008.png" o:title=" Description&#10;求S,a--aa--～一aa…aaa（有n个：）之值，其中堤一个数字。例如：2+22十222十2222+22222(,5),n由键盘输入。并且已知，2.&#10;Input&#10;output&#10;和&#10;SampleInput&#10;Sampleoutput&#10;24690"/>
</v:shape><![endif]--><![if !vml]><img width=890 height=415
src="ACM.fld/image008.png"
alt="算机生成了可选文字: Description&#10;求S,a--aa--～一aa…aaa（有n个：）之值，其中堤一个数字。例如：2+22十222十2222+22222(,5),n由键盘输入。并且已知，2.&#10;Input&#10;output&#10;和&#10;SampleInput&#10;Sampleoutput&#10;24690"
v:shapes="图片_x0020_8"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:9.95pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int a,x=0,b=1,c=0,i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=0;i&lt;a;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(i==0) x=2;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>else<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>b=b*10;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>c=c+b*2;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>x=x+c+2;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%d&quot;,x);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:"方正静蕾简体","serif";color:blue'>OneNoteTitle 1253:
</span></b><b><span style='font-size:16.0pt;font-family:DengXian;mso-ascii-font-family:
方正静蕾简体;mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:blue'>朋友数</span></b><span lang=EN-US
style='font-size:16.0pt;font-family:"方正静蕾简体","serif";color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2014</span><span style='font-size:9.0pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:gray'>年</span><span
lang=EN-US style='font-size:9.0pt;font-family:Calibri;color:gray'>8</span><span
style='font-size:9.0pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:gray'>月</span><span lang=EN-US
style='font-size:9.0pt;font-family:Calibri;color:gray'>21</span><span
style='font-size:9.0pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:gray'>日</span><span lang=EN-US
style='font-size:9.0pt;color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>8:58<o:p></o:p></span></p>

</div>

<div style='margin-top:21.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Description</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>220</span><span style='font-size:10.5pt;font-family:DengXian;
mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;mso-fareast-theme-font:
minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>的所有因数（不包括</span><span
lang=EN-US style='font-size:10.5pt;color:black'>220</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>本身）的和为</span><span lang=EN-US
style='font-size:10.5pt;color:black'>284</span><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>，即</span><span
lang=EN-US style='font-size:10.5pt;color:black'>1+2+4+5+10+11+20+22+44+55+110=284</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>。</span><span lang=EN-US
style='font-size:10.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>&nbsp;&nbsp; 284</span><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>的所有因数（不包括</span><span
lang=EN-US style='font-size:10.5pt;color:black'>284</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>本身）的和为</span><span lang=EN-US
style='font-size:10.5pt;color:black'>220</span><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>，即</span><span
lang=EN-US style='font-size:10.5pt;color:black'>1+2+4+71+142=220</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>。</span><span lang=EN-US
style='font-size:10.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>&nbsp; </span><span style='font-size:10.5pt;font-family:
DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>我们把</span><span
lang=EN-US style='font-size:10.5pt;color:black'>220</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>和</span><span lang=EN-US
style='font-size:10.5pt;color:black'>284</span><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>称为朋友数，编程求出</span><span
lang=EN-US style='font-size:10.5pt;color:black'>1----N</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>之间（包括</span><span lang=EN-US
style='font-size:10.5pt;color:black'>N</span><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>）的朋友数。</span><span
lang=EN-US style='font-size:10.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Input</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
10.5pt;color:black'>&nbsp;</span><span style='font-size:10.5pt;font-family:
DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>输入整数</span><span
lang=EN-US style='font-size:10.5pt;color:black'>N<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Output</span></b><span
lang=EN-US style='font-size:18.0pt;font-family:SimSun;color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>输出若干行每行一对朋友数，各行按升序排列，以空格分隔，行内数也按升序排列，注意</span><span
lang=EN-US style='font-size:10.5pt;color:black'>6</span><span style='font-size:
10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:
DengXian;mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;
color:black'>和本身</span><span lang=EN-US style='font-size:10.5pt;color:black'>(1+2+3)</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>，</span><span lang=EN-US
style='font-size:10.5pt;color:black'>28</span><span style='font-size:10.5pt;
font-family:DengXian;mso-ascii-font-family:方正静蕾简体;mso-fareast-font-family:DengXian;
mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:方正静蕾简体;color:black'>和本身</span><span
lang=EN-US style='font-size:10.5pt;color:black'>(1+2+4+7+14)</span><span
style='font-size:10.5pt;font-family:DengXian;mso-ascii-font-family:方正静蕾简体;
mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
mso-hansi-font-family:方正静蕾简体;color:black'>不算朋友数</span><span lang=EN-US
style='font-size:10.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Sample
Input</span></b><span lang=EN-US style='font-size:18.0pt;font-family:SimSun;
color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
13.5pt;color:black;background:#8DB8FF'>2000</span><span lang=EN-US
style='font-size:13.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:18.0pt;font-family:SimSun;color:blue;background:white'>Sample
Output</span></b><span lang=EN-US style='font-size:18.0pt;font-family:SimSun;
color:blue'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
13.5pt;color:black;background:#8DB8FF'>220 284 1184 1210</span><span
lang=EN-US style='font-size:13.5pt;color:black'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>#include &lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'><span style='mso-spacerun:yes'>   
</span>int a,b,c,x=1;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'><span style='mso-spacerun:yes'>   
</span>int i,j;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>while(x&lt;=a){<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>b=0;c=0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>for(i=1;i&lt;x;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>if(x%i==0) b=b+i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>for(j=1;j&lt;b;j++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>if(b%j==0) c=c+j;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>if(x==c&amp;&amp;c!=0&amp;&amp;x&lt;b) {<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>printf(&quot;%d %d\n&quot;,c,b);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>x++;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正静蕾简体","serif"'>&nbsp;<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:9.0pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:Calibri'>OneNoteTitle 1056:</span><span style='font-size:
16.0pt;font-family:宋体'>找出</span><span lang=EN-US style='font-size:16.0pt;
font-family:Calibri'>N</span><span style='font-size:16.0pt;font-family:宋体'>内所有完数</span><span
lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

</div>

<div style='margin-left:9.0pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>12</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>18</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>11:47<o:p></o:p></span></p>

</div>

<div style='margin-left:7.4pt;margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_9" o:spid="_x0000_i1040"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;一个数如果恰好等于它的因子之和，这个数就称为”完数‘，。例如，6的因子为1、2、3，而6司十2弓，因此6是’宪数”。编程序找出N之内的所有完数，并按下面格&#10;式输出其因子：&#10;Input&#10;Output&#10;?itsfaCtorSare???&#10;SampleInput&#10;1000&#10;Sampleoutput&#10;6itsfaCtorsarel&#10;28itsfaCtorSare&#10;4961七5fac七0r5dre&#10;3162124246"
 style='width:1021pt;height:471pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image009.png" o:title=" Description&#10;一个数如果恰好等于它的因子之和，这个数就称为”完数‘，。例如，6的因子为1、2、3，而6司十2弓，因此6是’宪数”。编程序找出N之内的所有完数，并按下面格&#10;式输出其因子：&#10;Input&#10;Output&#10;?itsfaCtorSare???&#10;SampleInput&#10;1000&#10;Sampleoutput&#10;6itsfaCtorsarel&#10;28itsfaCtorSare&#10;4961七5fac七0r5dre&#10;3162124246"/>
</v:shape><![endif]--><![if !vml]><img width=1021 height=471
src="ACM.fld/image009.png"
alt="算机生成了可选文字: Description&#10;一个数如果恰好等于它的因子之和，这个数就称为”完数‘，。例如，6的因子为1、2、3，而6司十2弓，因此6是’宪数”。编程序找出N之内的所有完数，并按下面格&#10;式输出其因子：&#10;Input&#10;Output&#10;?itsfaCtorSare???&#10;SampleInput&#10;1000&#10;Sampleoutput&#10;6itsfaCtorsarel&#10;28itsfaCtorSare&#10;4961七5fac七0r5dre&#10;3162124246"
v:shapes="图片_x0020_9"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include &lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    </span>int a,i,j,b=0;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
</span>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
</span>for(i=6;i&lt;a;i++)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    </span>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>        </span>b=0;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>       
</span>for(j=1;j&lt;=i/2;j++)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>        </span>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(i%j==0)
<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>b=b+j;<span style='mso-spacerun:yes'>  </span><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>        </span>}<span
style='mso-spacerun:yes'>   </span><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>        </span>if(b==i)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>           
</span>printf(&quot;%d its factors are &quot;,i);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>           
</span>for(j=1;j&lt;=i/2;j++)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>            </span>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(i%j==0) printf(&quot;%d &quot;,j);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>            </span>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;\n&quot;);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>        </span>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    </span>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1067:</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>方程的根</span></b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>24</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>13:49<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='mso-no-proof:
yes'><!--[if gte vml 1]><v:shape id="图片_x0020_10" o:spid="_x0000_i1039" type="#_x0000_t75"
 alt="算机生成了可选文字: Description&#10;求方程的根，用三个函数分别求当bZ一4ac大于0、等于O、和小于0时的根，并输出结果。从主函数输入。、b、。的值。&#10;Input&#10;abC&#10;output&#10;Xl=?x2=?&#10;SampleInput&#10;411&#10;Sampleoutput&#10;xl＝一0.125+0。4841xZ＝一0。125一0。4841"
 style='width:912pt;height:415pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image010.png" o:title=" Description&#10;求方程的根，用三个函数分别求当bZ一4ac大于0、等于O、和小于0时的根，并输出结果。从主函数输入。、b、。的值。&#10;Input&#10;abC&#10;output&#10;Xl=?x2=?&#10;SampleInput&#10;411&#10;Sampleoutput&#10;xl＝一0.125+0。4841xZ＝一0。125一0。4841"/>
</v:shape><![endif]--><![if !vml]><img width=912 height=415
src="ACM.fld/image010.png"
alt="算机生成了可选文字: Description&#10;求方程的根，用三个函数分别求当bZ一4ac大于0、等于O、和小于0时的根，并输出结果。从主函数输入。、b、。的值。&#10;Input&#10;abC&#10;output&#10;Xl=?x2=?&#10;SampleInput&#10;411&#10;Sampleoutput&#10;xl＝一0.125+0。4841xZ＝一0。125一0。4841"
v:shapes="图片_x0020_10"><![endif]></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;</span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>                      </span>//</span><span
style='font-size:16.0pt;font-family:宋体'>当</span><span lang=EN-US
style='font-size:16.0pt'>b^2-4ac&lt;0</span><span style='font-size:16.0pt;
font-family:宋体'>时也要输出值</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;math.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double a,b,c,x1,x2,x,y;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%lf%lf%lf&quot;,&amp;a,&amp;b,&amp;c);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if((b*b-4*a*c)&gt;0)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>x1=(-b+sqrt(b*b-4*a*c))/(2*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>x2=(-b-sqrt(b*b-4*a*c))/(2*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;x1=%.3lf x2=%.3lf&quot;,x1,x2);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if((b*b-4*a*c)==0)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>x1=-b/(2*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;x1=x2=%.3lf&quot;,x1);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if((b*b-4*a*c)&lt;0)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>x=-b/(2*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>y=(sqrt(4*a*c-b*b))/(2*a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt;text-indent:-11.95pt'><span lang=EN-US style='font-size:
16.0pt;mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_11" o:spid="_x0000_i1038"
 type="#_x0000_t75" alt="办事项" style='width:16pt;height:16pt;visibility:visible;
 mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image011.gif" o:title="办事项"/>
</v:shape><![endif]--><![if !vml]><img width=16 height=16
src="ACM.fld/image011.gif" alt=办事项 v:shapes="图片_x0020_11"><![endif]></span><span
lang=EN-US style='font-size:16.0pt'>&nbsp;</span><span lang=EN-US
style='font-size:16.0pt;font-family:宋体'>printf(&quot;x1=%.3lf+%.3lfi
x2=%.3lf-%.3lfi&quot;,x,y,x,y);</span><span lang=EN-US style='font-size:16.0pt;
font-family:Calibri'><span style='mso-spacerun:yes'>  </span>//</span><span
style='font-size:16.0pt;font-family:宋体'>蛋疼，后面加个</span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'>i</span><span style='font-size:
16.0pt;font-family:宋体'>。</span><span lang=EN-US style='font-size:16.0pt;
font-family:Calibri'><span style='mso-spacerun:yes'>    </span>= =!!!</span><span
lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:华文行楷;color:blue'>OneNoteTitle 1163: </span></b><b><span
style='font-size:16.0pt;font-family:华文行楷;color:blue'>二级：统计出现</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>$</span></b><b><span
style='font-size:16.0pt;font-family:华文行楷;color:blue'>的次数</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:华文行楷;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:华文行楷;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>17</span><span style='font-size:9.0pt;
font-family:华文行楷;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>21:36<o:p></o:p></span></p>

</div>

<div style='margin-top:11.1pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_12" o:spid="_x0000_i1037"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;编制程序，统计文本stdin中字符S出现的次数，并将结果写入文件stdout&#10;Input&#10;字符文本&#10;output&#10;＄次数&#10;SampleInput&#10;as$dfkjhkjkjdhf&#10;asdfkj$lskdfj&#10;wer1jwe1rjo$wie&#10;Sampleoutput"
 style='width:655pt;height:439pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image012.png" o:title=" Description&#10;编制程序，统计文本stdin中字符S出现的次数，并将结果写入文件stdout&#10;Input&#10;字符文本&#10;output&#10;＄次数&#10;SampleInput&#10;as$dfkjhkjkjdhf&#10;asdfkj$lskdfj&#10;wer1jwe1rjo$wie&#10;Sampleoutput"/>
</v:shape><![endif]--><![if !vml]><img width=655 height=439
src="ACM.fld/image012.png"
alt="算机生成了可选文字: Description&#10;编制程序，统计文本stdin中字符S出现的次数，并将结果写入文件stdout&#10;Input&#10;字符文本&#10;output&#10;＄次数&#10;SampleInput&#10;as$dfkjhkjkjdhf&#10;asdfkj$lskdfj&#10;wer1jwe1rjo$wie&#10;Sampleoutput"
v:shapes="图片_x0020_12"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=789
 style='width:789.1pt;margin-left:1.5pt;border-collapse:collapse;mso-yfti-tbllook:
 1184;mso-padding-alt:0cm 0cm 0cm 0cm' cols=3>
 <tr style='mso-yfti-irow:0;mso-yfti-firstrow:yes;height:.75pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  .75pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=274 valign=top style='width:274.4pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=248 valign=top style='width:247.55pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=267 valign=top style='width:267.1pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
 </tr>
 <tr style='mso-yfti-irow:1;height:8.85pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  8.85pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=274 valign=top style='width:274.4pt;padding:0cm 0cm 0cm 0cm;
  height:8.85pt'></td>
  <td width=248 valign=top style='width:247.55pt;padding:0cm 0cm 0cm 0cm;
  height:8.85pt'></td>
  <td width=267 rowspan=3 valign=top style='width:267.1pt;padding:0cm 0cm 0cm 0cm;
  height:8.85pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>#include&lt;stdio.h&gt;</span><span
  lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
  style='mso-spacerun:yes'>             </span><span style='color:red'>//</span></span><span
  style='font-size:16.0pt;font-family:DengXian;mso-ascii-font-family:隶书;
  mso-fareast-font-family:DengXian;mso-fareast-theme-font:minor-fareast;
  mso-hansi-font-family:隶书;color:red'>错误</span><span lang=EN-US
  style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>{<span
  style='mso-spacerun:yes'>    </span><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>char a[1000];<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>int i,b=0;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>for(i=0;;i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>scanf(&quot;%c&quot;,&amp;a[i]);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>for(i=0;;i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  Calibri'><span style='mso-spacerun:yes'>       </span></span><span
  lang=EN-US style='font-size:16.0pt;font-family:"隶书","serif"'>if(a[i]=='
  ')break;</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>if(a[i]=='$')b=b+1;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>printf(&quot;%d&quot;,b);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>return 0;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>}<o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:2;height:291.95pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  291.95pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=274 valign=top style='width:274.4pt;padding:0cm 0cm 0cm 0cm;
  height:291.95pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>#include&lt;stdio.h&gt;</span><span
  lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
  style='mso-spacerun:yes'>         </span><span
  style='mso-spacerun:yes'>      </span>//</span><span style='font-size:16.0pt;
  font-family:DengXian;mso-ascii-font-family:隶书;mso-fareast-font-family:DengXian;
  mso-fareast-theme-font:minor-fareast;mso-hansi-font-family:隶书'>正确</span><span
  lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>{<span
  style='mso-spacerun:yes'>    </span><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>char a[1000];<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>int i,b=0;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>for(i=0;;i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>scanf(&quot;%c&quot;,&amp;a[i]);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  Calibri'><span style='mso-spacerun:yes'>       </span></span><span
  lang=EN-US style='font-size:16.0pt;font-family:"隶书","serif"'>if(a[i]=='
  ')break;</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>if(a[i]=='$')b=b+1;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>printf(&quot;%d&quot;,b);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  "隶书","serif"'>return 0;<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:"隶书","serif"'>}<o:p></o:p></span></p>
  </td>
  <td width=248 valign=top style='width:247.55pt;padding:0cm 0cm 0cm 0cm;
  height:291.95pt'></td>
 </tr>
 <tr style='mso-yfti-irow:3;mso-yfti-lastrow:yes;height:53.3pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  53.3pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=274 valign=top style='width:274.4pt;padding:0cm 0cm 0cm 0cm;
  height:53.3pt'></td>
  <td width=248 valign=top style='width:247.55pt;padding:0cm 0cm 0cm 0cm;
  height:53.3pt'></td>
 </tr>
</table>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:Calibri'>OneNoteTitle *</span><span lang=EN-US
style='font-size:16.0pt;font-family:华文行楷'> </span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'>1165:</span><span
style='font-size:16.0pt;font-family:华文行楷'>二级：删除字符</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:华文行楷;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:华文行楷;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>18</span><span style='font-size:9.0pt;
font-family:华文行楷;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>13:47<o:p></o:p></span></p>

</div>

<div style='margin-top:9.15pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_13" o:spid="_x0000_i1036"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;编制函数del--char&#10;函数原型为voiddel--char(char*,char)：函数的功能是删除好旨向的字符串中值为ch的字符，例如从字符串”scADe尸中删除’A’后，字符串为”scDe尸。&#10;Input&#10;需要删除的字符ch&#10;需要处理的字符串&#10;output&#10;处理后的字符串&#10;SampleInput&#10;A&#10;ASCADef&#10;Sampleoutput&#10;SCDef"
 style='width:1018pt;height:499pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image013.png" o:title=" Description&#10;编制函数del--char&#10;函数原型为voiddel--char(char*,char)：函数的功能是删除好旨向的字符串中值为ch的字符，例如从字符串”scADe尸中删除’A’后，字符串为”scDe尸。&#10;Input&#10;需要删除的字符ch&#10;需要处理的字符串&#10;output&#10;处理后的字符串&#10;SampleInput&#10;A&#10;ASCADef&#10;Sampleoutput&#10;SCDef"/>
</v:shape><![endif]--><![if !vml]><img width=1018 height=499
src="ACM.fld/image013.png"
alt="算机生成了可选文字: Description&#10;编制函数del--char&#10;函数原型为voiddel--char(char*,char)：函数的功能是删除好旨向的字符串中值为ch的字符，例如从字符串”scADe尸中删除’A’后，字符串为”scDe尸。&#10;Input&#10;需要删除的字符ch&#10;需要处理的字符串&#10;output&#10;处理后的字符串&#10;SampleInput&#10;A&#10;ASCADef&#10;Sampleoutput&#10;SCDef"
v:shapes="图片_x0020_13"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>#include&lt;stdio.h&gt; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>#include&lt;string.h&gt; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>void del_char(char *a,char ch); <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>int main() <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>{ <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>char *p,ch,a1[100]; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>p=a1;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>scanf(&quot;%c&quot;,&amp;ch);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>getchar();<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>  </span><span
style='mso-spacerun:yes'>  </span>scanf(&quot;%s&quot;,p); <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>del_char(p,ch); <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>return 0;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>} <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>void del_char(char *a,char ch)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>{ <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>int i,j,flag; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>int jj;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>jj=strlen(a);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>for(i=0;i&lt;jj;i++) <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正舒体","serif"'>{ <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>       
</span>if(*(a+i)==ch) <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正舒体","serif"'>{ <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>           
</span>flag=i; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>           
</span>j=strlen(a);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>           
</span>for(;flag&lt;j;flag++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正舒体","serif"'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正舒体","serif"'><span style='mso-spacerun:yes'>           
</span>*(a+flag)=*(a+flag+1);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正舒体","serif"'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>       
</span>*(a+flag)='\0'; <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>       
</span>i--;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正舒体","serif"'>}<span style='mso-spacerun:yes'>   </span><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
"方正舒体","serif"'>} <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'><span style='mso-spacerun:yes'>   
</span>puts(a); <o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:"方正舒体","serif"'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:18.0pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1166: </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>二级：分支求方程（</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>sin</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>，</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>sqrt</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>）</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:18.0pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>26</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>13:56<o:p></o:p></span></p>

</div>

<div style='margin-left:16.4pt;margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_14" o:spid="_x0000_i1035"
 type="#_x0000_t75" alt="算机生成了可选文字: 题目描述&#10;编程，输入n后：输入n个数，根据下式计算并输出，值。&#10;,&#10;IX‘一SlllXX＜一2&#10;产毛&#10;2x十x一2&lt;=x&lt;=2&#10;、心妙冲x~&#10;＊输出保留两位小数&#10;输入&#10;n个数&#10;输出&#10;样例输入&#10;11"
 style='width:994pt;height:598pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image014.png" o:title=" 题目描述&#10;编程，输入n后：输入n个数，根据下式计算并输出，值。&#10;,&#10;IX‘一SlllXX＜一2&#10;产毛&#10;2x十x一2&lt;=x&lt;=2&#10;、心妙冲x~&#10;＊输出保留两位小数&#10;输入&#10;n个数&#10;输出&#10;样例输入&#10;11"/>
</v:shape><![endif]--><![if !vml]><img width=994 height=598
src="ACM.fld/image014.png"
alt="算机生成了可选文字: 题目描述&#10;编程，输入n后：输入n个数，根据下式计算并输出，值。&#10;,&#10;IX‘一SlllXX＜一2&#10;产毛&#10;2x十x一2&lt;=x&lt;=2&#10;、心妙冲x~&#10;＊输出保留两位小数&#10;输入&#10;n个数&#10;输出&#10;样例输入&#10;11"
v:shapes="图片_x0020_14"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;math.h&gt;</span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>             </span>//</span><span style='font-size:
16.0pt;font-family:宋体'>其实不用它也可以</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int p,x[10],i,j;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double a[10],b=1.0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%d&quot;,&amp;p);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(j=0;j&lt;p;j++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scanf(&quot;%d&quot;,&amp;x[j]);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(j=0;j&lt;p;j++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>    </span>if(x[j]&lt;-2)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>    </span>a[j]=x[j]*x[j]-sin(x[j]);</span><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>       </span>//</span><span style='font-size:16.0pt;
font-family:宋体'>三角函数直接用，如果是角度需要写成</span><span lang=EN-US style='font-size:16.0pt;
font-family:Calibri'>sin(x*3.14/180)</span><span lang=EN-US style='font-size:
16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>   
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;printf(&quot;%.2lf\n&quot;,a[j]);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(x[j]&gt;=-2&amp;&amp;x[j]&lt;=2)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>    </span>b=1;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>    </span>for(i=0;i&lt;x[j];i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>   
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b=b*2;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>   
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;printf(&quot;%.2lf\n&quot;,b+x[j]);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(x[j]&gt;2)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;printf(&quot;%.2lf\n&quot;,sqrt(x[j]*x[j]+x[j]+1));<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1173: </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>二级：</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>x</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>的</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>n</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>次方</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>25</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>15:05<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_15" o:spid="_x0000_i1034"
 type="#_x0000_t75" alt="算机生成了可选文字: 题目描述&#10;输入一个正数呀口一个正整数n，求下列算式的值。要求顶一个调用2个函数：fact(n）计算n的阶乘；m押。w(x,n）计算x的可欠幕（即xn)，两个函数的返回值类型是double。&#10;x一户2卜护I3！十…十（一l)n-lxntn!&#10;x输出保留4位小数。&#10;输入&#10;输出&#10;数列和&#10;样例输入&#10;2。03&#10;样例输出&#10;1。3333"
 style='width:1120pt;height:500pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image015.png" o:title=" 题目描述&#10;输入一个正数呀口一个正整数n，求下列算式的值。要求顶一个调用2个函数：fact(n）计算n的阶乘；m押。w(x,n）计算x的可欠幕（即xn)，两个函数的返回值类型是double。&#10;x一户2卜护I3！十…十（一l)n-lxntn!&#10;x输出保留4位小数。&#10;输入&#10;输出&#10;数列和&#10;样例输入&#10;2。03&#10;样例输出&#10;1。3333"/>
</v:shape><![endif]--><![if !vml]><img width=1120 height=500
src="ACM.fld/image015.png"
alt="算机生成了可选文字: 题目描述&#10;输入一个正数呀口一个正整数n，求下列算式的值。要求顶一个调用2个函数：fact(n）计算n的阶乘；m押。w(x,n）计算x的可欠幕（即xn)，两个函数的返回值类型是double。&#10;x一户2卜护I3！十…十（一l)n-lxntn!&#10;x输出保留4位小数。&#10;输入&#10;输出&#10;数列和&#10;样例输入&#10;2。03&#10;样例输出&#10;1。3333"
v:shapes="图片_x0020_15"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:37.45pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt; </span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>     </span>//</span><span style='font-size:16.0pt;
font-family:宋体'>比较麻烦</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>double fact(double a)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>float x=1.0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=1;i&lt;=a;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>x=x*i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>return x;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>double mypow(double b,int x)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double a=1.0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=0;i&lt;x;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>a=a*b;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>return a;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int b,i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double x=0,a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%lf&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%d&quot;,&amp;b);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=1;i&lt;=b;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(i%2!=0)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{x=x+mypow(a,i)/fact(i);}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>else <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{x=x-mypow(a,i)/fact(i);}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%.4lf&quot;,x);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1174: </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>二级：分支求方程（绝对值，</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>n</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>次方）</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>25</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>22:33<o:p></o:p></span></p>

</div>

<div style='margin-top:9.2pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='mso-no-proof:
yes'><!--[if gte vml 1]><v:shape id="图片_x0020_16" o:spid="_x0000_i1033" type="#_x0000_t75"
 alt="算机生成了可选文字: 题目描述&#10;计算并输出下列分段函数f(x）的值。可以调用数学库函数：平方根函数：qrt()，绝对值函数fab:(）和幕函数p。，(）。&#10;、、．月了&#10;XX&#10;入叹！&#10;输J&#10;保留2位小数&#10;输入&#10;输出&#10;f(x)&#10;样例输入&#10;5&#10;样例输出&#10;15。00"
 style='width:887pt;height:571pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image016.png" o:title="(）和幕函数p。，(）。&#10;、、．月了&#10;XX&#10;入叹！&#10;输J&#10;保留2位小数&#10;输入&#10;输出&#10;f(x)&#10;样例输入&#10;5&#10;样例输出&#10;15。00"/>
</v:shape><![endif]--><![if !vml]><img width=887 height=571
src="ACM.fld/image016.png"
alt="算机生成了可选文字: 题目描述&#10;计算并输出下列分段函数f(x）的值。可以调用数学库函数：平方根函数：qrt()，绝对值函数fab:(）和幕函数p。，(）。&#10;、、．月了&#10;XX&#10;入叹！&#10;输J&#10;保留2位小数&#10;输入&#10;输出&#10;f(x)&#10;样例输入&#10;5&#10;样例输出&#10;15。00"
v:shapes="图片_x0020_16"><![endif]></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;math.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>double fabsn(double x)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(x&gt;=0) a=x;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(x&lt;0) a=-x;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>return a;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>double sqrtn(double x)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(x&gt;=0&amp;&amp;x&lt;2) a=sqrt(x+1);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if((x&gt;=2&amp;&amp;x&lt;4)) a=(x+2)*(x+2)*(x+2)*(x+2)*(x+2);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>return a;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>double powa(double x)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>a=2.0*x+5.0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>return a;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double x;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%lf&quot;,&amp;x);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(x&lt;0) printf(&quot;%.2lf&quot;,fabsn(x));<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if((x&gt;=0&amp;&amp;x&lt;2)||(x&gt;=2&amp;&amp;x&lt;4))
printf(&quot;%.2lf&quot;,sqrtn(x));</span><span lang=EN-US style='font-size:
16.0pt;font-family:Calibri'><span style='mso-spacerun:yes'>    </span><span
style='color:red'>//</span></span><span style='font-size:16.0pt;font-family:
宋体;color:red'>这里</span><span lang=EN-US style='font-size:16.0pt;font-family:
Calibri;color:red'>sqrtn</span><span style='font-size:16.0pt;font-family:宋体;
color:red'>千万不可以写成</span><span lang=EN-US style='font-size:16.0pt;font-family:
Calibri;color:red'>sqrt</span><span style='font-size:16.0pt;font-family:宋体;
color:red'>！！</span><span lang=EN-US style='font-size:16.0pt;font-family:Calibri;
color:red'>sqrt</span><span style='font-size:16.0pt;font-family:宋体;color:red'>求平方根</span><span
lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(x&gt;=4) printf(&quot;%.2lf&quot;,powa(x));<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1180: C</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>二级辅导<span lang=EN-US>-</span>温度转换</span></b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>19</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>16:03<o:p></o:p></span></p>

</div>

<div style='margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_17" o:spid="_x0000_i1032"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;输入一个华氏温度，要求输出摄氏温度。公式为&#10;c＝旦（F一32)&#10;9'&#10;保留两位小数&#10;Input&#10;Output&#10;SamplcInput&#10;一40&#10;Sampleoutput&#10;一40。00"
 style='width:676pt;height:438pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image017.png" o:title=" Description&#10;输入一个华氏温度，要求输出摄氏温度。公式为&#10;c＝旦（F一32)&#10;9'&#10;保留两位小数&#10;Input&#10;Output&#10;SamplcInput&#10;一40&#10;Sampleoutput&#10;一40。00"/>
</v:shape><![endif]--><![if !vml]><img width=676 height=438
src="ACM.fld/image017.png"
alt="算机生成了可选文字: Description&#10;输入一个华氏温度，要求输出摄氏温度。公式为&#10;c＝旦（F一32)&#10;9'&#10;保留两位小数&#10;Input&#10;Output&#10;SamplcInput&#10;一40&#10;Sampleoutput&#10;一40。00"
v:shapes="图片_x0020_17"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double a,b;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%lf&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>b=5.0/9.0*(a-32.0);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%.2lf&quot;,b);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:18.0pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri;color:blue'>OneNoteTitle **</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'>1083: </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>三个字符串从大到小排序</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:18.0pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>26</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>15:39<o:p></o:p></span></p>

</div>

<div style='margin-left:16.4pt;margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_18" o:spid="_x0000_i1031"
 type="#_x0000_t75" alt="算机生成了可选文字: 题目描述&#10;输入三个字符串，按由小到大的顺序输出&#10;输入&#10;3行字符串&#10;输出&#10;按照从小到大输出成3行&#10;样例输入&#10;样例输出&#10;abC&#10;afq&#10;Cde"
 style='width:915pt;height:499pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image018.png" o:title=" 题目描述&#10;输入三个字符串，按由小到大的顺序输出&#10;输入&#10;3行字符串&#10;输出&#10;按照从小到大输出成3行&#10;样例输入&#10;样例输出&#10;abC&#10;afq&#10;Cde"/>
</v:shape><![endif]--><![if !vml]><img width=915 height=499
src="ACM.fld/image018.png"
alt="算机生成了可选文字: 题目描述&#10;输入三个字符串，按由小到大的顺序输出&#10;输入&#10;3行字符串&#10;输出&#10;按照从小到大输出成3行&#10;样例输入&#10;样例输出&#10;abC&#10;afq&#10;Cde"
v:shapes="图片_x0020_18"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;string.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>char a[100],b[100],c[100],t[100];<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>scanf(&quot;%s%s%s&quot;,a,b,c);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>if(strcmp(a,b)&gt;0)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{ strcpy(t,a);strcpy(a,b);strcpy(b,t); }<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>if(strcmp(a,c)&gt;0)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{ strcpy(t,a);strcpy(a,c);strcpy(c,t); }<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>if(strcmp(b,c)&gt;0)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{ strcpy(t,b);strcpy(b,c);strcpy(c,t); }<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>printf(&quot;%s\n%s\n%s\n&quot;,a,b,c);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>return 0;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1087: C</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>语言程序设计教程（第三版）课后习题<span
lang=EN-US>10.7</span></span></b><span lang=EN-US style='font-size:16.0pt;
font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>24</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>18:14<o:p></o:p></span></p>

</div>

<div style='margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_19" o:spid="_x0000_i1030"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;有一字符串，包含叮个字符。写一函数，将此字符串中从第m个字符开始的全部字符复制成为另一个字符串。&#10;Input&#10;数字n一行字符串数字m&#10;output&#10;从m开始的子串&#10;SampleInput&#10;6&#10;abCdef&#10;3&#10;Sampleoutput&#10;Cdef"
 style='width:927pt;height:548pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image019.png" o:title=" Description&#10;有一字符串，包含叮个字符。写一函数，将此字符串中从第m个字符开始的全部字符复制成为另一个字符串。&#10;Input&#10;数字n一行字符串数字m&#10;output&#10;从m开始的子串&#10;SampleInput&#10;6&#10;abCdef&#10;3&#10;Sampleoutput&#10;Cdef"/>
</v:shape><![endif]--><![if !vml]><img width=927 height=548
src="ACM.fld/image019.png"
alt="算机生成了可选文字: Description&#10;有一字符串，包含叮个字符。写一函数，将此字符串中从第m个字符开始的全部字符复制成为另一个字符串。&#10;Input&#10;数字n一行字符串数字m&#10;output&#10;从m开始的子串&#10;SampleInput&#10;6&#10;abCdef&#10;3&#10;Sampleoutput&#10;Cdef"
v:shapes="图片_x0020_19"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int a,b,i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>char str[30];<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>getchar();</span><span lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>               </span><span style='color:red'><span
style='mso-spacerun:yes'> </span>//</span></span><span style='font-size:16.0pt;
font-family:宋体;color:red'>把</span><span lang=EN-US style='font-size:16.0pt;
font-family:Calibri;color:red'>scanf</span><span style='font-size:16.0pt;
font-family:宋体;color:red'>的回车符吃掉，</span><span lang=EN-US style='font-size:16.0pt;
font-family:Calibri;color:red'>gets</span><span style='font-size:16.0pt;
font-family:宋体;color:red'>不会直接跳出</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>gets(str);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%d&quot;,&amp;b);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=b-1;i&lt;a;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%c&quot;,str[i]);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>？？<span lang=EN-US>1188: </span>阶乘数列</span></b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>21</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>14:04<o:p></o:p></span></p>

</div>

<div style='margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_20" o:spid="_x0000_i1029"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;求l+2!+3!+4!＋…＋30！。&#10;科学计数法，保留两位小数。"
 style='width:572pt;height:124pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image020.png" o:title=" Description&#10;求l+2!+3!+4!＋…＋30！。&#10;科学计数法，保留两位小数。"/>
</v:shape><![endif]--><![if !vml]><img width=572 height=124
src="ACM.fld/image020.png"
alt="算机生成了可选文字: Description&#10;求l+2!+3!+4!＋…＋30！。&#10;科学计数法，保留两位小数。" v:shapes="图片_x0020_20"><![endif]></span><span
lang=EN-US style='mso-fareast-font-family:"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:26.8pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>void main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int j,i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>double sum1=0,sum2=0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>i=30;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for (i=30;i&gt;0;i--)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>sum1=1;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for (j=i;j&gt;0 ;j--)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:11.0pt;font-family:
微软雅黑'>&nbsp;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>sum1=sum1*j;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>sum2=sum2+sum1;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf (&quot;%.2e\n&quot;,sum2);</span><span lang=EN-US style='font-size:
16.0pt;font-family:Calibri'><span style='mso-spacerun:yes'>  </span>//</span><span
style='font-size:16.0pt;font-family:宋体'>指数形式输出</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
11.0pt;font-family:微软雅黑'>&nbsp;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>} <o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:57.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span style='font-size:16.0pt;
font-family:宋体'>单循环<span lang=EN-US><o:p></o:p></span></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>long int a,i,s=0,p=1;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;</span><span style='font-size:16.0pt;font-family:宋体'>输入数字：<span
lang=EN-US>&quot;);<o:p></o:p></span></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%ld&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=1;i&lt;=a;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>p=p*i;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>s=s+p;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>} <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%ld&quot;,s);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:Calibri'>OneNoteTitle 1190</span><span style='font-size:
16.0pt;font-family:宋体'>：质数因子</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>12</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>18</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>11:37<o:p></o:p></span></p>

</div>

<div style='margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_21" o:spid="_x0000_i1028"
 type="#_x0000_t75" alt="算机生成了可选文字: 题目描述&#10;输入一个正整数，输出它的所有质数的因子（如180的质数因子为2、2、3、3、5)&#10;输入&#10;输出&#10;样例输入&#10;180&#10;样例输出&#10;22335"
 style='width:659pt;height:353pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image021.png" o:title=" 题目描述&#10;输入一个正整数，输出它的所有质数的因子（如180的质数因子为2、2、3、3、5)&#10;输入&#10;输出&#10;样例输入&#10;180&#10;样例输出&#10;22335"/>
</v:shape><![endif]--><![if !vml]><img width=659 height=353
src="ACM.fld/image021.png"
alt="算机生成了可选文字: 题目描述&#10;输入一个正整数，输出它的所有质数的因子（如180的质数因子为2、2、3、3、5)&#10;输入&#10;输出&#10;样例输入&#10;180&#10;样例输出&#10;22335"
v:shapes="图片_x0020_21"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:19.5pt;margin-top:35.0pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int c,i,b=2,a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>scanf(&quot;%d&quot;,&amp;a);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>c=a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=2;i&lt;=a;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(c%b==0) <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{ <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>c=c/b; <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>printf(&quot;%d &quot;,b); <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>} &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>else b++;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle </span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>？<span lang=EN-US>1191: </span></span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri;color:blue'>x+y=1333</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>21</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>15:13<o:p></o:p></span></p>

</div>

<div style='margin-top:22.55pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_22" o:spid="_x0000_i1027"
 type="#_x0000_t75" alt="算机生成了可选文字: Dcscription&#10;已知三位整数湃口乡两足x朽二1333，其中x的个位数是y的百位数，y的个位数是x的百位数，它们的十位数一样。求满足这样条件的湃口y。&#10;Input&#10;output&#10;419一914=1333&#10;按X从小到大输出，每个等式一行"
 style='width:932pt;height:238pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image022.png" o:title=" Dcscription&#10;已知三位整数湃口乡两足x朽二1333，其中x的个位数是y的百位数，y的个位数是x的百位数，它们的十位数一样。求满足这样条件的湃口y。&#10;Input&#10;output&#10;419一914=1333&#10;按X从小到大输出，每个等式一行"/>
</v:shape><![endif]--><![if !vml]><img width=932 height=238
src="ACM.fld/image022.png"
alt="算机生成了可选文字: Dcscription&#10;已知三位整数湃口乡两足x朽二1333，其中x的个位数是y的百位数，y的个位数是x的百位数，它们的十位数一样。求满足这样条件的湃口y。&#10;Input&#10;output&#10;419一914=1333&#10;按X从小到大输出，每个等式一行"
v:shapes="图片_x0020_22"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=900
 style='width:900.35pt;margin-left:1.5pt;border-collapse:collapse;mso-yfti-tbllook:
 1184;mso-padding-alt:0cm 0cm 0cm 0cm' cols=3>
 <tr style='mso-yfti-irow:0;mso-yfti-firstrow:yes;height:.75pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  .75pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=356 valign=top style='width:356.2pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=76 valign=top style='width:75.65pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
  <td width=468 valign=top style='width:468.35pt;padding:0cm 0cm 0cm 0cm;
  height:.75pt'></td>
 </tr>
 <tr style='mso-yfti-irow:1;height:271.1pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  271.1pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=356 rowspan=2 valign=top style='width:356.2pt;padding:0cm 0cm 0cm 0cm;
  height:271.1pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;</span><span
  lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
  style='mso-spacerun:yes'>             </span>//</span><span style='font-size:
  16.0pt;font-family:宋体'>正确</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>int i,j,a,b;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(i=100;i&lt;1000;i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(j=100;j&lt;1000;j++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>a=i/10;b=j/10;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>if(i/100==j%10&amp;&amp;i%10==j/100&amp;&amp;a%10==b%10&amp;&amp;i+j==1333)printf(&quot;%d+%d=1333\n&quot;,i,j);<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>}<o:p></o:p></span></p>
  </td>
  <td width=76 valign=top style='width:75.65pt;padding:0cm 0cm 0cm 0cm;
  height:271.1pt'></td>
  <td width=468 valign=top style='width:468.35pt;padding:0cm 0cm 0cm 0cm;
  height:271.1pt'>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;</span><span
  lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
  style='mso-spacerun:yes'>             </span>//</span><span style='font-size:
  16.0pt;font-family:宋体'>错误</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>int i,j;<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(i=100;i&lt;1000;i++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>for(j=100;j&lt;1000;j++)<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>{<o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>if(i/100==j%10&amp;&amp;i%10==j/100</span><span lang=EN-US
  style='font-size:16.0pt;font-family:黑体;color:red'>&amp;&amp;<b>(i/10)%10==(j/10)%10</b></span><span
  lang=EN-US style='font-size:16.0pt;font-family:宋体'>&amp;&amp;i+j==1333)printf(&quot;%d+%d=1333\n&quot;,i,j);</span><span
  lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}</span><span lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
  style='mso-spacerun:yes'>         </span><span style='color:red'>//</span></span><span
  style='font-size:16.0pt;font-family:宋体;color:red'>不知道为啥红色部分不能这样写</span><span
  lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>
  <p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
  margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
  宋体'>}<o:p></o:p></span></p>
  <p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US
  style='font-size:16.0pt;font-family:宋体'>}<o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:2;mso-yfti-lastrow:yes;height:41.55pt'>
  <td width=1 valign=top style='width:.75pt;padding:0cm 0cm 0cm 0cm;height:
  41.55pt'>
  <p><span lang=EN-US style='font-size:1.0pt'>&nbsp;<o:p></o:p></span></p>
  </td>
  <td width=76 valign=top style='width:75.65pt;padding:0cm 0cm 0cm 0cm;
  height:41.55pt'></td>
  <td width=468 valign=top style='width:468.35pt;padding:0cm 0cm 0cm 0cm;
  height:41.55pt'></td>
 </tr>
</table>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:1.5pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri;color:blue'>OneNoteTitle ***</span></b><b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'>1193:</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>寻找完数</span></b><span
lang=EN-US style='font-size:16.0pt;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:1.5pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>21</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>15:57<o:p></o:p></span></p>

</div>

<div style='margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_23" o:spid="_x0000_i1026"
 type="#_x0000_t75" alt="算机生成了可选文字: Description&#10;输出1一1000的完数（l不是完数）&#10;Input&#10;output&#10;卜1十2十3&#10;SampleInput&#10;Sampleoutput&#10;6=l+2+3&#10;28=1+2+4+7+14&#10;496=l+2+4+8+16+31+62+124+248"
 style='width:625pt;height:402pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image023.png" o:title=" Description&#10;输出1一1000的完数（l不是完数）&#10;Input&#10;output&#10;卜1十2十3&#10;SampleInput&#10;Sampleoutput&#10;6=l+2+3&#10;28=1+2+4+7+14&#10;496=l+2+4+8+16+31+62+124+248"/>
</v:shape><![endif]--><![if !vml]><img width=625 height=402
src="ACM.fld/image023.png"
alt="算机生成了可选文字: Description&#10;输出1一1000的完数（l不是完数）&#10;Input&#10;output&#10;卜1十2十3&#10;SampleInput&#10;Sampleoutput&#10;6=l+2+3&#10;28=1+2+4+7+14&#10;496=l+2+4+8+16+31+62+124+248"
v:shapes="图片_x0020_23"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-left:10.5pt;margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#define N 100<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main(void)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    </span>int
i,j,k=0,yinzi[N];<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>   
</span>for(i=2;i&lt;1001;i++)<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>    </span>{<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>       </span></span><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>  </span></span><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>yinzi[99]=0;</span><span lang=EN-US style='font-size:
16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>       
</span>for(j=1;j&lt;i;j++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
Calibri'><span style='mso-spacerun:yes'> </span></span><span lang=EN-US
style='font-size:16.0pt;font-family:宋体'>{</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if(i%j==0) {yinzi[k++]=j;}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
Calibri'><span style='mso-spacerun:yes'> </span></span><span lang=EN-US
style='font-size:16.0pt;font-family:宋体'>}</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
Calibri'><span style='mso-spacerun:yes'>         </span></span><span
lang=EN-US style='font-size:16.0pt;font-family:宋体'>for(j=0;j&lt;k;j++)
{yinzi[99]+=yinzi[j];}</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>       </span></span><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'> </span></span><span lang=EN-US style='font-size:16.0pt;
font-family:宋体'>if(i==yinzi[99])</span><span lang=EN-US style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>       </span></span><span
lang=EN-US style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'> </span>{</span><span lang=EN-US style='font-size:
16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>           
</span>printf(&quot;%d=&quot;,i);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>           
</span>for(j=0;j&lt;k;j++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
Calibri'><span style='mso-spacerun:yes'>           </span></span><span
lang=EN-US style='font-size:16.0pt;font-family:宋体'>{</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>                
</span>printf(&quot;%d&quot;,yinzi[j]);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>  </span></span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>   </span></span><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>if(j==k-1)break;</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:108.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'>  </span></span><span lang=EN-US
style='font-size:16.0pt;font-family:Calibri'><span
style='mso-spacerun:yes'>    </span></span><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>printf(&quot;+&quot;);</span><span lang=EN-US
style='font-size:16.0pt'><o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'> </span>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'><span style='mso-spacerun:yes'> </span>printf(&quot;\n&quot;);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'><span style='mso-spacerun:yes'>        </span>k=0;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<div style='border-width:100%'>

<div>

<div style='margin-left:18.0pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><b><span lang=EN-US
style='font-size:16.0pt;font-family:宋体;color:blue'>OneNoteTitle 1350:</span></b><b><span
style='font-size:16.0pt;font-family:宋体;color:blue'>删除非英文的字符后输出</span></b><span
lang=EN-US style='font-size:16.0pt;font-family:宋体;color:blue'><o:p></o:p></span></p>

</div>

<div style='margin-left:18.0pt;margin-top:2.75pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>2013</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>年</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>11</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>月</span><span lang=EN-US style='font-size:9.0pt;
font-family:Calibri;color:gray'>26</span><span style='font-size:9.0pt;
font-family:宋体;color:gray'>日</span><span lang=EN-US style='font-size:9.0pt;
color:gray'><o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
9.0pt;font-family:Calibri;color:gray'>9:27<o:p></o:p></span></p>

</div>

<div style='margin-left:16.4pt;margin-top:9.2pt'>

<p class=MsoNormal><span lang=EN-US style='mso-fareast-font-family:"Times New Roman";
mso-no-proof:yes'><!--[if gte vml 1]><v:shape id="图片_x0020_24" o:spid="_x0000_i1025"
 type="#_x0000_t75" alt="算机生成了可选文字: 题目描述&#10;编一个程序，输入一个字符串，将组成字符串的所有非英文字母的字符删除后输出。&#10;输入&#10;一个字符串，长度不超过8仓个字符&#10;输出&#10;册！掉非英文字母后的字符串。&#10;样例输入&#10;abcl23+xyz.5&#10;样例输出&#10;abcxyz"
 style='width:679pt;height:417pt;visibility:visible;mso-wrap-style:square'>
 <v:imagedata src="ACM.fld/image024.png" o:title=" 题目描述&#10;编一个程序，输入一个字符串，将组成字符串的所有非英文字母的字符删除后输出。&#10;输入&#10;一个字符串，长度不超过8仓个字符&#10;输出&#10;册！掉非英文字母后的字符串。&#10;样例输入&#10;abcl23+xyz.5&#10;样例输出&#10;abcxyz"/>
</v:shape><![endif]--><![if !vml]><img width=679 height=417
src="ACM.fld/image024.png"
alt="算机生成了可选文字: 题目描述&#10;编一个程序，输入一个字符串，将组成字符串的所有非英文字母的字符删除后输出。&#10;输入&#10;一个字符串，长度不超过8仓个字符&#10;输出&#10;册！掉非英文字母后的字符串。&#10;样例输入&#10;abcl23+xyz.5&#10;样例输出&#10;abcxyz"
v:shapes="图片_x0020_24"><![endif]></span><span lang=EN-US style='mso-fareast-font-family:
"Times New Roman"'><o:p></o:p></span></p>

</div>

<div style='margin-top:9.85pt'>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;stdio.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>#include&lt;string.h&gt;<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>int main()<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>char ch[80];<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>int i,j,a;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>gets(ch);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>a=strlen(ch);<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>for(i=0,j=0;i&lt;a;i++)<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>if((ch[i]&lt;='z'&amp;&amp;ch[i]&gt;='a')|| (ch[i] &gt;='A' &amp;&amp;
ch[i] &lt;= 'Z')) <o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>{<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>ch[j]=ch[i];<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:81.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>j++;<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:54.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>}<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>ch[j]='\0';<o:p></o:p></span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:27.0pt;
margin-bottom:.0001pt'><span lang=EN-US style='font-size:16.0pt;font-family:
宋体'>puts(ch);<o:p></o:p></span></p>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US style='font-size:
16.0pt;font-family:宋体'>}<o:p></o:p></span></p>

</div>

</div>

</div>

<div>

<p style='margin:0cm;margin-bottom:.0001pt'><span lang=EN-US>&nbsp;</span></p>
<p style='margin:0cm;margin-bottom:.0001pt'><span style='font-size:9.0pt;
font-family:宋体;color:#969696'>已使用<span lang=EN-US> Microsoft OneNote 2010 </span>创建<span
lang=EN-US><br>
</span>一个用于存放所有笔记和信息的位置<span lang=EN-US><o:p></o:p></span></span></p>

</div>

</div>

</body>

</html>