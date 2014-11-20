#How I .css

### .less
> [.less](http://lesscss.org/) is my preprocessor of choice. [sass](http://sass-lang.com/) is cool but I prefer node/npm tools. They're very similar so there's really no wrong answer.

### Organizing things: A tweak on [atomic design](http://bradfrost.com/blog/post/atomic-web-design/)
Atomic Design is a great methodology but I'm not a fan of the naming conventions. 

Atomic Design's Atoms, Molecules, Organisms, Templates and Pages are difficult to get a team to align on. Pages and Templates sound very similar and will confuse folks looking with a CMS-lens. Pages and Templates also break the bio-chem naming convention. Anyway, I obsess on naming and it's something I need to work on.

#### Organizing css & the DOM into manageable pieces.
This is how I break views down:
* **macro-structure** - This is how the nav, sidebars, main grid, footer etc. are composed on the page.
* **micro-structures (layout patterns)** - Smaller, potentially reusable layout structures like content grids, forms, tables, sidebar layouts etc.. These are containers with specific .css rules to govern the display of their children but don't always need associated .js.
* **components** - Components can contain multiple elements and or components. They usually have some .js associated with them. Examples are tabs, dialogs, etc.
* **elements** - The native html body elements (ul,p,div,etc.). In cases like tables and forms where an element is expected to contain multiple child elements I sometimes identify them as layout patterns or components.

Here's how that might apply to a site's main navigation. The nav is part of the page's macro structure in that it's a primary block of the page. The nav is also a container for micro-structures, components and elements.

```css
// macro structure
nav{
  background-color: black;
  height: 4rem;
  position: fixed;
  ...
}

// nav's internal micro structures
nav .tools{ ... }

// nav's components
nav .drop-down{ ... }

// nav's elements
nav h1{ ... }
nav ul{
 ...
 li{
  ...
 }
}
```

> # The Don'ts

### Don't overcomplicate things.

There's been a lot of attention around css coding convention systems like [BEM (Block, Element, Modifier)](http://www.integralist.co.uk/posts/maintainable-css-with-bem/) and [SUIT](http://suitcss.github.io/). Hate is a strong word. I hate both approaches.

Both are positioned as methods to organize css/dom while providing performance improvements for the browser's css selector engine. 

#### Don't use unweildy naming conventions 
**Both introduce excessive & repetitive naming conventions that pollute the class list and put burden on the front end developer. They suffer from obsessive encapsulation that's already provided by the DOM.**

Here's a BEM example
```html
<!-- BEM example -->
<section class="widget">
    <h1 class="widget__header">...</h1>
    <form class="widget__form" action="process.php" method="post">
        <p>...</p>
        <p>
            <input name="amount" class="widget__input widget__input--amount"> 
            <input type="submit" value="Calculate" class="widget__input widget__input--submit">
        </p>
    </form>
</section>

```

SUIT gets even more draconian because it can be used with a validation tool that introduces more complexity to the [naming conventions](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md) by requiring pascal case and camel case.
```html
<!-- SUIT example -->
<section class="Widget">
    <h1 class="Widget-header">...</h1>
    <form class="Widget-form" action="process.php" method="post">
        <p>...</p>
        <p>
            <input name="amount" class="Widget-input Widget-input--amount"> 
            <input type="submit" value="Calculate" class="Widget-input Widget-input--submit">
        </p>
    </form>
</section>
```

Should it be ``Widget-input`` or ``Widget-form-input``? Do I need ``__``, ``--`` or ``-``? Too much work.

**It leads to shit like this**
```
<ul class='list'>
 <li class='list__item'>...</li>
</ul>
```

#### Don't tightly couple .js functionality with the DOM
