Overriding
====

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
Modificare il file `src/Web6/Bundle/XxxBundle/Web6XxxBundle.php`:
```php
namespace Web6\Bundle\XxxBundle;
use Symfony\Component\HttpKernel\Bundle\Bundle;
class Web6XxxBundle extends Bundle{
    public function getParent(){ return 'SyliusWebBundle'; }
}
```
Per modificare il layout del frontend:

```bash
$ cd ~/path/of/project/vendor/sylius/web-bundle/Sylius/Bundle/WebBundle/Controller
$ cp -vR Frontend ~/path/of/project/src/Web6/XxxBundle/Controller
$ cd ~/path/of/project/vendor/sylius/web-bundle/Sylius/Bundle/WebBundle/Resources/config
$ cp -vR routing ~/path/of/project/src/Web6/XxxBundle/Resources/config
```
