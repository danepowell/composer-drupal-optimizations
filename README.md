Optimize Composer for Drupal projects
====
[![Build Status](https://travis-ci.org/zaporylie/composer-drupal-optimizations.svg?branch=master)](https://travis-ci.org/zaporylie/composer-drupal-optimizations)
[![Packagist](https://img.shields.io/packagist/v/zaporylie/composer-drupal-optimizations.svg)](https://packagist.org/packages/zaporylie/composer-drupal-optimizations)


# About

This composer-plugin contains set of improvements that makes running heavy duty composer commands (i.e. `composer update` or `composer require`) much faster.

# Installation

```bash
composer require zaporylie/composer-drupal-optimizations:^1.1
```

No configuration required 🎊

# Optimizations

- Reduce memory usage and CPU usage by removing legacy symfony tags

# Benchmark

Following numbers are for clean https://github.com/drupal-composer/drupal-project/ without and with this plugin.

Before:

```
Memory usage: 323.19MB (peak: 1121.09MB), time: 13.68s
```

After:

```
Memory usage: 238.66MB (peak: 297.17MB), time: 4.84s
```

> php 7.2, macOS High Sierra, i7, 16GB RAM

# Configuration

If no configuration is provided this package will provide sensible defaults based on the content of project's composer.json
file. Default configuration should cover 99% of the cases. However, in case you want to manually specify the tags
that should be filtered out you are welcome to use the `extra` section:

```json
{
  "extra": {
    "composer-drupal-optimizations": {
      "require": {
        "symfony/symfony": ">3.4"
      }
    }
  }
}
```

***Recommendation note:***
Use defaults (skip config above) if possible - this package will be maintained throughout the Drupal's lifecycle in order
to optimize legacy constraints in parallel with Drupal's requirements.

All you have to do is to make sure your drupal core constraint is set to `drupal/core: ^8.5` or above.

# Credits

- Symfony community - idea and development; Special thanks to @nicolas-grekas
- Jakub Piasecki - port and maintenance
