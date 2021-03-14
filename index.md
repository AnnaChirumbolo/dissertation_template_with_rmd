![tutheaderbl](https://user-images.githubusercontent.com/43357858/111071816-2a280400-84d8-11eb-8b1e-8cb70e58f2dc.png)

## Write your dissertation in Rmarkdown!

*Created by Anna*

### Tutorial Aims

1. Understanding the advantages of using `Rmarkdown` for writing pdf documents, focusing on writing your dissertation;

2. Learning how to create the template for the main page, and appending all the other sections to it;

3. Using LaTex for embellishing the pdf output and functioning as a supplement to Markdown; 

4. Becoming familiar with `knitr` and `kableExtra` packages. 

### Steps:

* <a href="#section1"> 1. The "main" Rmarkdown document.</a>

* <a href="#subsect1">a) The front page.</a>
* <a href="#subsect2">b) The abstract.</a>

* <a href="#section2"> 2. "Child" documents.</a>

* <a href="#subsect3"> Example: the Appendix.</a>

* <a href="#section4"> 4. Some final adjustments.</a>

*  <a href="#section5"> 5. Let's merge!</a>

* <a href="#section6"> 6. Final tips. </a>

<a name="section1"></a>

## 1. The "main" Rmarkdown document. 

When you write a document, whether it's an essay, or a scientific report, or your undergraduate dissertation, it is going to be structured in different sections. 

In the scientific world, these sections consist of: an introduction, methods, results, discussion, and a list of your references. If we consider a published paper or a thesis, these also contain an abstract, perhaps a section with abbreviations, and at the end present a section with supplementary information, or an appendix. 

As the aim of this tutorial is to successfully write your dissertation with Rmarkdown, it is useful to consider the number of sections necessary for your output, and to *avoid writing everything in one single .Rmd document*. 

In fact, for sake of easier read and better organisation, but also faster upload of the final pdf, we are going to create multiple .Rmd files, corresponding to the main sections of the dissertation. We are then going to merge them together, within the "mother" document. 

So, first thing we are going to do is create the main .Rmd file. 
Here, we are going to set the first page of your dissertation and we are going to **link** all the other .Rmd documents containing the different sections. 
In this file, we are also going to set the general formatting rules (written in **LaTex**), which are going to apply to the entire document.

**Open Rstudio and create a new .Rmd file** by clicking on the blank sheet with the green plus one the left-hand side of the interface. 

<img width="1280" alt="open_md" src="https://user-images.githubusercontent.com/43357858/111072154-91928380-84d9-11eb-8dd7-6cee402bd889.png">

