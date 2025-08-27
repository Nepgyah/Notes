## Styling
### Formatting
1 selector per line in multi-selected rulesets
```
Good
.anime,
.manga {
	color: pink
}

Bad 
.anime, .manga {
	color: pink
}
```
1 declaration per line in a declaration block
```
Good
.anime {
	color: '#ffffff';
	padding-top: 1rem;
}

Bad 
.anime {
	color: '#ffffff'; padding-top: 1rem;
}
```

Use lowercase, longhand hex values
```
Good
color: '#1234ff'

Bad
color: GREEN
```

Use single quotes
```
Good
input[type='checkbox']

Bad
input[type="checkbox]
```

Do not specify units for zero-values
```
Good
margin-top: 0

Bad
margin-top: 0px
```

Do not add leading zeroes for decimal figures
```
Good
padding-left: .5rem

Bad
padding-left: 0.5rem
```
### Declaration Order
If possible stick to this grouping during styling
```
.selector {
	/* Positioning + Z Index */
	
	/* Display, Box Model, Margin, Padding */

	/* Typography, List Styles, Font, Text Styles */

	/* Background */

	/* Border styling */
	
	/* Animations and Transitions */

	/* Misc */
}
```

### BEM
A common way to name and organize classes is through BEM (Block, Element, Modifers). This only applies to classes and **SHOULD NOT** be used for ids

- Block
    - Describe its purpose
    - Functional independent component that can be resued, represented by the class attribute
        - Ex: "header", "logo", "search-form"
    - Block should influence its enviornment, shouldnt set the external geometry (margin, positioning, etc)
- Element
    - Describe its purpose
    - Part of a block that can't be used seperately from it
        - EX: "item", "text"
    - Elements are seperated from the block using double underscore
        - EX: "block-name__element-name"
            - "search-form__input"
            - "search-form__button"
- Modifyers
    - Describes its appearance, state, or behavior of a block
    - Used on **BOTH** block and element
    - Ex:
        - "size_s", "disabled", "left-top"
    - Defined by single underscore
        - Ex: "logo_left-top", "search-form_disabled"
### Accessibility
#### ARIA (Accessible Rich Internet Applications)
HTML attributes that define regions of a page. They let screen readers and other assistive technologies understand the structure of your page and provide navigational shortcuts
Common landmarks (roles)
- `banner`: The side wide header at the top
- `navigation`: Primary navigation menu
- `main`: The main content of the page, one per page
- `search`: Search form or section
- `complementary`: Side bar content
- `contentinfo`: Footer with side wide content (copyright, contact, etc)
- `region`: Generic label section of a page, requires a `aria-label` or `aria-labelled-by`. Some common sections that could require a label: "Contact, Pricing, FAQ"

Prefer native html first as they automatically map to ARIA roles in modern browsers
- `main`
- `nav`
- `header`
- `footer`
- `aside`

If you have multiple of the same type, distinguish them via a `aria-label`
```
<nav aria-label="Main navigation">...</nav>
<nav aria-label="Footer navigation">...</nav>
```

If links are simply images, such as a logo that acts as a home redirect. Add a label for the screen reader to compile
```
<a href="/" aria-label="Homepage">
  <svg class="arcadia-logo" viewBox="0 0 2554 1348">
    <use href="#arcadia-icon"></use>
  </svg>
</a>
```
