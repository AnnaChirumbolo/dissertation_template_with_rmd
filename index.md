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


