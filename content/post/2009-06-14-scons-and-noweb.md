+++
author = "enrico_spinielli"
blogger_id = "tag:blogger.com,1999:blog-1947405997418753543.post-287329049599051800"
blogger_orig_url = "http://ongiantsshoulders.blogspot.com/2009/06/scons-and-noweb.html"
comments = true
date = "2009-06-14"
modified_time = "2009-07-07T21:47:13.133+02:00"
tags = ["scons", "latex", "python", "noweb"]
title = "Scons and noweb"
url = "/2009/06/14/scons-and-noweb/"

+++

I was curious to see how I could integrate noweb and Scons.

You can download my little Sconstruct for this,
[Sconstruct.example](http://enrico.spinielli.googlepages.com/Sconstruct.example).
It defines two builders. NoWeave is used to produce TeX or LaTeX documents,
while NoTangle extracts the non-document artefacts, i.e. programs, config files,
scripts ... It also includes productions for generating a sample program about
Ackermann function: 


{{< highlight python "style=emacs" >}}
	ackdoc  = env.NoWeave('ack.tex', 'ack.nw')
	ackcode = env.NoTangle('ack.py', 'ack.nw')
	acktest = env.NoTangle('ackTest.py', 'ack.nw')
{{< / highlight >}}


The noweb source is [ack.nw](http://enrico.spinielli.googlepages.com/ack.nw) and
the companion BibTeX file is
[ack.bib](http://enrico.spinielli.googlepages.com/ack.bib)

It contains the doc chunks describing the function, the source code chunck for
the relevant Python code and the code chunk for the unit test.

You can try it out executing


{{< highlight bash >}}
	$ scons -f Sconstruct.example
{{< / highlight >}}


You will get the following artefacts,
[ack.py](http://enrico.spinielli.googlepages.com/ack.py),
[ack.tex](http://enrico.spinielli.googlepages.com/ack.tex),
[ackTest.py](http://enrico.spinielli.googlepages.com/ackTest.py) and
[ack.pdf](http://enrico.spinielli.googlepages.com/ack.pdf) 

Remember to run BibTeX first...
