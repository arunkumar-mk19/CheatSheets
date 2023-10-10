# Pure CSS style snippets


#### 1. Required mark for labels

```css
.required:after {
    content: "*";
    position: relative;
    font-size: inherit;
    color: red;
    padding-left: .25rem;
    font-weight: 600
}
```

Example preview:
`Name *`