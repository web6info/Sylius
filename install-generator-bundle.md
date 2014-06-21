Installare SensioGeneratorBundle su Sylius
===

Modificare il file `/dir/progetti/progetto/composer.json`:

```js
...
"require": {
    ...
    "sensio/generator-bundle": "~2.3",
    ...
},
...
"autoload": {
	"psr-0": { "Sylius\\": "src/", "Web6\\": "src/" }
},
...
```

Applicare le modifiche lanciando i seguenti comandi:
```bash
$ cd /dir/progetti/progetto/
$ composer update
```

Attivare il "SensioGeneratorBundle" modificando il file `AppKernel.php`:
```php
public function registerBundles(){
    $bundles = array(
        ...
        new Sensio\Bundle\GeneratorBundle\SensioGeneratorBundle(),
    );
    ...
}
```
