<center><img src="/img/tutheaderbl.png" alt="Img"></center>

## Write your dissertation in Rmarkdown!

*Created by Anna*

### Tutorial Aims

1. Understanding the advantages of using `Rmarkdown` for writing pdf documents, focusing on writing your dissertation;

2. Learning how to create the template for the main page, and appending all the other sections to it;

3. Glancing at using LaTex for embellishing the pdf output and functioning as a supplement to Markdown; 

4. Becoming familiar with `knitr` and `kableExtra` packages. 

### Steps:

#### <a href="#section1"> 1. The "main" Rmarkdown document.</a>
<a href="#subsect1"><sub> a) The front page </sub></a>

<a href="#subsect1"><sub> b) Abstract </sub></a>

#### <a href="#section2"> 2. Create the different sections of your dissertation.</a>
#### <a href="#section3"> 3. Add or create tables.</a>
#### <a href="#section4"> 4. Add or create figures.</a>
#### <a href="#section5"> 5. Add or create code.</a>
#### <a href="#section6"> 6. Add raw data in the Appendidx.</a>
#### <a href="#section7"> 7. Some final adjustments.</a>
#### <a href="#section8"> 8. Let's merge!</a>

<a name="section1"></a>

## 1. The "main" Rmarkdown document. 

When you write a document, whether it's an essay, or a scientific report, or be it your undergraduate dissertation, it is going to be structured in different sections. 

In the scientific world, this document likely contains: an introduction, methods, results, discussion, and a list of your references. If we consider a published paper or a thesis, these also contain an abstract, perhaps a section with abbreviations, and at the end present a section with supplementary information, aka the appendix. 

As the aim of this tutorial is to successfully write your dissertation with Rmarkdown, it is useful to consider the number of sections necessary for your output. In fact, Rstudio would crash???? if the entire load of your written work, together with any potential code, images, tables, etc., would all be inserted in just one .Rmd file. Also as a matter of cleanliness of code and better organisation, it is a matter of good practice to create a series of .Rmd files that then merge within just one, which is going to be the final pdf output. 

So, the first to start with is the macro .Rmd file. The one where all other files are going to merge. In this file we are going to set the first page of your dissertation, and also the general formatting rules that will apply to the entire document. 

To do so, open Rstudio and create a new .Rmd file by clicking on the blank sheet with the green plus one the left-hand side of the interface. 

<img src="/img/open_md.png" alt="opening rmarkdown">

