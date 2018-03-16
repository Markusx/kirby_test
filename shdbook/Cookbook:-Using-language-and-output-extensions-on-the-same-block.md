Showdown let's you use and define any number of extensions that act on the same block, that can be ran sequentially or at different moments.
This enables you to pre-parse/mark a block of text but defer any modifications for last by using a combination of a language extension and a output extensions.

This is useful if you, for instance, don't want showdown to parse the contents of your new language construct.

## Example
For instance, let's say you create an extension that captures everything between `%start%` and `%end%`. However, that content should not be modified by showdown. Obviously you can use pre tags for that, but that is beside the point.

Although showdown doesn't have any flag to prevent parsing the content of an extension, the same effect can be easily achieved by using a lang and a output extension together.
 
### Code (Fiddle here: http://jsfiddle.net/tivie/1rqr7xy8/)

```js
showdown.extension('myExt', function() {
    var matches = [];
    return [
        { 
            type: 'lang',
            regex: /%start%([^]+?)%end%/gi,
            replace: function(s, match) { 
                matches.push(match);
                var n = matches.length - 1;
                return '%PLACEHOLDER' + n + '%';
            }
        },
        {
            type: 'output',
            filter: function (text) {
                for (var i=0; i< matches.length; ++i) {
                    var pat = '<p>%PLACEHOLDER' + i + '% *<\/p>';
                    text = text.replace(new RegExp(pat, 'gi'), matches[i]);
                }
                //reset array
                matches = [];
                return text;
            }
        }
    ]
});
```
Basically, in this example, we created a lang extension that looks for the pseudo tags `%start%` and `%end%`, extract everything in between and saves it in a variable. The contents are replaced by a placeholder, so we can know the exact position where the text was extracted.

Later, after showdown has finished parsing everything, the output extension replaces the placeholder with the saved content.
