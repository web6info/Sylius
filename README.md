[Installare Sylius](https://github.com/Sylius/Sylius/blob/master/README.md#sylius--)
===

1. Scaricare i file dal [**repository**](https://github.com/Sylius/Sylius) github di Sylius:
```bash
$ cd /directory/dei/progetti
$ git clone https://github.com/Sylius/Sylius.git
```

2. Modificare il file /directory/dei/progetti/Sylius/composer.json come segue (fonte):
```bash
"symfony/icu": "1.1.0",
"symfony/symfony": "2.4.*",
```

3. Per creare il progetto lanciare i seguenti comandi:
```bash
$ cd /directory/dei/progetti/Sylius
$ php composer.phar create-project
```

4. Quando chiede user e pass inserire le proprie credenziali di github

5. Per installare la distribuzione "prod" lanciare il seguente comando:
```bash
$ app/console sylius:install -e prod --no-debug
```
