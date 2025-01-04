# Apiator.js

Apiator.js is a JavaScript library that provides an easy way to work with JSON API resources. It offers a simple interface for handling collections and items, with support for pagination, filtering, and sorting.

## Features

- JSON API compliant
- Collection and Item resource handling
- Built-in pagination support
- Filtering capabilities
- Sorting functionality
- Template-based rendering
- Event handling
- Promise-based AJAX operations

## Dependencies

- jQuery
- Underscore.js (for templating)

## Installation

Include the required dependencies and apiator.js in your HTML:

```html
<script src="jquery.min.js"></script>
<script src="underscore.min.js"></script>
<script src="apiator.js"></script>
```

## Basic Usage

### Initialize a Collection

```javascript
// Using jQuery plugin syntax
$("#my-collection").apiator({
    url: "/api/resources",
    resourcetype: "collection", // default is collection when not specified 
    template: "#item-template" // default is content of the  selected jQuery element when not specified    
});

// Alternative syntax
$("#my-collection").apiator2collection("/api/resources");
```

### Initialize an Item

```javascript
$("#my-item").apiator({
    url: "/api/resources/123",
    resourcetype: "item",
    template: "#item-template" // default is jQuery selected element when not specified    
});

// Alternative syntax
$("#my-item").apiator2item("/api/resources/123");
```

### HTML Template Example

```html
<script type="text/template" id="item-template">
    <div class="item">
        <h3><%= attributes.title %></h3>
        <p><%= attributes.description %></p>
    </div>
</script>
```

## Configuration Options

- `url`: API endpoint URL
- `resourcetype`: Type of resource ("collection" or "item")
- `template`: Template for rendering items (can be selector or HTML string)
- `pageSize`: Number of items per page
- `paging`: Element selector for pagination controls
- `filter`: Form element selector for filtering
- `sort`: Element selector for sorting controls
- `emptyview`: Template for empty state
- `addontop`: Boolean to add new items at the top of the collection

## Events

```javascript
$("#my-collection").apiator({
    url: "/api/resources",
    on: {
        load: function(collection) {
            console.log("Collection loaded", collection);
        },
        update: function(collection) {
            console.log("Collection updated", collection);
        },
        afterrender: function(collection) {
            console.log("Collection rendered", collection);
        }
    }
});
```

## Methods

### Collection Methods

- `loadFromRemote()`: Load data from server
- `reload()`: Reload current data
- `refresh()`: Alias for reload
- `append(data)`: Add new item to collection
- `clear()`: Remove all items
- `render()`: Re-render the collection

### Item Methods

- `loadFromRemote()`: Load item data from server
- `update(data)`: Update item data
- `delete()`: Delete the item
- `render()`: Re-render the item

## Debug Mode

Enable debug mode to see detailed logs:

```javascript
apiatorDebug = true;
```