Once you have created a new Rmarkdown document, leave title and author blank (you don't want these to appear at the top of your pdf) and select PDF as the Default Output Format. Click OK and let's start writing in the new file.

<img width="1280" alt="rmd_opened" src="https://user-images.githubusercontent.com/43357858/111072170-a40cbd00-84d9-11eb-9f9f-c34388939c3e.png">

You will see at the top a section called YAML header, delimited by three hyphens (---). The header embeds the information that you have just given (blank for the title, no author and pdf_document as your desired output), and allows you to set the rules that are going to be applied throught the document (as well as the **linked** documents). This header will not show in the output. 

Erase the text, as we are going to be writing our own, but keep the YAML header (IT'S ESSENTIAL!) and also the first grey banner or **code chunk**. Your file should look like this: 

<img width="1280" alt="clean_rmd" src="https://user-images.githubusercontent.com/43357858/111072215-df0ef080-84d9-11eb-9501-dc599a64cafd.png">

<a name="subsect1"></a>

### a) The front page

The School of Geosciences provides standard formatting rules for the undergraduate dissertation document, and we are going to set the file according to them (these are as of 2020, if they have changed edit them accordingly). 

Let's create the **front page** of the dissertation. It's an important one, as it's going to make the first great impression of your work!

The front page requires all elements to be **centred**. We are going to start using some **LaTex syntax** to do so. Write the following under the first code chunk:

````
\begin{centering}

\end{centering}
````

This is written in LaTex. We are defining a space in the document, **within** which anything we will write will be centered on the page. 

In between these lines, we are going to specify a 3 cm spacing from the top of the page, to then insert the first element: the university logo. 

````
\vspace{3cm}
````

Undearneath the *vertical spacing (vspace)* function, add a new code chunk by selecting on the icon "insert" and clicking on "R". 

Inside it, write

````
```{r uni_logo, echo=F, out.width="20%"}
knitr::include_graphics("img/uniedlogo.png")
```
````

This way, the image of the UoE logo is going to appear at the top of the page. 

<img width="1280" alt="uni_logo_chunk" src="https://user-images.githubusercontent.com/43357858/111072428-de2a8e80-84da-11eb-8f36-ed9c5c323576.png">

As you can see, I have **named** the code chunk "uni_logo", making it easier to retrieve the chunk later on, when there are going to be many more. 

*Echo = False* will only show the output of the code inside the code chunk, not the code itself. 

*Out.width* is a feature for images and figures, in particular the percentage width that the image will occupy out of the total white space in the pdf document. 

[**Knitr**](https://yihui.org/knitr/) is the only most important package used in Rmarkdown, to help you create elegant, flexible and fast report generation. 

You can retrieve the image of the university logo with the function *include_graphics()*.

1 cm distant from the logo, we need to add the name of the university and that of your department, As an example: 

````
\vspace{1cm}

\Large 
{\bf The University Of Edinburgh}

\Large
{\bf School Of Geosciences}
````

You recall the *\vspace* function from above. **\Large** sets all text below it to be of larger font, and \bf which sets the text within curly brackets to **bold**.

**\Large** is a font changing command, and the pt size it reflects is often determined by the document class itself. Here is an overview of the values for the standard classes. 

````
Command             10pt    11pt    12pt
\tiny               5       6       6
\scriptsize         7       8       8
\footnotesize       8       9       10
\small              9       10      10.95
\normalsize         10      10.95   12
\large              12      12      14.4
\Large              14.4    14.4    17.28
\LARGE              17.28   17.28   20.74
\huge               20.74   20.74   24.88
\Huge               24.88   24.88   24.88
````

It's time to add the *title* of your dissertation! I have written mine below just as an example.

````
\vspace{1cm}

\Large

\doublespacing
{\bf COMPARISON OF TOP-DOWN AND BOTTOM-UP APPROACHES ON SPECIFIC LEAF AREA PATTERNS, \\AT GLOBAL, LATITUDINAL, AND BIOME SCALES}
````

As you might have figured, adding \doublespacing will double the space between lines of text. By wrapping a specific part of your text within curly brackets and adding the function \bf at the start, you will specify that **only** that part of the text will need be in bold. 

The university guidelines specify to have the title **all capitalised**. And finally, the `\\` sign will break the text onto a new line (just like \n for a string in R code!).

To finish up the front page we need to add author, degree and date! 

````
\vspace{1 cm}

\normalsize
\singlespacing
By 

\vspace{0.5 cm}

\Large

{\bf ANNA CHIRUMBOLO}

\vspace{1.5 cm}

in partial fulfilment of the requirement \\for the degree of BSc with Honours \\in Ecological and Environmental Sciences 

\vspace{1.5 cm}

\normalsize
mm yy
````

Again, as a matter of formatting guidance, I added some specified spacing in between the lines of text that follow the thesis title. 

**Remember** that rmarkdown will remember any input you last gave it, and to change it agaom for the following lines you need to specify the new function!
In fact, by changing the font back to \normalsize you input the .Rmd file to go back to a 'normal' font (12 pt), since the last input you gave it was to be \Large. 

We have created the front page, which should look like this. 

<img width="583" alt="front_page_pdf" src="https://user-images.githubusercontent.com/43357858/111072920-f3082180-84dc-11eb-9a68-1101e7f55977.png">

<a name="subsect2"></a>

### b) Abstract

We can add the Abstract on a new page, by specifying this LaTex command (remember to start writing outside of the centering command from now on). 

````
\newpage
````

Anything you'll write or insert after this command will appear on a new page. This way you have control over the distribution of your content. 

In the new page, write the following

````
\begin{centering}

{\bf Abstract}

\end{centering}

\spacing{1.5}

(the spacing is set to 1.5) 

no more than 250 words for the abstract

- a description of the research question/knowledge gap – what we know and what we don’t know
- how your research has attempted to fill this gap
- a brief description of the methods
- brief results
- key conclusions that put the research into a larger context
````

The title "Abstract" is centered and bold, while the spacing between lines of text is set to 1.5. 

<img width="1280" alt="abstract" src="https://user-images.githubusercontent.com/43357858/111073019-5eea8a00-84dd-11eb-86b0-0a0a5313c76c.png">

I have included main guidelines for writing an abstract, which should come useful to you when writing it. 

<img width="1083" alt="abstract_output" src="https://user-images.githubusercontent.com/43357858/111073008-54c88b80-84dd-11eb-8f86-614a8f07a82d.png">

<a name="section2"></a>

## 2. "Child" documents.

Looking good! 

The front page of the dissertation is ready, and so is your abstract. 

Now we need to add the different sections of your dissertation, which we'll create on separate .Rmd files as I mentioned at the beginning of this tutorial. These .rmd files will behave as **'children'** to the main file, which we have worked on so far.

In the main document, paste the following after the section on the abstract.

````
\newpage

```{r acknowledgments, child='acknowledgments.Rmd'}
```

\newpage

```{r intro, child = 'introduction.Rmd'}
```

\newpage

```{r methods, child = 'methods.Rmd'}
```

\newpage

```{r results, child = 'results.Rmd'}
```

\newpage 

```{r discussion, child = 'discussion.Rmd'}
```

\newpage 

```{r conclusion, child = 'conclusion.Rmd'}
```

\newpage 

```{r biblio, child = 'bibliography.Rmd'}
```

\newpage 

```{r appendix, child = 'appendix.Rmd'}
```
````

As you can see, we've just added a code chunk for each section of your dissertation. The "child" feature specified in the code chunk options, links the **content** of this other .Rmd file to the main one. This means that once you'll knit the main document, the **content from each of the child documents will be pasted and marged into one, final pdf**. 

However, remember to make sure you've created **all** .Rmd files that you have **specified** in your main file, and **check the spelling**! As you can imagine, non-existing or mispelled files which you will try to link to the main document will result in an error, whenever you will try to knit to pdf. 

To speed things up a little, I have created the files already and you can see them in the [repository](https://github.com/AnnaChirumbolo/dissertation_template_with_rmd). Knitting the document now, you should see how the content from each has been pasted into one main document.

You should now have a 10-page document, with each section of the dissertation appearing on a new page. The structure is coming along nicely! Well done!

<a href="subsect3"></a>

### Example: the appendix. 

As an example, we are going to structure a section that we do not often work with, because it is optional, albeit very useful - the appendix. You might decide to include it or not in your final dissertation, but what you're going to learn from now on applies to any section of your document. 

However, there are some general rules that apply to the appendix section. Appendices: 

1. Appear the end of the document, often after references; 

2. You should create one appendix for each topic, e.g. additional tables, additional figures, code, etc. Each should start on a new page; 

3. If there are multiple appendices in your document, there should be labelled with letters, and usually accompanied by a title that clarifies their content; 

4. Appendices are also included in the table of contents at the beginning of the main document. 

We are going to follow these formatting rules and we are going to explore three types of appendices: additional tables, additional figures and code (used for programming during your research). 

#### A) Additional tables

Opening the appendix.Rmd document, you will see it already contains some text I had added. 

````
# Appendix(ces)

## Appendix A: additional tables 

Insert content for additional tables here.

\newpage

## Appendix B: additional figures

Insert content for additional figures here. 

\newpage

## Appendix C: code

Insert code (if any) used during your dissertation work here. 
````

We will start with **Appendix A: additional tables**. 

We are going to add a new chunk with the following code, to start coding live within the .Rmd. 

We are opening a .csv file containing information on the Atlantic puffins (*Fratercula arctica*) species trend and temperature information from 1979 until 2008, in Norway.  

````
```{r setup and tidy, include = F}
library(knitr)  # for dynamic report generation
library(kableExtra) # to build complex HTML or 'LaTex' tables
library(tidyverse) # for data manipulation

puffins_t <- read.csv("./data/puffins_temp.csv")
                      # to open the file puffins_temp.csv

puffins_t <- puffins_t %>%
  rename("Year" = year, "Country list" = Country.list,
         "Population trend" = pop_trend, "ID" = id,
         "Mean max. T (°C)" = mean_tmax, "Mean min. T (°C)" = mean_tmin)  
            # A bit of data transformation! "New name" = Old.name
```
````

*Note: `include=F` in the `{}` makes sure that neither code chunk nor output are shown in the pdf output.*

If you have never used the `tidyverse` package before don't worry - it is not part of the learning objectives for this tutorial. If you want to learn about the Tidyverse, do this <a href="https://ourcodingclub.github.io/2017/03/20/seecc.html" target="____blank">Coding Club tutorial</a>.

Now, the data set is almost presentable and ready to be inserted in a table. There are still other details, like number of decimals to be fixed, that `knitr::kable()` function helps fixing.

`kableExtra` is a package that uses `kable()` and *pipes* from the `Tidyverse` package, to build complex and professional tables. We are going to use one example for the sake of this tutorial, but if you wish to explore further on the large variety of features that kableExtra can offer, have a look at its <a href="https://cran.r-project.org/web/packages/kableExtra/kableExtra.pdf" target="____blank">manual</a>.[^4]. Moreover, kableExtra is often combined with `viridisLite` package, for using smoother <a href="https://cran.r-project.org/web/packages/viridis/vignettes/intro-to-viridis.html" target="____blank">colour scales</a>.

Copy the following code chunk and run it (make sure it is spaced from the one above).

~~~~
```{r table1, echo=F}
puffins_t %>%
  slice(1:10) %>%   # the table is going to show only the first 10 lines (a sample of the data set)
  kable(digits = 2) %>% # each value has 2 decimal digits
  kable_styling(full_width = F, # the width of the table is not fit to the width of the page
                position = "center", font_size = 10)  # table settings with the kableExtra package
```			
~~~~

You can notice that the table has now appeared after the chunk and in the 'Viewer' tab on the bottom-right panel.

![app_table](https://user-images.githubusercontent.com/43357858/111074272-8abc3e80-84e2-11eb-992a-8c311a2315f5.jpg)

**REMEMBER: the tables output in Rstudio Viewer are in html format. This means that on pdf will have a slightly different look, particularly when it comes to colours chosen. Make sure you specify these colors and check the output (kableExtra was initially made for hmtl, not pdf outputs).**

Moving on to **Appendix B: additional figures**. We are going to use the same data on the Atlantic Puffins. 

As we did for the table, we could output our figure by coding directly inside the code chunk, and specifying **include = F** in the code chunk options, to only display the figure and not the code that generated it, in the pdf. 

Otherwise, **knitr** package provides us with options to add pre-saved figures. We've already used this function when adding the university logo in our main page. 

As an example, we are displaying mean temperature change between 1979 and 2008 in Norway. 

~~~~
```{r path-to-folder plots fixed size, echo = TRUE, out.height="40%", fig.show='hold', fig.align="center",  fig.cap="Additional images in Appendix B"}

include_graphics("img/meant_plot.png") 
```
~~~~

- <sub>`fig.align` defines the alignment of figures in the output;</sub>

- <sub>`fig.cap` adds the figure caption at the bottom;</sub>

- <sub>The `list.files()` function lists the files present in a specified path. Here I chose the 'appendix_fig' folder, where all the figures to insert in the appendix had been saved;</sub>

- <sub>`The 'include_graphics()` function is part of the 'knitr' package, and it allows to embed external images in document format supported by 'knitr'.</sub>

Finally, **Appendix C: code**. Let's imagine we want to use our last appendix to include all the code we used to carry out our data cleaning, the statistical analyses, the features used for creating our figures and tables, and perhaps the custom functions we created to automate our work. 

Remember that making the code available in the appendix **favours the transparency and replicability of your work**. 

Doing this requires a very simple, single line of code. 

As you can see, we are leaving the code chunk empty, and writing exclusively within the curly brackets, to set the options for display. 

~~~~
```{r code=readLines(knitr::purl('./appendix.Rmd', documentation = 0)), eval = F}
```
~~~~

The function `purl()` takes the source code from the main document (specified by the file path `'./file.Rmd'`) and lists it within a single chunk that is not run (`eval=F`).

A long list of code lines should appear within the code chunk and it corresponds to the code used in appendix.Rmd!



