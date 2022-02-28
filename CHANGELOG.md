# Changelog
All notable changes to this project will be documented in this file.

## 1.0.10 - 2022-02-28
* Added support of multi-environment for feature flags, Related to [`activate_feature`](https://developers.kameleoon.com/ruby-sdk.html#activate_feature), [`obtain_feature_variable`](https://developers.kameleoon.com/ruby-sdk.html#obtain_feature_variable)
* Fixed issue with multiple adding CustomData with different values. Related to [`add_data`](https://developers.kameleoon.com/ruby-sdk.html#adddata)
* Added checking for status of site_code (Enable / Disable). Related to [`activate_feature`](https://developers.kameleoon.com/ruby-sdk.html#activate_feature) and trigger_experiment[`trigger_experiment`](https://developers.kameleoon.com/ruby-sdk.html#trigger_experiment)

## 1.0.9 - 2021-11-25
* Fix issues when [`obtain_variation_associated_data`](https://developers.kameleoon.com/ruby-sdk.html#obtain_variation_associated_data) and [`obtain_feature_variable`](https://developers.kameleoon.com/ruby-sdk.html#obtain_feature_variable) return wrong values
* Fix issue when activate_feature[`activate_feature`](https://developers.kameleoon.com/ruby-sdk.html#activate_feature) doesn't send tracking data
* Fix issue when activate_feature[`obtain_feature_variable`](https://developers.kameleoon.com/ruby-sdk.html#obtain_feature_variable) doesn't return JSON values
* Fix targeting issue when activate_feature[`activate_feature`](https://developers.kameleoon.com/ruby-sdk.html#activate_feature) and trigger_experiment[`trigger_experiment`](https://developers.kameleoon.com/ruby-sdk.html#trigger_experiment) can be not target.
* Fix issue when tracking request sends many times instead of once. Related to activate_feature[`activate_feature`](https://developers.kameleoon.com/ruby-sdk.html#activate_feature) and trigger_experiment[`trigger_experiment`](https://developers.kameleoon.com/ruby-sdk.html#trigger_experiment)
* Fix wording: Correct VariationConfigurationNotFound wording.

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
