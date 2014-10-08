working-style
=============

# markup

### Give ``<script>`` tags ___title___ attributes
```
<script title='main nav functionality' src='nav.js'></script>
<script title='image uploader' src='uploader.js'></script>
```

Usually I'm using gulp or grunt to create distributions with my .js and .css minified into single files. If for whatever reason I'm not, I use this technique for readibility. It's helpful scanning a stack of ``<script>`` tags and making sure everything is being loaded in the right order.

If I've got multiple .css files, I'll use it for my ``<link>`` tags.


### See if an [existing element](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5/HTML5_element_list) can be applied before classing another ``<div>``

```
  <!-- i like -->
  <main>
    <section></section>
  </main>

  <!-- 
      now everything in my .css starts with a 'c' and i'm going to keep forgetting the nesting order of these two. wah. wah. 
  -->
  <div class='container'>
    <div class='content'></div>
  </div>
```

