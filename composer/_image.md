## intervention/image

[packagist](https://packagist.org/packages/intervention/image)

[usage](http://image.intervention.io/use/basics)

处理图片的各种方法集合，驱动支持 gd/imagick

Yii2 components 封装：

```php
<?php

namespace common\components;

use Intervention\Image\ImageManager;
use yii\base\BaseObject;

/**
 * @mixin ImageManager
 */
class Image extends BaseObject
{
    public $driver = 'gd'; // gd / imagick

    private $manager;

    public function init()
    {
        $this->manager = new ImageManager([
            'driver' => $this->driver,
        ]);
    }

    public function __call($name, $params)
    {
        return $this->manager->{$name}(...$params);
    }
}
```

## simplesoftwareio/simple-qrcode

[packagist](https://packagist.org/packages/simplesoftwareio/simple-qrcode)

生成二维码，支持中间带图片和色彩

Yii2 components 封装：

```php
<?php

namespace common\components;

use BaconQrCode\Renderer\Image\Png;
use SimpleSoftwareIO\QrCode\BaconQrCodeGenerator;
use yii\base\BaseObject;

/**
 * @mixin BaconQrCodeGenerator
 */
class QrCodeManager extends BaseObject
{
    public $defaultMargin = 0;
    public $defaultSize = 100;
    public $defaultEncoding = 'UTF-8';

    private $_qrCode = false;

    public function getQrCode()
    {
        if ($this->_qrCode === false) {
            $this->_qrCode = new BaconQrCodeGenerator(null, new Png());
            $this->_qrCode
                ->margin($this->defaultMargin)
                ->size($this->defaultSize)
                ->encoding($this->defaultEncoding);
        }
        return $this->_qrCode;
    }

    public function __call($name, $params)
    {
        return $this->getQrCode()->{$name}(...$params);
    }
}
```