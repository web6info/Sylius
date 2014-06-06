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
$ php composer.phar update
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
Creare il proprio bundle:
```bash
$ php app/console generate:bundle --namespace=Web6/Bundle/XxxBundle --format=yml
```
In `app/CliKernel.php` è possibile individuare la seguente riga
```php
new \Web6\Bundle\XxxBundle\Web6XxxBundle(),
```
Questa riga va eliminata da `app/CliKernel.php` e aggiunta in `app/AppKernel.php`.
