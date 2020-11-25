<center><img src="/img/tutheaderbl.png" alt="Img"></center>

## Write your dissertation in Rmarkdown!

**Created by Anna** 

### Tutorial Aims

1. Understanding the advantages of using `Rmarkdown` for writing pdf documents, focusing on writing your dissertation;

2. Learning how to create the template for the main page, and appending all the other sections to it;

3. Glancing at using LaTex for embellishing the pdf output and functioning as a supplement to Markdown; 

4. Becoming familiar with `knitr`and `kableExtra` packages. 

### Steps:

#### <a href="#section1"> 1. The "main" Rmarkdown document.</a>
#### <a href="#section2"> 2. Create the different sections of your dissertation.</a>
#### <a href="#section3"> 3. Add or create tables.</a>
#### <a href="#section4"> 4. Add or create figures.</a>
#### <a href="#section5"> 5. Add or create code.</a>
#### <a href="#section6"> 6. Add raw data in the Appendidx.</a>
#### <a href="#section7"> 7. Let's merge!</a>

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


