# Changelog
All notable changes to this project will be documented in this file.

## 3.9.0 - 2025-02-26
### Features
* Added SDK support for **Mutually Exclusive Groups**. When feature flags are grouped into a **Mutually Exclusive Group**, only one flag in the group will be evaluated at a time. All other flags in the group will automatically return their default variation.

## 3.8.0 - 2025-02-10
### Features
* Added SDK support for **holdout experiments**. Visitors assigned to a holdout experiment are excluded from all other rollouts and experiments, and consistently receive the default variation. For visitors not in a holdout experiment, the standard evaluation process applies, allowing them to be evaluated for all feature flags as usual. Platform-wide release expected in February 2025.

## 3.7.0 - 2024-12-16
### Features
* Added support for **simulated** variations.
* Added the [`set_forced_variation()`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#set_forced_variation) method. This method allows explicitly setting a forced variation for a visitor, which will be applied during experiment evaluation.
### Bug fixes
* Fixed an issue where the [`Variation.active?`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#variation) method raised `NameError`.

## 3.6.1 - 2024-11-20
### Bug fixes
* Resolved an issue where the validation of [top-level domains](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#configure-the-client) for `localhost` resulted in incorrect failures. The SDK now accepts the provided domain without modification if it is deemed invalid and logs an [error](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#log-levels) to notify you of any issues with the specified domain.

## 3.6.0 - 2024-11-14
### Features
* Introduced a new `visitor_code` parameter to [`RemoteVisitorDataFilter`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#using-parameters-in-get_remote_visitor_data). This parameter determines whether to use the `visitor_code` from the most recent previous visit instead of the current `visitor_code`. When enabled, this feature allows visitor exposure to be based on the retrieved `visitor_code`, facilitating [cross-device reconciliation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation/). Default value of the parameter is `true`.
### Bug fixes
* Fixed an issue with the [`Page URL`](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments/#benefits-of-calling-getremotevisitordata) and [`Page Title`](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments/#benefits-of-calling-getremotevisitordata) targeting conditions, where the condition evaluated all previously visited URLs in the session instead of only the current URL, corresponding to the latest added [`PageView`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#pageview).<br/>
**NOTE**: This change may impact your existing targeting. Please review your targeting conditions to ensure accuracy.

## 3.5.0 - 2024-10-04
### Features
* Introduced new evaluation methods for clarity and improved efficiency when working with the SDK:
  - [`get_variation`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#get_variation)
  - [`get_variations`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#get_variations)
* These methods replace the deprecated ones:
  - [`get_feature_variation_key`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_feature_variation_key)
  - [`get_feature_variable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_feature_variable)
  - [`get_active_features`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_active_features)
  - [`get_feature_variation_variables`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_feature_variation_variables)
* A new version of the [`feature_active?`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#feature_active) method now includes an optional `track` parameter, which controls whether the assigned variation is tracked (default: `true`).
* Enhanced top-level domain validation within the SDK. The implementation now includes automatic trimming of extraneous symbols and provides a [warning](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#log-levels) when an invalid domain is detected.
* Enhanced the [`get_engine_tracking_code`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#getenginetrackingcode) method to properly handle `JS` and `CSS` variables.

## 3.4.0 - 2024-08-15
### Features
* Improved the tracking mechanism to consolidate multiple visitors into a single request. The new approach combines information on all affected visitors into one request, which is sent once per interval.
* Added a new parameter `instant` of the [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#flush) method. If the parameter's value is `true` the visitor's data is tracked instantly. Otherwise, the visitor's data will be tracked with next tracking interval. Default value of the parameter is `false`.
* Added new configuration parameter `tracking_interval_millisecond` to [`KameleoonClientConfig`](https://developers.kameleoon.com/ruby-sdk.html#initialize-the-client) and the [configuration](https://developers.kameleoon.com/ruby-sdk.html#configure-the-client) file, which is used to set interval for tracking requests. Default value is `1000` milliseconds.
* New Kameleoon Data type [`UniqueIdentifier`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#uniqueidentifier) is introduced. It will be used in all methods instead of `is_unique_identifier` parameter. All usages of the `is_unique_identifier` parameter in the methods are marked as deprecated:
    - [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#flush)
    - [`track_conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#track_conversion)
    - [`get_feature_variation_key`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_feature_variation_key)
    - [`get_feature_variable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_feature_variable)
    - [`feature_active?`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#feature_active)
    - [`get_remote_visitor_data`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_remote_visitor_data)
* Enhanced [logging](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#logging):
  - Introduced [log levels](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#log-levels):
    - `NONE`
    - `ERROR`
    - `WARNING`
    - `INFO`
    - `DEBUG`
  - Added support for [custom logger](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#custom-handling-of-logs) implementations.
* Changed the parameter `verbose_mode` in object [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#configure-the-client) the deprecated.
### Bug fixes
* Resolved an issue where the [`flush(nil, is_unique_identifier)`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#flush) method was incorrectly sending requests with `is_unique_identifier` applied to each visitor. Now, `is_unique_identifier` is only considered if `visitor_code` is provided and not nil.
* Fixed an issue that caused duplicate entries in feature flag results for both anonymous and authorized/identified visitors during data reconciliation. This problem occurred when custom data of type mapping ID was not consistently sent for all sessions.

## 3.3.0 - 2024-06-21
### Features
* The [Likelihood to convert](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments) targeting condition is now available. Pre-loading the data is required using [`get_remote_visitor_data`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#get_remote_visitor_data) with the `kcs` parameter set to `true`.
* Added [`get_active_features`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#getactivefeatures) method. It retrieves information about the active feature flags that are available for a specific visitor code. This method replaces the deprecated [`get_active_feature_list_for_visitor`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#getactivefeaturelistforvisitor) method.

## 3.2.0 - 2024-05-22
### Features
* New targeting conditions are now available (some of them may require [`get_remote_visitor_data`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk#getremotevisitordata) pre-loaded data)
  - Browser Cookie
  - Operating System
  - IP Geolocation
  - Kameleoon Segment
  - Target Feature Flag
  - Previous Page
  - Number of Page Views
  - Time since First Visit
  - Time since Last Visit
  - Number of Visits Today
  - Total Number of Visits
  - New or Returning Visitor
* New Kameleoon Data types were introduced:
  - [`Cookie`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#cookie)
  - [`OperatingSystem`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#operatingsystem)
  - [`Geolocation`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#geolocation)
* Changed the parameter `title` in object [`PageView`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#pageview) to optional.
### Bug fixes
* Stability and performance improvements

## 3.1.1 - 2024-02-27
### Bug fixes
* Stability and performance improvements

## 3.1.0 - 2024-02-22
### Features
* Added support for additional Data API servers across the world for even faster network requests.
* Increased limit for requests to Data API: [rate limits](https://developers.kameleoon.com/apis/data-api-rest/overview/#rate-limits)
* Added [`get_visitor_warehouse_audience`](https://developers.kameleoon.com/ruby-sdk.html#get_visitor_warehouse_audience) method to retrieve all data associated with a visitor's warehouse audiences and adds it to the visitor.
### Bug fixes
* Stability and performance improvements

## 3.0.0 - 2023-12-13
### Breaking changes
* Removed all previously deprecated methods and exceptions related to **experiments** (use feature experiments instead):
  * Methods:
    - `trigger_experiment`
    - `get_variation_associated_data`
    - `get_experiment_list`
    - `get_experiment_list_for_visitor`
  * Exceptions:
    - `ExperimentConfigurationNotFound`
    - `NotTargeted`
    - `NotAllocated`
    - `SiteCodeDisabled`
* Removed all other methods that were deprecated in 2.x versions:
    - `obtain_visitor_code`
    - `activate_feature`
    - `obtain_variation_associated_data`
    - `obtain_feature_variable`
    - `retrieve_data_from_remote_source`
* Changed the following classes, methods, and exceptions:
    * Classes:
        - Renamed `ClientConfig` to [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#initializing-the-kameleoon-client)
        - Renamed `ClientFactory` to [`KameleoonClientFactory`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#kameleoonclientfactory)
        - Renamed `Client` to [`KameleoonClient`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#initializing-the-kameleoon-client)
    * Methods:
        - Renamed `get_feature_all_variables` method to [`get_feature_variation_variables`](https://developers.kameleoon.com/ruby-sdk.html#get_feature_variation_variables)
        - Removed `make_from_yaml` method from [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#initializing-the-kameleoon-client). If you used the method please use `read_from_yaml` instead.
    * Exceptions:
        - Renamed `VisitorCodeNotValid` to `VisitorCodeInvalid`
        - Renamed `FeatureConfigurationNotFound` to `FeatureNotFound`
        - Renamed `VariationConfigurationNotFound` to `FeatureVariationNotFound`
        - Renamed `CredentialsNotFound` to `ConfigCredentialsInvalid`
        - Added `SiteCodeIsEmpty` exception, which the [`KameleoonClientFactory.create`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#create) method raises if the specified site code parameter is `nil` or empty.
* Changed [configuration fields](https://developers.kameleoon.com/ruby-sdk.html#additional-configuration):
    - removed `visitor_data_maximum_size` field
    - renamed `configuration_refresh_interval` to [`refresh_interval_minute`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#additional-configuration)
    - renamed `default_timeout` to [`default_timeout_millisecond`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#additional-configuration)
    - changed [`client_id`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#additional-configuration) and [`client_secret`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#additional-configuration) to required fields. `Exception::ConfigCredentialsInvalid` is now raised if `client_id` and `client_secret` are not specified.
* Added new exception [`Exception::FeatureEnvironmentDisabled`] indicating that the feature flag is disabled for certain environments. The following methods can throw the new exception:
    - [`get_feature_variation_key`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#get_feature_variation_key)
    - [`get_feature_variable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#get_feature_variable)
    - [`get_feature_variation_variables`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#get_feature_variation_variables)
* Removed `top_level_domain` parameter from [`get_visitor_code`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#get_visitor_code).
* Reworked [`CustomData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#customdata):
    - Changed the data type of the `id` field to `Integer`
    - Removed the `value` hash parameter due to the deprecation

### Features
* Added new parameters for [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#initializing-the-kameleoon-client):
    - `session_duration_minute`
    - `top_level_domain`
* Added [`set_legal_consent`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#set_legal_consent) method to determine the types of data Kameleoon includes in tracking requests. This helps you adhere to legal and regulatory requirements while responsibly managing visitor data. You can find more information in the [Consent management policy](https://help.kameleoon.com/consent-management-policy/).
* Added new error `Exception::SiteCodeIsEmpty` which is raised if provided site code is `nil` or empty.

### Bug fixes
* Stability and performance improvements

## 2.3.0 - 2023-10-02
### Features
* We are pleased to introduce an enhancement that simplifies the configuration of the `Kameleoon::Client`. We have added a configuration option called [`Kameleoon::ClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#initializing-the-kameleoon-client). With this option, you don't need an external settings file when you initialize the client. You can apply the new configuration option using the [`Kameleoon::ClientFactory.create`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#create) method.

## 2.2.0 - 2023-09-14
### Features
* Added [`get_remote_visitor_data`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#get_remote_visitor_data) method to fetch a visitor's remote data (with an optional capability to add the fetched data to the visitor)
### Bug fixes
* Stability and performance improvements

## 2.1.1 - 2023-08-28
### Features
* Added new conditions for targeting:
    - `Visitor Code`
    - `SDK Language`
    - [`Page Title & Page Url`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#pageview)
    - [`Browser`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#browser)
    - [`Device`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#device)
    - [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/ruby-sdk/#tracking-conversion)
### Bug fixes
* Stability and performance improvements

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
