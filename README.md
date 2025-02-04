<img src="https://github.com/phlex-ruby/morphlex/assets/246692/128ebe6a-bdf3-4b88-8a40-f29df64b3ac8" alt="Morphlex" width="481">

Morphlex is a tiny (1.6KB [minified/gzipped](https://www.unpkg.com/morphlex)), optimal DOM morphing library written in TypeScript. DOM morphing is the process of transforming one DOM tree to reflect another, while preserving the state of the original tree and making as few changes as possible.

Morphlex uses ID Sets — a concept pioneered by Idiomorph — to match nodes with deeply nested identified elements. It also maps out _sensitive_ elements to avoid moving them around.

## ID Sets

Each element is tagged with the set of IDs it contains, allowing for more optimal matching.

Failing an ID Set match, Morphlex will search for the next best match by tag name. If no element can be found, the reference element will be deeply cloned.

## Node sensitivity

Simply moving certain elements in the DOM tree can cause issues. To account for this, Morphlex gives priority to sensitive elements, moving less sensitive elements around them whenever possible.

This works in any direction, even if the sensitive element is deeply nested.

## Try it out

The easiest way to try out Morphlex is to import it directly from UNPKG.

```html
<script type="module">
  import { morph } from "https://www.unpkg.com/morphlex@0.0.15/dist/morphlex.min.js";

  morph(currentNode, referenceNode);
</script>
```

Alternatively, you can install it via npm and import it into your project.

```bash
npm install morphlex --save
```

```javascript
import { morph } from "morphlex";

morph(currentNode, referenceNode);
```

The `currentNode` will be morphed into the state of the `referenceNode`. The `referenceNode` will not be mutated in this process.

## Contributing

If you find a bug or have a feature request, please open an issue. If you want to contribute, please open a pull request.

> [!TIP]
> Morphlex is written in **[TypeScript](https://www.typescriptlang.org)** becuase it helps us avoid a whole category of potential bugs. If you’re more comfortable writing JavaScript, you’re very welcome to open a Pull Request modifying the `dist/morphlex.js` file. I’m happy to take care of the TypeScript conversion myself. — Joel
