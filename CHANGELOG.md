# Change Log
All notable changes to this project will be documented in this file.

## 1.0.8
* Fix issue: Allow Integer for default visitorCode.

## 1.0.7
* Fix issue: Allow default visitorCode length till 255 chars.
* New exception: raise VisitorCodeNotValid if visitorCode is empty or too long.

## 1.0.6
* Fix issue: experiments with status DEVIATED were not fetched.

## 1.0.5
* Fix issue: tracking experiment without data
* Added 'Kameleoon-Client' header with version for tracking requests

## 1.0.4
* Fix issue: targeting experiment without segment

## 1.0.3
* Add verbose mode, complete tests

## 1.0.2
* Remove TLS warning

## 1.0.1
* Fix multiple exceptions names.
* Return Hash for `obtain_variation_associated_data`.
* Update entry for `actions_configuration_refresh_interval` to accept only number as amount of minutes.

## 1.0.0
* Create new Kameleoon client ruby SDK
