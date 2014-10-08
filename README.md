#Working Style
=============

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

## readable ui components

> There are only two hard things in Computer Science: cache invalidation and naming things.  
> -- Phil Karlton

My UI elements typically have 3 major distinctions for .css styling.

1. The component name
2. The component's variation(s)
3. The component's ui state

Here's how I declare them...

 First, a basic component named ``dialog``.
```
<div class='dialog'></div>
```

Easy. Next, I add a ``modal`` variation because I want this dialog to be a fullscreen modal. Things are still feeling readable.
```
<div class='dialog modal'></div>
```

Here's where things get different. I like to use [data attributes](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_data_attributes) to manage the ui state.

```
<div class='dialog modal' data-state='active'></div>
```

Data attributes are easy to access in javascript which is important for my UI states because I assume I'll be be working with the state property in my app's .js.

#### Bonus
If you use jQuery, your element's data- attributes are [automatically pulled into the jQuery's data object](http://api.jquery.com/data/#data-html5). 

```
  <div id='myModal' class='modal' data-state='active'></div>
  <script>
    var $myModal = $('#myModal');
    console.log($myModal.data('state')); // logs 'active'
  </script>
```



