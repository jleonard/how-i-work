#How I .css

### .less
> [.less](http://lesscss.org/) is my preprocessor of choice. [sass](http://sass-lang.com/) is cool but I prefer node/npm tools. They're very similar so there's really no wrong answer.

### Organizing things: A tweak on [atomic design](http://bradfrost.com/blog/post/atomic-web-design/)
Atomic Design is a great methodology but I'm not a fan of the naming conventions. 

Atomic Design's Atoms, Molecules, Organisms, Templates and Pages are difficult to get a team to align on. Pages and Templates sound very similar and will confuse folks looking with a CMS-lens. Pages and Templates also break the bio-chem naming convention. Anyway, I obsess on naming and it's something I need to work on.

#### Organizing css & the DOM into manageable pieces.
This is how I break views down:
* **macro structure** - This is how the nav, sidebars, main grid, footer etc. are composed on the page.
* **micro structures (layout patterns)** - Smaller, potentially reusable layout structures like content grids, forms, tables, sidebar layouts etc.. These are containers with specific .css rules to govern the display of their children but don't always need associated .js.
* **elements** - The native html body elements (ul,p,div,etc.). In cases like tables and forms where an element is expected to contain multiple child elements I sometimes identify them as layout patterns or components.
* **components** - Components can contain multiple elements and or components. They usually have some .js associated with them. Examples are tabs, dialogs, etc.

