#How I Work

> My name is John Leonard. I'm Associate Director of Technology at [frog](http://frogdesign.com). I do a lot of prototyping on the web platform. This is how I work.

## Machine setup
I work on a Mac Book Pro. [Here's a gist with rough notes on my setup](https://gist.github.com/jleonard/8041209). The thing I love most on that list is [sexy bash prompt](https://github.com/twolfson/sexy-bash-prompt).

# html

### Give ``<script>`` tags ___title___ attributes
```
<script title='main nav functionality' src='nav.js'></script>
<script title='image uploader' src='uploader.js'></script>
```

If for whatever reason I'm not minifying everything into a single .js file, I use this technique for readibility. It's helpful scanning a stack of ``<script>`` tags and making sure everything is being loaded in the right order.

If I've got multiple .css files, I'll use it for my ``<link>`` tags.


### See if an [existing element](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5/HTML5_element_list) can be applied before classing another ``<div>``

```
  <!-- i like -->
  <main>
    <section></section>
  </main>

  <!-- 
      Now everything in my .css starts with a '.c' and I can't remember the nesting order. wah. wah. 
  -->
  <div class='container'>
    <div class='content'></div>
  </div>
```

# css

## organizing ui component names, states and variations

> There are only two hard things in Computer Science: cache invalidation and naming things.  
> -- Phil Karlton

My UI elements have 3 major distinctions for .css styling.

1. Name
2. Variation(s)
3. State

Here's how I declare them...

**Component name is part of the class list.**
```
<div class='dialog'></div>
```

**The Component's variation goes in the class list as well.**
```
<div class='dialog modal'></div>
```

Here's where things get different. I like to use [data attributes](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_data_attributes) to manage the ui state.

```
<div class='dialog modal' data-state='active'></div>
```

Data attributes are easy to access in javascript which is important for my UI states because I assume I'll be be working with the state property in my app's .js.

> ##### Bonus
> If you use jQuery, your element's data- attributes are [automatically pulled into the jQuery's data object](http://api.jquery.com/data/#data-html5). 

```
  <div id='myModal' class='modal' data-state='active'></div>
  <script>
    var $myModal = $('#myModal');
    console.log($myModal.data('state')); // logs 'active'
  </script>
```

## (imho) css readability is more important than selector efficiency

Look at most css frameworks and you'll find components that look like this...

```
<div class='button button-primary'></div>
```

I prefer the readiblity of...
```
<div class='button primary'></div>
```
...even though it's less efficent css. This comes down to a case of [knowing the rules](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS) before breaking them.


