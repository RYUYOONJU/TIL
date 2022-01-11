# PHP와 숫자

## 1. integer
정수를 표현한다.(음수~자연수)
```php
<?php
    echo 1;
    print(1);
?>
```
* echo,print는 출력할때 쓰는 php언어
* php는 하나의 구문이 끝나면 세미콜론을 찍어야한다.

## 2. float
부동소수점을 표현한다. (소수점이 있는 실수)
```php
<?php
    echo 1.1;
    print(1.1);
?>
```

## 3. 숫자의 연산
```php
<!DOCTYPE html>
<html>
    <body>
        <h1>Number & Arithmetic Operator</h1>
        <h2>1+1</h2>
        <?php
            echo 1+1;
        ?>

        <h2>2-1</h2>
        <?php
            echo 2-1;
        ?>

        <h2>2*2</h2>
        <?php
            echo 2*2;
        ?>

        <h2>4/2</h2>
        <?php
            echo 4/2;
        ?>
    </body>
</html>
```