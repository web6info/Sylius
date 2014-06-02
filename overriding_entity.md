Overriding entity
====
[Silius doc](http://docs.sylius.org/en/latest/bundles/general/overriding_models.html?highlight=overriding)

Creeremo la nuova entità `Product` sovrascrivendo quella di default presente nel path `Sylius\Component\Product\Model\Product.php`. La nuova entità esisterà nel dominio del nostro bundle, lasciando intatta l'entità di default.

Iniziamo creando la classe `Product.php` nel namespace `Web6\Bundle\XxxBundle\Entity`

```php
<?php

// src/Web6/Bundle/XxxBundle/Entity/Product.php
namespace Web6\Bundle\XxxBundle\Entity;

use Sylius\Component\Product\Model\Product as BaseProduct;

class Product extends BaseProduct{
}
```
Adesso definiamo il mapping per questa entità.
È necessario creare il file di mapping nel path `src/Web6/Bundle/ViaggiBundle/Resources/config/doctrine/Product.orm.xml`:
```xml
<?xml version="1.0" encoding="UTF-8"?>

<doctrine-mapping xmlns="http://doctrine-project.org/schemas/orm/doctrine-mapping"
                         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                         xsi:schemaLocation="http://doctrine-project.org/schemas/orm/doctrine-mapping
                                             http://doctrine-project.org/schemas/orm/doctrine-mapping.xsd">

    <entity name="Web6\Bundle\XxxBundle\Entity\CartItem" table="web6_product">
    </entity>

</doctrine-mapping>
```
Non è necessario mappare il campo *ID* dal momento che questo è già mappato nella classe
`Sylius\Component\Product\Model\Product`.
