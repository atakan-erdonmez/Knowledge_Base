---
tags:
  - "#web-design"
  - "#css"
---
 Concept: Instead of styling for desktop and stripping away features for mobile, you style for the smallest screen first, then use media queries to "add"  complexity as the screen size increases.

Why it’s a best practice:
1. Efficiency: Mobile browsers are the most constrained. By setting the simplest layout as your default (base), you serve the least amount of complex CSS to the devices that need it most.
2. Maintainability: Media queries become "enhancements" rather than overrides. You aren't constantly fighting against complex desktop styles to make them work on a phone.
3. Code Volume: You avoid writing redundant CSS. You define the "core" once, then only write the rules that need to change for larger screens.

  The Syntax Pattern:
```
/* 1. Base Styles (Applies to all devices, i.e., Mobile) */
.element {
    margin-left: 0;
    width: 100%;
}
/* 2. Enhancements (Applies only when the screen is wide enough, i.e., Desktop) */
@media (min-width: 768px) {
	   .element {
        margin-left: 3rem; /* Add specific layout shifts here */
        width: 50%;
    }
}
```


Key Takeaway: Always use min-width in your media queries. It dictates that the styling "kicks in" only once the screen passes that minimum size threshold,
keeping your base styles cleanly focused on mobile.

Used in [[10_Docs/50_Services/Website|Website]]