# Shopware on platform.sh
> Run test environments of your Shopware projects on platform.sh.

## Prerequisites

For plugin projects we assume a new-style (since 5.2) plugin. The plugin has to be the repository root, so no additional subfolder structure.

For shop projects we support both repositories with and without Shopware core files included.

## Usage

First create a platform.sh project for your repository.

Copy `.platform`, `.platform.app.yaml` and `.environment` into your project. Then edit `.environment`.

If your project is a plugin repository you can use the variable `PLUGIN_NAME`. During platform.sh environment creation the code will be copied as a plugin into Shopware.

If your project is a shop repository you can use the variable `PROJECT_ROOT` giving the subfolder where the Shopware root is located. If this is the repository root just use `.`.

### Additional plugins

If your plugin project requires additional plugins as a dependency - maybe you're building upon a Shopware Premium plugin - you can define those inside of `kellerkinder-plugin.json`. We support both URLs to ZIP archives as well as git repository URLs. See the example provided for the file structure.

Use `zip_url` or `clone_url` respectively. Please note that all URLs have to be publicly reachable. If you require authentication, add it to the URL.

### Media

If you're using real product data for your platform.sh environment you can specify an URL to a media ZIP archive in `.environment`. 
The archive will be downloaded for every deployment and unpacked in the shopware root directory. Therefor the archive has to contain the `media` directory with its subdirectories and files. 

Please note, your platform.sh project needs sufficient storage because of the additional space requirement of the archive and the unpacked media files.

### Elasticsearch / Enterprise Search

You can use and test your shop with Elasticsearch simply by uncommenting the neccessary parts in `.platform.app.yaml` (add the relationship) and `.platform/services.yaml` (add the service). Also change `USE_ELASTICSEARCH` to 1 in `.environment` and you're ready to go.

This also works with the Enterprise Search plugin.

## License

Distributed under the MIT license. See `LICENSE` for more information.


## Contributing

1. Fork it (<https://github.com/kellerkinderDE/platformsh-shopware/fork>)
2. Create your feature branch (`git checkout -b feature/my-additional-feature`)
3. Commit your changes (`git commit -am 'Add my feature'`)
4. Push to the branch (`git push origin feature/my-additional-feature`)
5. Create a new Pull Request
