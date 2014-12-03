Tagging
=======

A select2 wrapper for Stackla tagging control.

## Render By HTML

```html
<span class="tagging"
     data-toggle="tagging" 
     data-tagging-mode="view"
     data-tagging-load-url="/api/tags?total=100"
     data-tagging-search-url="/api/tags?search?tag={label}" 
     data-tagging-add-url="/api/tags/add?tag={label}" />
     <span class="tagging-view">
         <span data-tag-label="foo" data-tag-value="1">foo</span>
         <span data-tag-label="bar" data-tag-value="2">bar</span>
         <span data-tag-label="zoo" data-tag-value="3">zoo</span>
         <span data-tag-label="fun" data-tag-value="4">fun</span>
    </span>
    <span class="tagging-modify">
        <select multiple="multiple"><!-- Could be omitted -->
            <option value="1" selected>foo</option>
            <option value="2" selected>bar</option>
            <option value="3" selected>zoo</option>
            <option value="4" selected>fun</option>
            <option value="5">goo</option>
        </select>
    </span>
</span>
```
    
## Render By JavaScript

### HTML

```html
<span id="wrapper"></span>
```

### JavaScript

```js
var tagging = new Tagging('wrapper', {
    loadUrl: '/api/tags?stack=vari&limit=100',
    loadMethod: 'GET',
    mode: 'view',
    multiple: true,
    saveUrl: '/api/tags?stack=vari&tag={label}',
    saveMethod: 'PUT',
    // Be careful with return value, you should always return something it needs.
    onBeforeLoad: function (xhrSettings) { return xhrSettings; },
    onBeforeSave: function (xhrSettings) { return xhrSettings; },
    onLoad: function (data) { return data; },
    onSave: function (data) { return data; },
    tags: [
        {label: 'foo', value: 1, selected: true},
        {label: 'bar', value: 2, selected: true},    
        {label: 'zoo', value: 3, selected: true},    
        {label: 'fun', value: 4, selected: true},   
        {label: 'goo', value: 5}  
    ]    
});
```

Or...

```js
$('#wrapper').tagging({
    // the same as above
});
```

## Methods

* `addTag` - Select a tag
* `refresh` - Refresh to get the latest data
* `removeTag` - Remove a specific tag
* `setMode` - The param could be 'view' or 'modify'
* `hasTag` - Check if a tag exists
* `toggle` - Switch the mode

## Events

* `render`
* `load`
* `save`
* `toggle`
* `refresh`
