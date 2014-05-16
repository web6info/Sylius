Overriding
===

Aggiungere nel file /dir/progetti/progetto/composer.json la seguente riga:
```yaml
"sensio/generator-bundle": "~2.3",
```

    2. Installare il "SensioGeneratorBundle" lanciando il seguente comando:
    $ cd /dir/progetti/progetto/
    $ php composer.phar update

    3. Attivare il "SensioGeneratorBundle" modificando il file "AppKernel.php":
    public function registerBundles(){
        $bundles = array(
            ...
            new Sensio\Bundle\GeneratorBundle\SensioGeneratorBundle(),
        );
        ...
    }

    4. Creare il proprio bundle:
    $ php app/console generate:bundle --namespace=Web6/XxxBundle --format=yml

    5. Modificare il file "src/Web6/XxxBundle/Web6XxxBundle.php":
    namespace Web6\XxxBundle;
    use Symfony\Component\HttpKernel\Bundle\Bundle;
    class Web6XxxBundle extends Bundle{
        public function getParent(){ return 'SyliusWebBundle'; }
    }

    6. Per modificare il layout del frontend:
    $ cd ~/path/of/project/vendor/sylius/web-bundle/Sylius/Bundle/WebBundle/Controller
    $ cp -vR Frontend ~/path/of/project/src/Web6/XxxBundle/Controller
    $ cd ~/path/of/project/vendor/sylius/web-bundle/Sylius/Bundle/WebBundle/Resources/config
    $ cp -vR routing ~/path/of/project/src/Web6/XxxBundle/Resources/config
