# Stamps.com Shipping Label API Client

A handy-dandy Stamps.com API integration to generate shipping labels.

### Usage

```php
$to = (new \Slicvic\Stamps\Address\Address)
    ->setFullname('Neymar Jr')
    ->setAddress1('100 Ocean Drive')
    ->setAddress2('#200')
    ->setCity('Miami Beach')
    ->setState('Florida')
    ->setZipcode('33139')
    ->setCountry('US');

$from = (new \Slicvic\Stamps\Address\Address)
    ->setFullname('Leonel Messi')
    ->setAddress1('300 Broadway')
    ->setAddress2('#400')
    ->setCity('New York City')
    ->setState('NY')
    ->setZipcode('10001')
    ->setCountry('US');

try {
    $shippingLabel = new \Slicvic\Stamps\Api\ShippingLabel('API_URL');
    $shippingLabel
        ->setApiIntegrationId('YOUR_API_INTEGRATION_ID')
        ->setApiUserId('YOUR_API_USER_ID')
        ->setApiPassword('YOUR_API_PASSWORD')
        ->setImageType(\Slicvic\Stamps\Api\ShippingLabel::IMAGE_TYPE_PNG)
        ->setPackageType(\Slicvic\Stamps\Api\ShippingLabel::PACKAGE_TYPE_THICK_ENVELOPE)
        ->setServiceType(\Slicvic\Stamps\Api\ShippingLabel::SERVICE_TYPE_FC)
        ->setFrom($from)
        ->setTo($to)
        ->setIsSampleOnly(false)
        ->setWeightOz(100)
        ->setShipDate('2018-01-17')
        ->setShowPrice(false);

    // Generate label and get URL to the PDF or PNG
    // Takes an optional filename argument to save label to file
    $labelUrl = $shippingLabel->create();
} catch(Exception $e) {
    // Handle exception
}
```
