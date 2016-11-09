# zeus-barcode-febraban
Implementa uma API para criação, manipulação e desenho de códigos de barras utilizados pela Federação Brasileira dos Bancos (Febraban)

## Examplo
Pacotes requeridos...
```json
{
    "require": {
        "rafsalvioni/zeus-barcode-febraban": "1.*",
        "rafsalvioni/zeus-barcode-renderer-svg": "1.*"
    }
}
```
Código de exemplo
```php
<?php
require 'vendor/autoload.php';

use Zeus\Barcode\Renderer\SvgRenderer;

$bcs = [
    new \Zeus\Barcode\Febraban\Bloqueto('03399.72101 20500.000110 04833.601018 4 67000000039211'),
    new \Zeus\Barcode\Febraban\Convenio('836000000007 839700481006 200471236816 001009939388'),
];

$render = new SvgRenderer();
$render->merge = true;

foreach ($bcs as &$bc) {
    $bc->border = 2;
    $bc->showText = true;
    $bc->draw($render);
    $render->offsetTop += $bc->getTotalHeight() + 50;
}
$render->render();
```
