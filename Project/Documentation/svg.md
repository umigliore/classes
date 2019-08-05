# svg

Manipulate svg as objects and make code more readable.

## Instantiate a new SVG tree

_svgObject_ [object] := ***svg*** {(_param_ [text])}

- _param_ is an optional text enumeration semicolons separated like `'keepReference;solid:lavender'`.

  1. `keepReference` indicate that the svg reference should be kept in memory after use. In this case, don't omit to [release memory] when svgObject will no more used.
  2. `solid` allow to create a canvas with a white background (transparent by default). To specify another background color you can pass the color expression to use after a colon character ie `solid:lavender`
  
- _svgObject_ returned object containing the XML reference in memory and associated member methods.


 Properties         | Contains                                                                                       | Default
-------------       |-------------                                                                                   |-------------
*root*              | The XML reference of the SVG tree                                                              |
*lastCreatedObject* | The XML reference of the last created object using a creation method                           | Null
*picture*           | The image generated from the SVG description after calling method `get ("picture")`            | Null
*xml*               | The XML text generated from the SVG description after calling method `get ("xml")`             | Null
*autoClose*         | A boolean that indicates whether the xml tree should be closed after calling the get () method | True 
*success*           | A boolean that indicates whether a method call was successfully executed                       |
*errors*            | A collection of textual descriptions of encountered errors                                     | [ ]


**Notes**: 

* If a setting method is called before the creation of an object in the canvas, the target is canvas itself, otherwise the target is the last created object. Where appropriate, the target of the method can be given (see above)
* Remember that you can always add non managed attributes with the methods attribute() or attributes() (see above)
* Remember that you can always use DOM XML commands to manipulate the SVG tree (*root*) or object (*lastCreatedObject*)
* Creation and setting methods always return the _svgObject_ so methods could be chained

## Creation methods
 |  
-------------    |-------------
`group()`        | Creates a group
`rect()`         | Creates a square or arectangle
`image()`        | Put a referenced image
`embedPicture()` | Embed a picture
`textArea()`     | Creates a text area


## Settings methods
 |  
-------------  |-------------
`position()`   | Sets the position
`dimensions()` | Sets the dimensions
`fill()`       | Sets the beackground color and opacity
`stroke()`     | Sets the foreground properties
`font()`       | Sets the font properties
`attribute()`  | Sets one attribute
`attributes()` | Sets one or more attributes

## Miscellaneous
 |  
-------------  |-------------
`get()`        | Returns the picture or the XML text generated from the SVG tree (the result is keep into the picture or xml property).
`close()`      | Releases the XML tree from the memory.
`show()`       | Display the SVG picture & tree into the SVG Viewer if the component 4D SVG is available.

## Sample code

`$m:=svg`    
    
`// My first rect`   

`// Pass optional attributes if you need`        

`// Or use svg methods if available`   
`// You can always add non managed attributes with attribute() or attributes()`   

`// Create a group with id "test" & keep its reference`   

`// Create a rounded square into the group`   

`// My first text`   

`// Get the image and keep the reference of the svg object for later use`   

`// Get the XML text (the memory is automatically released)`   