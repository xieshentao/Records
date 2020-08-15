---
date: 2020-08-15 12:10
status: public
title: PHP-工厂方法模式
---

# 简单工厂模式
>在`工厂方法模式`前，首先了解`简单工厂模式`，也称为静态工厂，不属于`GoF23`种设计模式。

```php
class Factory
{
    public static function createProduct(string $type) : Product
    {
        $product = null;
        switch ($type) {
            case 'A':
                $product = new ProductA();
                break;
            case 'B':
                $product = new ProductB();
                break;
        }
        return $product;
    }
}
```
>
产品接口和产品实现

```php
// Products
interface Product
{
    public function show();
}

class ProductA implements Product
{
    public function show()
    {
        echo 'Show ProductA';
    }
}

class ProductB implements Product
{
    public function show()
    {
        echo 'Show ProductB';
    }
}
------------------------------------------------
// Client
$productA = Factory::createProduct('A');
$productB = Factory::createProduct('B');
$productA->show();
$productB->show();
```
> 形象化一点的比喻：我是一个卖手机的批发商（客户Client，业务方），我需要一批手机（产品Product），于是我去让富士康（工厂Factory）来帮我生产。我下了订单（$type变量）指明型号，然后富士康就给我对应型号的手机，然后我就继续我的工作了，和富士康的合作还真是挺愉快的。<br/>
这里比较规范的写法可能是所有产品都会去实现一个统一的接口，然后客户端只知道接口的方法统一调用即可。不规范的话也可以不使用接口，返回各种不同的对象，类似于外观（Facade）模式进行统一的门面管理。














