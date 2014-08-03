# KayueRequirejsBundle 

This bundle provides simple integration of RequireJS library into Symfony2.

## Configuration

```yaml
kayue_requirejs:
    bundles:
        AcmeDemoBundle: 
            baseUrl: bundles/acmedemo/scripts
            builtUrl: bundles/acmedemo/scripts-built
        FooBarBundle: ~
    requirejs: 
        src: "//cdnjs.cloudflare.com/ajax/libs/require.js/2.1.8/require.min.js"
        binary: "node_modules/requirejs/bin/r.js"
        config:
            paths: 
                "jquery": "../bower_components/jquery/dist/jquery"
                "bootstrap": "../bower_components/bootstrap/js"
                # This bundle will auto include the registered bundles:
                # "acmedemo": "bundles/acmedemo/scripts"
                # "foobar": "bundles/anotherdemo/scripts"
            shim:
                "bootstrap/dropdown": ["jquery"]
        build:
            optimize: "uglify2" # Default to "none"
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
