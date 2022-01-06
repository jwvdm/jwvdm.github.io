# Personal Homepage Jan-Willem van de Meent

Made using jekyll, bootstrap and jekyll-scholar (for bibtex publication list). 


## Adding new Publication

For your publication to appear under one of the sections on the "Publications" page you simply have to add a bibtex entry to the corresponding bibtex file in `./_bibliography`.


## Adding new Working Paper

In order for your paper to appear in the "Working Papers" section on the main page you have to add your paper in `_include/_includes/papers.html`. 
Each entry `<div class="pub row"> ... </div>` needs to specify a 
thumbnail image, title, venue, authors, abstract, and a link to the manuscript. 
Your entry should have the following form:

```html
<div class="pub row">
  <div class="pub-image col-md-3">
    <img alt="your alt text" src="{{ '/assets/images/your_thumbnail.jpg' | relative_url }}">
  </div>
  <div class="pub-info col-md-9">
    <div class="pub-title">
      Your paper title
    </div>
    <div class="pub-venue">
      <a href="url_to_venue">Name of venue</a>
    </div>
    <div class="pub-auth">
      <a href="url_to_authors_website">author name</a>,
      ...
      <a href="/">Jan-Willem van de Meent</a>.
    </div>
    <div class="pub-abst">
        Your abstract     
    </div>
    <div class="pub-links">
      [<a href="url_to_your_paper">Abbreviation or short form of platform/venue, i.e. arXiv or NeurIPS 2021</a>] 
    </div>
  </div>
</div>
```
Don't forget to upload your thumbnail image to `./assets/images` (please try to keep the file size minimal).

Before you submit a pull request please check that everything works as expected, i.e. check that everything is rendering correctly and all of your links are working.
To inspect your changes you can run a jekyll server locally by running
```
    bundle exec jekyll serve
```
in the repository's root directory. 
To run the above command you need to have `ruby` and `bundler` installed. Once your have `ruby` you can install bundler via
```gem install bundler```.

