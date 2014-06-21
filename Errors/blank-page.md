Error Blank Page
===

Se visitando l'URL dove risiede l'installazione di Sylius ottengo una pagina vuota, provare una delle seguenti soluzioni:

####Reset cache di APC
Sylius sta usando un acceleratore (per es. APC) e a seguito di qualche modifica (per es. cambio nome della dir del progetto) si presenta il problema. In questo caso bisogna cancellare la cache di APC, operazione che può essere eseguita lanciando il seguente comando:
```
# service httpd graceful
```
