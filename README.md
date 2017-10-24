---
layout: post
title: LaTex your Resume 
tags: [resume, latex, github]
---

Note:  this is a copy of a post from [my blog](https://hackersupply.org).  Since Githubs SEO is likely stronger than mine, I'm putting this post here to help anyone who might stumble on this, and want to impliment something similar for themselves.  

One of the things that I like about linux, is that GUIs don't need to slow me down.  I can do most anything via the CLI, and likely do it way faster than I ever could clicking around a clunky interface.  With that said, when it comes time to update my resume,  it generally takes me all of about 5 or 10 minutes.  I imagine doing the same via Libre Office would take much longer.

I keep my resume in LaTex format on a personal git server. 

LaTex (pronounced '/lah-tek/' or '/lay-tek/' is a very powerful document preparation system.  Its generally used in Mathematics and Science fields where formulas and equasions are not readily typed with a standad keyboard. It could probably be argued that using it for my boring resume is a bit overkill.

An all encompassing LaTex Tutorial would be a huge undertaking.  However, after finishing this you should be able to generate your own technical resume from a LaTex source file and a template that looks similar to [mine](https://doubleday.io/nick-doubleday.pdf). 

First, we're going to need to install the necessary LaTex packages. 

```
Arch Linux: 
pacman -S texlive-bin texi2pdf

Ubuntu/Debian: 
apt-get install texlive-full 

Fedora/CentOS/RedHat

yum install 'texlive-*'
```

Please note, we are doing a full installation of the TexLive suite.  This might be overkill for what you want. I use LaTex for a number of things, and just install all of it.  If you want you can take the time to find out specifically what tex packages are needed.  

Now that we have LaTex, clone the repo containing my resume.  I've uploaded a static copy to github for you to use

```
git clone https://github.com/nick2day/tex_resume.git
```

Inside you should find 2 files,  nick-doubleday.tex and res.cls. 

The res.cls file is the actual template that makes the resume look like it does.  You won't need to edit that (at least in the scope of this tutorial).  

What you will need to edit is nick-doubleday.tex.  Use your favorite text editor to replace all my information with yours.

Once everything is updated with your info, we can generate the PDF Resume

```
#Arch: 
texi2pdf nick-doubleday.tex

#Ubuntu/Debian: 
pdflatex nick-doubleday.tex

#Fedora/CentOS/RedHat: 
pdflatex nick-doubleday.tex
```bash

On Arch, the output looks like this:

```
╭─nick6508@racktop ~/git/tex_resume  ‹master*› 
╰─$ texi2pdf nick-doubleday.tex 
This is pdfTeX, Version 3.14159265-2.6-1.40.18 (TeX Live 2017/Arch Linux) (preloaded format=pdflatex)
 restricted \write18 enabled.
entering extended mode
LaTeX2e <2017-04-15>
Babel <3.12> and hyphenation patterns for 84 language(s) loaded.
(./nick-doubleday.tex (/home/nick6508/git/tex_resume/res.cls
Document Style `res' <26 Sep 89>.
Document Class: res 2000/05/19 v1.4b Resume class
(/usr/share/texmf-dist/tex/latex/base/article.cls
Document Class: article 2014/09/29 v1.4h Standard LaTeX document class
(/usr/share/texmf-dist/tex/latex/base/size10.clo))
No auxiliary output files.

) (/usr/share/texmf-dist/tex/latex/psnfss/helvet.sty
(/usr/share/texmf-dist/tex/latex/graphics/keyval.sty))
No file nick-doubleday.aux.
(/usr/share/texmf-dist/tex/latex/base/omscmr.fd)
Overfull \hbox (0.44992pt too wide) in paragraph at lines 36--37
[]\OT1/cmr/m/n/10 Building the first con-tainer-ized PaaS/IaaS for in-ter-nal a
p-pli-ca-tions at Rackspace 

Overfull \hbox (0.56215pt too wide) in paragraph at lines 39--40
[]\OT1/cmr/m/n/10 Developing and en-forc-ing stan-dards to tran-si-tion Rackspa
ce from De-vOps model
[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] [2] )
(see the transcript file for additional information)</usr/share/texmf-dist/font
s/type1/public/amsfonts/cm/cmbx10.pfb></usr/share/texmf-dist/fonts/type1/public
/amsfonts/cm/cmbx12.pfb></usr/share/texmf-dist/fonts/type1/public/amsfonts/cm/c
mr10.pfb></usr/share/texmf-dist/fonts/type1/public/amsfonts/cm/cmsl10.pfb></usr
/share/texmf-dist/fonts/type1/public/amsfonts/cm/cmsy10.pfb></usr/share/texmf-d
ist/fonts/type1/public/amsfonts/cm/cmti10.pfb>
Output written on nick-doubleday.pdf (2 pages, 89037 bytes).
Transcript written on nick-doubleday.log

```
If you kept the original n ame, you should now have a file named nick-doubleday.pdf

Sometimes you'll need to add a couple lines to make sure that some section of your resume doesn't get split on the page break.  To generate line breaks in LaTEx, you use `//`.  For example the line
`{\sl Freelancer} \hfill        April 2008 - Jan 2012 \\` generates a line break after the text `Jan 2012`.  

### Benefits of a version controlled Resume
Aside from being quicker to update,  there are a few other benefits to having your resume as a flat text LaTex source file.  Namely, that is version control.  

Due to it being version controlled, its very easy to roll back any changes, or even revert your resume to how it appeared 10 versions ago if you would like. Sometimes though, you might tweak your resume so that its tailored specifically for a company you're applying for.  For this, you can create a branch.  You can create tons of branches if you want,  one for each job type you would like to apply for.  

Once its in git,  you can also automate against it.  For instance,  my [personal site](https://doubleday.io) contains a link to my resume.  That resume is always up-to date, as a push to git triggers an automated build of my resume in pdf form, that gets uploaded to the website.  

I'm sure there are many other benefits as well.  If you're doing anything interesting with this, please let me know!   
