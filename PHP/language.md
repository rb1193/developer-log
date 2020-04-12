# PHP Language

## Behaviours

In PHP, casting an array to an object will result in an instance of /stdClass with the array pairs set as attributes

If PHP is not properly recognizing the line endings when reading files either on or created by a Macintosh computer, enabling the auto_detect_line_endings configuration option may help resolve the problem

PHP magic methods can’t be mocked

PHP constants can’t be interpolated into strings

`transliterator_transliterate("Any-Latin; Latin-ASCII;", $str)` can be used to clean most strings before converting into URL slugs. It will replace any characters outside of the Latin ASCII character sets with their nearest approximation. Depends on the php-intl library being installed. Also has an OOP equivalent.

`json_decode($input)` returns NULL if the input is not valid JSON and cannot be decoded, unless the JSON_THROW_ON_ERROR option is set

PHP traits cannot have constants

### Requests

PHP does not receive keys in the $_POST array for empty HTML form checkboxes

When making a POST request with a JSON body, if you don’t specify the Content-Type header as ‘application/json’, PHP will not read the variables into the $_POST variable

## Configuration

The PHP ini mail.log option can be set to log mail() calls. Make sure the log file is writable by the web server
