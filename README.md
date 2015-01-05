# Eagle Tools

From <http://bardagjy.com/?p=563>

I revisited the tools I <a href="http://bardagjy.com/?p=524">previously</a> put together to process EagleCAD files for manufacture. I extended my export tools to generate all the gerbers required for most major board houses (like <a href="http://www.4pcb.com/">Advanced Circuits</a>) and PNGs required for <a href="http://kokompe.cba.mit.edu/dist/">Fab modules</a> (used by the <a href="http://fab.cba.mit.edu/content/processes/PCB/modela2.html">Media Lab's Modella</a>). 

As icing on the cake, I also wrote a python script to generate csv parts lists that can be easily uploaded to Digikey.

So, the scripts (a Makefile and a python script, eagle_parts) can export:
<ul>
	<li> <a href="http://www.barebonespcb.com/">Barebones</a> compatible gerbers </li>
	<li> <a href="http://www.4pcb.com/">Advanced Circuits</a> (and most other board houses) compatible gerbers </li>
	<li> <a href="http://kokompe.cba.mit.edu/dist/">MIT CBA Fab Module</a> compatible PNGs </li>
	<li> <a href="http://www.digikey.com/">Digikey</a> compatible csv parts lists </li>
</ul>

These tools will work best under Unixy operating systems, maybe someone can get it to work under Cygwin, I've used them under OSX. They depend on a few pretty usual command line tools including GNU make, git, and python and a few unusual tools like <a href="http://www.cadsoftusa.com/">EAGLE</a>, <a href="http://gerbv.sourceforge.net/">gerbv</a>, and <a href="http://www.imagemagick.org/">imagemagick</a>. 

All of these tools should be easy to install via repositories (like macports, fink, apt etc). The only wrinkle under OSX is making EAGLE usable from the command line which can be easily enabled with a softlink

<code>ln -s /Applications/EAGLE/EAGLE.app/Contents/MacOS/EAGLE /usr/bin/eagle</code>

To install the tools, first grab a copy of my eagle_tools git repo

<code>git clone git://bardagjy.com/eagle_tools</code>

In my repo, you'll get three directories; cam, dru, and export. In the cam directory I've shared my Advanced Circuits and Barebones cam files. In the dru directory I've shared my design rules for the Modella and Advanced Circuits. In the export directory is a sample makefile and a python script eagle_parts for exporting Digikey compatible csv parts lists.

To use the export tools, copy the makefile into your project directory and change the PROJECT variable to the name of your project. I assume the your .brd and .sch files are the name of your project, though this is not enforced by EAGLE (I should probably fix this in the future). 

I prefer to make a softlink from my git repo to /usr/bin

<code>ln -s eagle_tools/export/eagle_parts /usr/bin/eagle_parts</code>

While I'm at it, I link the repo cam and dru files to the system installed cam and dru files.

That's it! Feel free to ask questions in the comments.