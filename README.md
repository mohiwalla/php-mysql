# PHP-MySQL Database Wrapper

This is a simple PHP class that provides a wrapper around the MySQL database using the MySQLi extension. It abstracts the database connection and query execution, making it easier to interact with a MySQL database in your PHP projects.

## Features

- Establishes a connection to the MySQL database using the provided credentials.
- Executes SQL queries using prepared statements, which helps prevent SQL injection attacks.
- Provides a method to execute stored procedures with parameters.
- Fetches all rows from a MySQL result set and applies an optional callback to each row.
- Automatically closes the database connection when the object is destroyed.

### Installation

To install the utility, you can use Composer. Add the following to your `composer.json` file:

```json
{
	"require": {
		"mohiwalla/php-mysql": "1.0.0"
	}
}
```

Then run:

```sh
composer install
```

OR just run this command directly:

```sh
composer require mohiwalla/php-mysql
```

## Usage

Here's an example of how to use the `DB` class:

```php
require __DIR__ . "/vendor/mohiwalla/php-mysql/index.php";

$con = new DB("localhost", "root", "", "shoppy");
$query = "SELECT * FROM users;";
$result = $con->query($query);

while ($row = mysqli_fetch_object($result)) {
    echo print_r($row, true);
}
```

## Methods

### `__construct(string $host, string $user, string $password, string $database)`

Initializes a new instance of the `DB` class, establishing a connection to the MySQL database using the provided host, user, password, and database name. If the connection fails, the script exits with an error message.

### `query(string $query, ...$values)`

Executes a SQL query using a prepared statement with the given parameters. This function prepares and executes the query, handling the binding of the provided parameters to the query and returning the result object.

### `procedure(string $name, ...$values)`

Executes a stored procedure with the given name and parameters. This function constructs a SQL query to call the stored procedure using placeholders for the parameters, then prepares and executes the query.

### `fetchAll($result, callable $callback = null)`

Fetches all rows from a MySQL result set and applies an optional callback to each row. This method iterates over the result set, fetches each row as an associative array, optionally applies a user-defined callback to each row, and collects the rows in an array.

## Contributing

If you encounter any issues or have suggestions for improvements, please feel free to open an issue or submit a pull request on the [GitHub repository](https://github.com/your-username/php-mysql-wrapper).

## License

This project is licensed under the [MIT License](LICENSE).