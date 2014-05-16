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
$ cd /dir/progetti/progetto/src/Sylius/Bundle/WebBundle/Controller/Frontend
$ cp -vR HomepageController.php /dir/progetti/progetto/src/Web6/Bundle/XxxBundle/Controller

$ cd /dir/progetti/progetto/src/Sylius/Bundle/WebBundle/Resources/config
$ cp -vR routing ~/path/of/project/src/Web6/Bundle/XxxBundle/Resources/config
```

Modificare il file `app/config/routing.yml` nel seguente modo:
```yaml
#web6_xxx:
#    resource: "@Web6XxxBundle/Resources/config/routing.yml"
#    prefix:   /

...

sylius_web:
    resource: "@Web6XxxBundle/Resources/config/routing/main.yml"
    #resource: "@SyliusWebBundle/Resources/config/routing/main.yml"
```

Modificare il file `src/Web6/Bundle/XxxBundle/Resources/config/routing/main.yml`:
```yaml
sylius_frontend:
    resource: @Web6XxxBundle/Resources/config/routing/frontend/main.yml
    #resource: @SyliusWebBundle/Resources/config/routing/frontend/main.yml
...
```

Modificare il file `src/Web6/Bundle/XxxBundle/Resources/config/routing/frontend/main.yml`:
```yaml
sylius_homepage:
    pattern: /
    defaults: { _controller: Web6ViaggiBundle:Homepage:main }
    #defaults: { _controller: sylius.controller.frontend.homepage:mainAction }
```
