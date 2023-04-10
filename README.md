## knowledge-base

The [documentation](https://maggomann.github.io/knowledge-base/) is under construction.

## Installation and Usage

### Step 1: Install Python 3

Make sure that Python 3 is installed on your system. If you haven't installed Python 3 yet, you can download it from the
[Python website](https://www.python.org/downloads/).

### Step 2: Install Pip3

Pip3 is the package manager for Python 3. To install Pip3, run the following command:

```bash
    sudo apt install python3-pip
```

or

```bash
    sudo apt-get install python3-pip
```

### Step 3: Install MkDocs

MkDocs is the tool used for building static websites. To install MkDocs, run the following command:

```bash
    pip3 install mkdocs
```

### Step 4: Install Plugins

Install the required plugins for MkDocs with the following command:

```bash
    pip3 install mkdocs-material pymdown-extensions mkdocs-minify-plugin mkdocs-i18n glightbox pdf-export mkdocs-search
```

### Step 5: Build the Documentation

To build the documentation, run the following command:

```bash
    mkdocs build
```

### Step 6: Serve the Documentation Locally

To serve the documentation locally, run the following command:

```bash
    mkdocs serve
```

Then navigate to [http://localhost:8000](http://localhost:8000) in your browser.

### Notes

Step 2 and 4 installations may require root permissions on your system. Therefore, use sudo before the corresponding commands if you don't have root permissions.

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Marco Ehrt](https://github.com/Maggomann)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
