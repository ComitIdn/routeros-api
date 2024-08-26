# RouterOS PHP API Client

`routeros-api` is a PHP client library for interacting with MikroTik's RouterOS API. This library allows developers to remotely manage and monitor MikroTik devices by executing various RouterOS commands directly from their PHP applications.

## Features

- **Connection Management**: Easily connect to MikroTik RouterOS using IP, username, and password.
- **Command Execution**: Execute RouterOS commands and retrieve results in a structured format.
- **Data Parsing**: Automatically parse responses from RouterOS API into associative arrays for easy manipulation.
- **Error Handling**: Comprehensive error handling to capture and respond to connection issues or invalid commands.
- **Extensibility**: The library is designed to be extended and customized according to your specific needs.

## Use Cases

- **Network Monitoring**: Fetch and display traffic statistics, interface statuses, and other metrics from MikroTik devices.
- **Configuration Management**: Remotely change configurations, manage users, and update firmware on MikroTik routers.
- **Automation**: Automate repetitive tasks such as backup scheduling, user management, and network diagnostics.

## Requirements

- **PHP 7.2+**
- **MikroTik RouterOS with API enabled**

## Installation

You can include this library in your project using Composer.

### Quick Installation

To install this package quickly using Composer, run the following command:

```bash
composer require comitidn/routeros-api
```

# Manual Installation
Alternatively, you can manually add the package to your `composer.json` file:

## Step 1: Add the package to your Composer configuration
Add the following to your `composer.json` file:
```json
{
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/comitidn/routeros-api.git"
        }
    ],
    "require": {
        "comitidn/routeros-api": "dev-main"
    }
}
```
### Step 2: Install the package
Run the following command to install the package:
```bash
composer update
```
### Usage
Here's a basic example of how to use the `routeros-api` library:
```php
use RouterOSAPI\RouterOSAPI;

$api = new RouterOSAPI();
$api->connect('192.168.88.1', 'admin', 'password', 8728); // 8728 port default for API

// Example: Retrieve all interfaces
$api->write('/interface/print');
$interfaces = $api->read();

print_r($interfaces);

$api->disconnect();
```
### Advanced Usage
You can extend the basic usage to handle more complex tasks, such as:

- **Fetching Specific Data**: Filter results based on specific parameters.
- **Configuring Devices**: Send commands to change configurations on the router.
- **Error Handling**: Capture and handle errors during the API communication.
Example of filtering data:
```php
$api->write('/interface/print', false);
$api->write('?name=ether1', true);
$ether1 = $api->read();

print_r($ether1);
```
### Contributing
Contributions are welcome! If you have suggestions or bug reports, please open an issue or submit a pull request.

### License
This project is licensed under the MIT License. See the LICENSE file for details.

