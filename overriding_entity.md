Overriding entity
====
Creeremo la nuova entità `Product` sovrascrivendo quella di default presente nel path `Sylius\Component\Product\Model\Product.php`. La nuova entità esisterà nel dominio del nostro bundle, lasciando intatta l'entità di default.

Iniziamo creando la classe `Product.php` nel namespace `Web6\Bundle\XxxBundle\Entity`

.. code-block:: php

    <?php

    // src/Web6/Bundle/XxxBundle/Entity/Product.php
    namespace Web6\Bundle\XxxBundle\Entity;

    use Sylius\Bundle\ProductBundle\Model\Product as BaseProduct;

    class Product extends BaseProduct
    {
    }
