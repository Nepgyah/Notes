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