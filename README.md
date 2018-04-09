# Fast, Secure, Random UUIDs

Pure PHP.

Generate RFC-4122 compliant
[random UUIDs](https://en.wikipedia.org/wiki/Universally_unique_identifier#Version_4_.28random.29)
with better
[statistical dispersion](https://en.wikipedia.org/wiki/Statistical_dispersion)
than `mt_rand()`, and **5x faster** than `create_uuid()`.


## Example Usage

If you are using composer, make sure you `require 'vendor/autoload.php`, then the code should Just Work™. Otherwise you can require `lib/Uuid.php` directly.

```php
<?php

use Jchook\Uuid;

Uuid::v4(); // 2ca24f61-2a32-45d0-93d1-409f944a43e1

?>
```

## Install w/ Composer

    composer require jchook/uuid


## Requirements

* PHP 7.0+


## Features

* Very fast!
* Pure PHP implementation
* Cryptographically secure PRNG


## Performance

Surprisingly, this library is **5x faster** than the [PECL UUID extension](https://pecl.php.net/package/UUID).

| package         | performance      |
|-----------------|------------------|
| PECL UUID       | 300k ops/sec     |
| **meter/uuid**  | **1.5M ops/sec** |


## Q&A

### What is UUID v4?

**U**niversally **U**nique **ID**entifiers transcend many constraints of
traditional incremental integer IDs, especially in distributed systems. Version
4 means that it's random, instead of being based on the current time, etc. This purely random ID [has](https://stackoverflow.com/questions/20342058/which-uuid-version-to-use) [many](http://www.sohamkamani.com/blog/2016/10/05/uuid1-vs-uuid4/) [advantages](https://stackoverflow.com/questions/703035/when-are-you-truly-forced-to-use-uuid-as-part-of-the-design/786541#786541).


### What about collisions?

The chance of a collision is so vanishingly small that it is [arguably smaller than UUID V1's collision probability](https://blogs.msdn.microsoft.com/oldnewthing/20160114-00/?p=92851). For scale, you would need to do-loop `Uuid::v4()` at max speed for 100,000 years to achieve a 50% chance of **one** collision.


## License

MIT
