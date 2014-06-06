Overriding template
====

####Riferimenti
- [Sylius doc](http://docs.sylius.org/en/latest/bundles/general/overriding_controllers.html?highlight=overriding)
- [Symfony doc](http://symfony.com/it/doc/current/cookbook/bundles/inheritance.html)

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
    defaults: { _controller: Web6XxxBundle:Homepage:main }
    #defaults: { _controller: sylius.controller.frontend.homepage:mainAction }
```
Modificare il file `src/Web6/Bundle/XxxBundle/Controller/HomepageController.php`:
```php
namespace Web6\Bundle\XxxBundle\Controller;
...
public function mainAction(){
	return $this->render('Web6XxxBundle:Default:index.html.twig');
}
```
Dove il file`src/Web6/Bundle/XxxBundle/Resources/views/Default/index.html.twig` contiene il seguente testo:
```html
Hello World!
```
