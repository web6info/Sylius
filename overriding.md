Overriding
===
Aggiungere nel file /dir/progetti/progetto/composer.json la seguente riga:
```js
"sensio/generator-bundle": "~2.3",
```
Installare il "SensioGeneratorBundle" lanciando il seguente comando:
```bash
$ cd /dir/progetti/progetto/
$ php composer.phar update
```
Attivare il "SensioGeneratorBundle" modificando il file "AppKernel.php":
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
$ php app/console generate:bundle --namespace=Web6/XxxBundle --format=yml
```
Modificare il file "src/Web6/XxxBundle/Web6XxxBundle.php":
```php
namespace Web6\XxxBundle;
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
