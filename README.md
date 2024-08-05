# clear-basics
Basics of Frontend development

# Extensions downloaded:
    - Prettier
    - Live-server
  
# Fundamentals:
    - When you visit website, your browser(client) sends an HTTP request to server & receives an HTTP response which includes HTML document that represent page you're visiting. Browser reads the document & constructs a DOM(Document Object Model). Once DOM  is ready, browser renders the target page.
    - To view HTTP request we can use `Network Tab`.
    - DOCTYPE declaration specifies version of HTML being used
    - root element in HTML is html element
    - Styles types: Embedded, external and inline
    - External stylesheets: styles.css Link the stylesheet doc: 
    - Override the external sheet stylesheet by defining the rules in the same html. 
    - Inline styles:

# Normalize css
    - Normalize.css will define css for complete page 
    - SELECTORS: Type, id, class, attribute
    - ID: <section id="products"></section>
    - <a href="www.google.com" target="_blank">Google</a>
        - To access all 'a' tag with target attribute :** a[target="_blank"] { color: orange; }**
              - OR
        - **a[href*="google"]{ color: orange;  }  **   //Use this instead of typing actual url as it is very fragile.
        - To check if url starts with given word: **a[href^="http"] { color: orange;  }**
        - To check if url ends with given word: **a[href$="http"] { color: orange;  }**
  
# Relational selectors



Select using p which includes all 'p'
        #products p{
            color: orange;
        }

Select only first child of products
        #products > p{
            color: orange
        }

Select immediate sibling of products
        #products + p{
            color: orange;
        }

Select all sibling of products
        #products ~ p{
            color: orange;
        }

# **Pseudo class selectors**

    Types of Pseudo selectors are: It starts with ":"
        - article :first-child{}
        - article p:first-child{}
        - article :first-of-type{}
        - article p:first-of-type{}
        - article p:last-child{}
        - article p:last-of-type{}
        - ul li:nth-child(odd){}
        - a :visited, a :link{}
        - a :hover, a :focus{}
  
# **Pseudo elements selectors**
    
    Starts with "::"
    - p ::first-letter{}
    - p ::first-line{}
    - p :: selection{}
    - p :: before{}
  
# **Selector Specificity**

    Each selector has weight. Herirachy is:
        - ID selector
        - Class & attributes specific
        - Element selector

# Basics:

For css property: box-sizing = border-box; the size of content is only shown or calculated and paddings and borders arent included. Therefore, apply it universally. But it is not applied to pseudo elements so specifically mention it  like
    *, *::before *::after{}

    overflow: hidden -> will hide if extra content and show scroll
    overflow: auto -> scrollbar only shows if more content

    Absolute units:
    px, pt, in, cm, mm

    Relative units:
    % -> relative to size of parent. By default the  block level elements height is 0 and width = 100%. Height cannot be used
    vw  -> size of view port -> We can size as per height as well and width too = 100vh and width = 50vw
    vh  -> size of view port
    em, rem -> font-size = em =  width = 10em means 10 * 16px(font-size default) and rem is root level which is 16px but em is whatever is parent font-size. Benefit is properly resizable and adjust as per fontsize of html defined in windows settings


    vh height can cause some issues in mobile screen. So use media queries

# Positioning:

    By default all boxes position of all elements are "Static" means they are not positioned. To position these elements change position property to relative where we can position it relative to original posiition

    position: relative -> we can position it relative to its original position by left = -4rem or right = 4rem. 

    z-index property is the depth. By default its 0 for all elements. if 1 means closer to us and -1 means away

    Absolute:  Here we can position element relative to its container
        container - position: relative
        box2: position: absolute

    Position to view port:
        Box2: position: fixed
                top: 0


# Floating elements:
    float: left or right // pushed the elements to right or left side of container and other elements will float around it so we can even have the block level elements like p to the side of the element

    parent collapsing: Floated elements are invisible to parent element so it does not contain it.
    So add empty div with clear class:
    <div class="clear"> </div>

    Other way:
    Use pseudo class:
    tweet ::after{
        content: '';
        display: block;
        clear: both;
    }

    to fix it everywhere in page right general class: cf 
     cf ::after{
        content: '';
        display: block;
        clear: both;
    }

//Dont use floats: Use Flexbox to build layouts

# FlexBox:

Laying out elements in either row or column direction:

Flex will handle how the childrens will be placed in a container. So always apply flex to the parent and not to the child

In flex we have two axis: main and cross axis
    direction: row -> main = horizontala nd cross: vertical
    direction: columne -> main: vertical and cross: horizontal  

    Align items:
        justify content:  along main axis
        align-item: along cross axis
    flex-wrap: wrap; Items that dont fit in one line will be wrapped and pushed down mainitaining the size 
    align-content: center: This align content will adjust the complete content of flexbox as per main axiss

    //To move one of item up or down or left or right:
    align-self
   s

   Sizing items in flex: Not to container but to items:
   - flex basis: // will override the normal width or height depending on flex-direction: row or column.
   - flex grow: // growth factor of flex items. Grow in same factor
   - flex shrink: // how the elements shouldl shrink 
   - flex grow shrink basis

# Grids:

Define a grid using container
    display: grid
    grid-template-rows
    grid-template-columns

    justify-item: along horizontal axis
    align-items: along vertical axis
    