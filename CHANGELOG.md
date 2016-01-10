# Nginx (`nginx`) - Change log

All notable changes to this role will be documented in this file.
This role adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased][unreleased]

## 2.0.0 - 05/01/2016

This role has been completely rewritten for this version. No backwards compatibility should be assumed.

### Changed - BREAKING!

* Nginx configuration file is now built from a hierarchy of (a) 'main', 'module' and 'additional' configuration files,
along with server block definition files
* Configuration options previously contained directly within the main configuration have been refactored to module,
additional or server block configuration files as needed
* All variables have been renamed, or serve a new purpose

### Removed - BREAKING!

* Direct support for generating server block definition files is removed

### Added

* Support for CentOS 7
* Support for configuring the system firewall automatically by generating a firewall service with rules based on 
configured listening ports, for a number of scenarios
* Templates for common server block definitions are made available for convenience in external tasks
* Testing using both CI and local manual testing using Vagrant and testing Ansible playbooks for common scenarios

## 1.0.1 - 01/04/2015

### Fixed

* Unnecessary change reporting for some tasks

### Changed

* Refactoring tasks

## 1.0.0 - 01/04/2015

### Changed - BREAKING!

* Updating default locations of SSL certificate and private key files

### Added

* Support for customising the interface the default virtual host will bind to and the ports used for HTTP and HTTPS traffic
* Support for Nginx PPA to ensure the latest stable version is installed

## 0.2.3 - 01/12/2014

### Changed

* Preparing role for public release

## 0.2.2 - 01/10/2014

### Added

* App user is now configurable using a variable

### Changed

* Updating dependencies
* Preparing for public release

## 0.2.1 - 01/10/2014

### Changed

* Adjusting role for inclusion in BARC
* Tasks cleanup

## 0.2.0 - 01/07/2014

### Added

* TLS/SSL support

## 0.1.0 - 01/07/2014

### Added

* Initial version
