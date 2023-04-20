# Changelog
All notable changes to this project will be documented in this file.

## 2.1.0 - 2023-04-20
* Added update campaigns and feature flag configurations instantaneously with Real-Time Streaming Architecture: [`Documentation`](https://developers.kameleoon.com/ruby-sdk.html#streaming) or [`Product Updates`](https://www.kameleoon.com/en/blog/real-time-streaming)
* Added a new methods:
    - [`on_update_configuration`](https://developers.kameleoon.com/ruby-sdk.html#on_update_configuration) to handle events when configuration data is updated in real time.
    - [`get_engine_tracking_code`](https://developers.kameleoon.com/ruby-sdk.html#get_engine_tracking_code) which can be used to simplify utilization of hybrid mode
* Renaming of methods:
    - `obtain_feature_variable` -> [`get_feature_variable`](https://developers.kameleoon.com/ruby-sdk.html#get_feature_variable)
    - `retrieve_data_from_remote_source` -> [`get_remote_date`](https://developers.kameleoon.com/ruby-sdk.html#get_feature_variable)
* Added possibility for [`CustomData`](https://developers.kameleoon.com/ruby-sdk.html#customdata) to use variable argument list of values

## 2.0.0 - 2023-02-02
* Significantly improved configuration load time
* Added support of new feature flag rules:
    - [`get_feature_variation_key`](https://developers.kameleoon.com/ruby-sdk.html#get_feature_variation_key)
    - [`get_feature_variable`](https://developers.kameleoon.com/ruby-sdk.html#get_feature_variable)
    - [`get_feature_all_variables`](https://developers.kameleoon.com/ruby-sdk.html#get_feature_all_variables)
    - `activate_feature` -> [`feature_active?`](https://developers.kameleoon.com/ruby-sdk.html#feature_active)
* Methods added for obtaining experiment and feature flag:
    - [`get_experiment_list`](https://developers.kameleoon.com/ruby-sdk.html#experiment_list)
    - [`get_experiment_list_for_visitor`](https://developers.kameleoon.com/ruby-sdk.html#experiment_list_for_visitor)
    - [`get_feature_list`](https://developers.kameleoon.com/ruby-sdk.html#get_feature_list)
    - [`get_active_feature_list_for_visitor`](https://developers.kameleoon.com/ruby-sdk.html#get_active_feature_list_for_visitor)
* Renaming of methods:
    - `obtain_visitor_code` -> [`get_visitor_code`](https://developers.kameleoon.com/ruby-sdk.html#get_visitor_code)
    - `obtain_variation_associated_data` -> [`get_variation_associated_data`](https://developers.kameleoon.com/ruby-sdk.html#get_variation_associated_data)
* Changes in Kameleoon Data:
    - Added Kameleoon [`Device`](https://developers.kameleoon.com/ruby-sdk.html#device) data. Possible values are: **PHONE**, **TABLET**, **DESKTOP**.
    - Added possibility to set [`UserAgent`](https://developers.kameleoon.com/ruby-sdk.html#useragent).
    - Removed Kameleoon `Interest` data.
* Renaming of exceptions:
    - `NotActivated` -> `NotAllocated`
* Removed blocking mode of SDK.
* Added support of `is among the values` operator for Custom Data
* Added support for **Experiment** & **Exclusive Campaign** conditions. Related to [`trigger_experiment`](https://developers.kameleoon.com/ruby-sdk.html#trigger_experiment)

## 1.1.2 - 2022-07-08
* Significantly improved SDK stability

## 1.1.1 - 2022-07-04
* Fixed using default value if [`actions_configuration_refresh_interval`](https://developers.kameleoon.com/ruby-sdk.html#additional-configuration) parameter is not set in config file

## 1.1.0 - 2022-04-12
* Added method for retrieving data from remote source: [`retrieve_data_from_remote_source`](https://developers.kameleoon.com/ruby-sdk.html#retrieve_data_from_remote_source)

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
