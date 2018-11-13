# facebook-messenger-bundle

Use the [Kerox messenger repository](https://github.com/ker0x/messenger).

### Download the Bundle

```console
$ composer require yogradac/facebook-messenger-bundle
```

### Enable the Bundle

Registered bundles in the `app/AppKernel.php` file of your project:

```php
<?php
class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            // ...
            new Yogradac\FacebookMessengerBundle\FacebookMessengerBundle(),
        );
        // ...
    }
    // ...
}
```

### Config
Add this to config.yml:

```yaml
facebook_messenger:
    app_secret:     %facebook_messenger_app_secret%
    verify_token:   %facebook_messenger_verify_token%
    page_token:     %facebook_messenger_page_token%
    api_version:    %facebook_messenger_api_version%
```

### Example
Send text message:

```php
$messenger = $this->get('facebook_messenger.messenger');
$response = $messenger->broadcast()->create('Hello world');

$messenger->broadcast()->send($response->getMessageCreativeId());
```