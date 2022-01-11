# PHP와 문자열

## 1. single quoted & double quoted ('',"")
문자열을 표현하는 기호
```php
<!DOCTYPE html>
<html>
    <body>
        <h1>String & String Operator</h1>
        <?php
            echo 'Hello World';
        ?>

        <?php
            echo "Hello 'W'orld";
        ?>

        <?php
            echo "Hello \"W\"orld";
        ?>

        <h2>4/2</h2>
        <?php
            echo 4/2;
        ?>
    </body>
</html>
```

## 2. 문자열 결합 연산자
```php
<!DOCTYPE html>
<html>
    <body>
        <h1>concatenation operator</h1>
        <?php
            echo 'Hello'.'World';
        ?>
        <h1>String length function</h1>
        <?php
            echo strlen("Hello World");
        ?>
    </body>
</html>
```

