## Google APIs Client

### Requirements

- [x] PHP
- [x] [Google API Keys](https://github.com/googleapis/google-api-php-client/tree/master/docs)
- [x] https://github.com/googleapis/google-api-php-client [`composer require google/apiclient:"^2.0"`]

### Example OAuth Client

#### [Using OAuth 2.0 for Web Server Applications](https://github.com/googleapis/google-api-php-client/blob/master/docs/oauth-web.md#create-authorization-credentials)
#### Пример клиента на PHP:

index.php
```php
<?php

require_once 'vendor/autoload.php';

$client = new Google_Client();
// нужно скачать с консоли json файл с правами и токенами: Client ID, Client Secret
$client->setAuthConfig('client_credentials.json');
$client->addScope('email'); // openid

// в консоли Google API должны быть прописаны redirect_url, например:
$redirect_uri = 'http://localhost:8001';
$client->setRedirectUri($redirect_uri);
// нужны для получения refresh_token
$client->setApprovalPrompt('force');
$client->setAccessType('offline');

echo '<a href="' .  $client->createAuthUrl() . '">Авторизация через Google</a>';

if (isset($_GET['code'])) {
    $token = $client->fetchAccessTokenWithAuthCode($_GET['code']);
    
    echo '<pre>';
    print_r($token);
}
```

1. Запускаем первый сервер: `php -S localhost:8000 index.php`
2. Запускаем второй сервер: `php -S localhost:8001 index.php`, сюда будет перенаправлять после авторизации и выводить необходимый массив на экран
