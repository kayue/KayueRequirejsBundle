# KayueRequirejsBundle 

This bundle provides simple integration of RequireJS library into Symfony2.

## Configuration

```yaml
kayue_requirejs:
    requirejs: 
        src: "//cdnjs.cloudflare.com/ajax/libs/require.js/2.1.8/require.min.js"
        binary: "node_modules/requirejs/bin/r.js"
        optimize:
            -
                resource: @AcmeBundle/Resources/public
                buildFile: build.js
                mainConfigFile: config.js
    bower: 
        binary: "node_modules/bower/bin/bower"
```

## Usage

Load RequireJS in the head of your HTML.

```jinja
{{ kayeu_requirejs_require({ "acmedemo/common": {"foobar/page1"} }) }}
```

The above will render the following code:

```html
<script src="//cdnjs.cloudflare.com/ajax/libs/require.js/2.1.8/require.min.js"></script>
<script>
    require(['acmedemo/common'], function (common) {
        require(['foobar/page1']);
    });
</script>
``` 

## References

- [HearsayRequireJSBundle](https://github.com/hearsayit/HearsayRequireJSBundle)
- [OroRequireJSBundle](https://github.com/orocrm/platform/tree/master/src/Oro/Bundle/RequireJSBundle)
- [RequireJS Multipage Shim Example](https://github.com/requirejs/example-multipage-shim)
