## Responsive and Screen Variants:

```css
@responsive{
  .myStyle{ /* Now it will works with responsive variants like => sm,md,lg,xl,etc. */
    color: pink;
  }
}

@screen md{ /* That means => @media screen and (min-width:md){}*/
  body{
    background: #444;
  }
}
```
