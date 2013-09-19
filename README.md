Dlin Symfony Geocoder Bundle
=========

Dlin Symfony Geocoder Bundle is wrapper bundle for  [dlin/geocoder]([https://github.com/dlin-me/geocoder) library :


Dlin Symfony Geocoder Bundle provides a configurable service to work with geocoding


***
Version
-

0.9


***
Installation
--------------


Installation using [Composer](http://getcomposer.org/)

Add to your `composer.json`:


    json
    {
        "require" :  {
            "dlin/geocoder-bundle": "dev-master"
        }
    }


Enable the bundle in you AppKernel.php


    public function registerBundles()
    {
        $bundles = array(
        ...
        new Dlin\Bundle\GeocoderBundle\DlinGeocoderBundle(),
        ...
    }


Configuration
--------------

You can specify multiple geocoding providers. For example:

    #app/config/config.yml

    dlin_geocoder:
        geocoder_service:
             Provider2:
				vendor: google
				weight: 19

			 Provider3:
				vendor: bing
				key: AvwNOuwxCZESwB9_p_RAHncR-oypS6UTsX5_g9u4Ejyt32G59_kKnvTSG3ySE3Q8
				weight: ~

		     Provider4:
				vendor: bing
				key: ApUmGCPD3VPcMRjlZUjVz1Z5uPHhlZYqA6Up9wvOVjQrYmJlygS3ftM87SHlIyx9
				weight: 5

For more information, please refere to the documentation of the  [dlin/geocoder]([https://github.com/dlin-me/geocoder) library



Usage
--------------

Geting the service in a controller

    $geocoder =  $this->get('dlin.geocoder_service');

Getting the service in a ContainerAwareService

    $geocoder = $this->container->get('dlin.geocoder_service');

Using the method "foward"


    $address = $geocoder->forward('1 Queen Street, Melbourne, Vic, AU');



Using the method "reverse"


    $address = $geocoder->reverse("-33.86687", "151.19565");



The returned $address

    $address = $geocoder->reverse("-33.86687", "151.19565");

    print_r($address);

    /* ========= out put ============

    Dlin\Geocoder\GeoAddress Object
    (
        [addressLine1] => 48 Pirrama Rd
        [addressLine2] =>
        [suburb] => Pyrmont
        [state] => NSW
        [postcode] => 2009
        [country] => Australia
        [latitude] => -33.86687
        [longitude] => 151.19565
        [partial] =>
        [formattedAddress] => 5/48 Pirrama Road, Pyrmont NSW 2009, Australia
        [geoCoding] => my bing
    )





License
--------------

MIT

*Free Software, Yeah!*