Once you have created a new Rmarkdown document, leave title and author blank (you don't want these to appear at the top of your pdf) and select PDF as the Default Output Format. Click OK and let's start writing in the new file.

<img src="/img/rmd_opened.png" alt="rmarkdown opened">

You will see at the top a section called YAML header, delimited by three hyphens (---). The header embeds the information that you have just given (blank for the title, no author and pdf_document as your desired output) and allows you to set rules that are going to be applied throught the document. This header does not show in the output. 

As you can see, the new .Rmd file provides a default structure already written, quickly explaining the file and showing code chunks that can be embedded in it (the grey banners). Erase the text, as we are going to be writing our own, but keep the YAML header (IT'S ESSENTIAL!) and also the first grey banner or code chunk. Your file should look like this: 

<img src="/img/clean_rmd.png" alt="clean rmd file">

<a name="subsect1"></a>

### a) The front page

The School of Geosciences has a standard formatting rules for the undergraduate dissertation document, and we are going to set the file according to them (these are as of 2020, if they have changed edit them accordingly). 

Let's create the front page of the dissertation. It's an important one, as it's going to make the first great impression of your work!
The front page requires all elements to be centred. Here we are going to start using some LaTex syntax to do so. Write the following right under the first code chunk (will explain what that does later):

````
\begin{centering}

\end{centering}
````

Whatever you will write in between the begin and end centering functions will be centered in the page. 
Now let's set a 3cm spacing from the top of the page, to insert the first element of the front page: the university logo. 
Remeber, write in between the \begin and \end functions to centre your elements. 

````
\vspace{3cm}
````
This feature will create a 3cm spacing from the top of the page. 
Undearneath it, we are going to place our second code chunk, to show the image of the university logo. In the repository, you will find an image called "uni_logo.png", stored in a file called "img". 

Insert the code chunk by selecting on the icon "insert" and clicking on "R". In this way the code chunk will be supporting R language, but as you can see it also supports Python, Bash, SQL, etc. 

<img src="/img/uni_logo_chunk.png" alt="uni logo chunk">

In between the curly brackets of the code chunk, you can set all the characteristics that you want applied to the code within it. I have named the code chunk "uni_logo", making it easier to retrieve the chunk later on among many. Echo = False will show only the output of the code inserted in the code chunk, but not the code itself. And finally, out.width sets a feature for images and figures, in particular the percentage width that the image will occupy out of the total white space in the pdf document. 

Knitr is the only most important package used in Rmarkdown, to manipulate code within code chunks. **INSERT LINLK TO KNITR PAGE?** You can retrieve the image of the university logo with the function include_graphics().

Now we need to add the name of the university and that of the department. We are going to do so 1cm distant from the logo.

````
\vspace{1cm}

\Large 
{\bf The University Of Edinburgh}

\Large
{\bf School Of Geosciences}
````

You recall the \vspace function from above, but now there's also \Large, which sets a standard for the text that comes later to be output with a larger font, and \bf which sets the text within curly brackets to **bold**.

It's time to add the *title* of your dissertation! 

````
\vspace{1cm}

\Large

\doublespacing
{\bf COMPARISON OF TOP-DOWN AND BOTTOM-UP APPROACHES ON SPECIFIC LEAF AREA PATTERNS, \\AT GLOBAL, LATITUDINAL, AND BIOME SCALES}
````

As you might have figured, adding the function \Large will increase the font of whatever writing you add undearneath it, and adding \doublespacing will double the space between lines of text. By wrapping a specific part of your text within curly brackets and adding the function \bf at the start you will specify that only that part of the text will need be in bold font. The university guidelines specify to have the title all capitalised. And finally, the double `\\` sign will make the text go onto a new line (just like \n in a string in R code!).

To finish the front page we need to add author, degree and date! 

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
May 2020
````

Again, as a matter of formatting guidance, I added some specified spacing in between the various lines of text that follow the thesis title. By adding \normalsize you input the .Rmd file to go back to a 'normal' font, since the last input was \Large. 

**Remember** that rmarkdown will remember the last formatting input you gave it, and to change it for the following lines you need to specify the new function!

We have created the front page! Knit it to check what it looks like: 

<img src="/img/front_page_pdf.png" alt="front page pdf output">


<a name="subsect2"></a>

### b) Abstract

We can add the Abstract in the next page, by specifying this LaTex command

````
\newpage
````

Anything you'll write or insert after this specification will appear on a new page. This way you have control over the distribution of your content. 

In the new page, insert the following

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

The title "Abstract" is centered and bold, while the spacing in between lines of text is set to 1.5. As text I have included main guidelines for writing an abstract, which should come useful to you when writing it. 

You can knit the document to check out the output.

<img src="/img/abstract.png" alt="abstract" width = 49%>

<img src="/img/abstract_output.png" alt="abstract output" width=49%>

<a name="section2"></a>

## 2. Create the different sections of your dissertation.

Looking good! The front page of the dissertation is ready, and so is your abstract. Now we need to add the different sections of the thesis, which we'll create on separate .Rmd files. These .rmd files will behave as 'children' to the main file, which we have knitted so far.

In the main document, paste the following

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

As you can see, we've just added a code chunk for each section of your dissertation. The "child" feature of the code chunk links the main .Rmd document to another one. This means that once you'll knit from the same main document, the content from each of the child documents will be pasted and marged into one, final pdf. Cool, uh! And super easy. 

However, remember to make sure you've created the .Rmd files that you link to your main file, and check the spelling! As you can imagine, non-existing or mispelled files which have been included in the main document will give you error. 

To speed things up a little, I have created the files already and you can check them out from the main folder. Knitting the document now, you should see how the content from each has been pasted into one main document.

It is unpractical to show here in one image, but you should now have a 10-page document, with each section of the dissertation on a new page. The structure is coming along nicely! Well done!

