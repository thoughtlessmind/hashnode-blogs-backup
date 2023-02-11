# Tooltip using only CSS

Using a tooltip is a great way to pass information to the user in a very minimal and efficient way. It reduces the contents from the page which is important to show but not needed to show all the time.

  But when it comes to adding tooltips to the website, developers generally use a library for this, which is definitely good as it gives a lot of customizations and controls. But in a situation when tooltips are required but not on a large scale instead, in certain places on the page, then it kinda feels useless to carry around such big libraries for this.  

___
 
>*Required Knowledge:-*
- *General working knowledge of `HTML` and `CSS`*
- *How `data` attribute works in HTML and CSS. For reference check [this CSS-tricks article](https://css-tricks.com/a-complete-guide-to-data-attributes/#styling)*  
- *Understanding of pseudo-selectors in CSS*

___
 
  There are several ways to create a tooltip in CSS. In this, we'll be using `pseudo-selectors` of CSS. One benefit of using this method is that there's no need to create an actual element in the HTML.  
  First of all on whichever element you want to show the tooltip, add a `data` attribute `data-customTooltip="Tooltip text"`. Also, pass the text you wanna show on the tooltip.

> index.html
```html
<span data-customTooltip="Tooltip text">
  Hover on me to see tooltip
</span>
```

That's it, this is all we need in HTML. Now, let's add CSS to it. Here we'll be styling the tooltip using data attribute selector. [Read here](https://css-tricks.com/a-complete-guide-to-data-attributes/#styling) more about it.
> styles.css  

```css
[data-customTooltip]{
    cursor: pointer;
    position: relative;
}

[data-customTooltip]::after {
    background-color: #fff;
    color: #222;
    font-size:14px;
    padding: 8px 12px;
    height: fit-content;
    width: fit-content;
    border-radius: 6px;
    position: absolute;
    text-align: center;
    bottom: 0px;
    left: 50%;
    content: attr(data-customTooltip);
    transform: translate(-50%, 110%) scale(0);
    transform-origin: top;
    transition: 0.14s;
    box-shadow: 0 4px 14px 0 rgba(0,0,0,.2), 0 0 0 1px rgba(0,0,0,.05);
  }
```  
Here, we're selecting the elements which have data-customTooltip attribute on them and creating a pseudo-element using :after. Till now a pseudo-element for the tooltip is created but it's not visible as there is scale(0) in the style.   

 Now change the scale to 1 on hover on the parent element.

> style.css
```css
  [data-customTooltip]:hover:after {
    display: block;
    transform: translate(-50%, 110%) scale(1);
  }
```  


And here is our tooltip....  
Position can be changed according to requirement by giving suitable `top`, `left`, `bottom`, and `right` values along with translate property.  
*I'll be writing another blog where we'll make the position of the tooltip dynamic and also incorporate light and dark themes.*


![tooltipDemo.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1610738524318/TO87qEe7p.gif)
 
Now just pass `data-customTooltip="tooltip text"` attribute wherever you want to add a tooltip.
> Codepen demo  


%[https://codepen.io/thoughtlessmind/pen/rNMoLWo]

 ---
PS:- *This is my first blog, if there's any mistake I'm making or there's any scope of improvement, please feel free to comment.*😀



