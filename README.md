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

## Naming

> There are only two hard things in Computer Science: cache invalidation and naming things.  
> -- Phil Karlton

UI elements have 3 major style points.

1. The component name ex ``<div class='modal'></div>``
2. The component's variation(s) ex. ``<div class='modal '></div>``
3. The component's state ex. ``<div class='modal' data-state='active'></div>``



