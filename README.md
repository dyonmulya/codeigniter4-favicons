<h1 align="center">CodeIgniter 4 Favicons</h1>

<h6 align="center">A codeigniter 4 library to auto generate favicons to your main application.</h6>

<p align="center">
    <a target="_blank" title="Stars" href="https://github.com/dyonmulya/codeigniter4-favicons/stargazers"><img alt="Stars" src="https://img.shields.io/github/stars/dyonmulya/codeigniter4-favicons.svg"/></a>&nbsp;
    <a target="_blank" title="Packagist Version" href="https://github.com/dyonmulya/codeigniter4-favicons/releases"><img alt="Packagist Version" src="https://img.shields.io/packagist/v/dyonmulya/codeigniter4-favicons"/></a>&nbsp;
    <a target="_blank" title="License" href="LICENSE"><img alt="License" src="https://img.shields.io/github/license/dyonmulya/codeigniter4-favicons"/></a>&nbsp;
</p>

<p align="center">
    <a>Getting Started</a>&nbsp;&middot;&nbsp;
    <a>Generate Favicons</a>&nbsp;&middot;&nbsp;
    <a>Generate Tags</a>
</p>

<a href="https://www.svgrepo.com/svg/485006/balloon-flat-icon-part-2"><img align="center" alt="Favicons" src="https://miro.medium.com/v2/resize:fit:1400/0*YWWu79bmNumsH1m7.png"/></a>

<h2>Getting Started</h2>

<h3>Requirements</h3>
<p>
    <ul>
        <li>PHP version 8.1 or higher</li>
        <li>CodeIgniter version 4.1 or higher</li>
        <li>
            Image Processing Extension, like:
            <ul>
                <li>Imagick</li>
                <li>Gd</li>
            </ul>
        </li>
    </ul>
</p>

<h3>Installation</h3>

<h4>Packagist (Composer)</h4>

```bash
composer require dyonmulya/codeigniter4-favicons
```

<h4>Manual Installation</h4>

<p>Should you choose not to use Composer to install, you can clone or download this repo and then enable it by editing <strong>app/Config/Autoload.php</strong> and adding the <code>DyonMulya\Codeigniter4Favicons</code> namespace to the <code>$psr4</code> array. For example, if you copied it into <strong>app/ThirdParty/</strong>:</p>

```php
$psr4 = [
    'Config'      => APPPATH . 'Config',
    APP_NAMESPACE => APPPATH,
    'App'         => APPPATH,
    'DyonMulya\CodeIgniter4Favicons'   => APPPATH . 'ThirdParty/codeigniter4-favicons/src',
];
```

<h3>Publish</h3>

<p>After installation, run the following command to publish to your main application.</p>

```bash
php spark publish
```

<h3>Configuration</h3>

<h4>app/Config/App.php</h4>

```php
class App extends BaseConfig {
    ...
    /**
     * ---------------------------------------------------
     * Name
     * ---------------------------------------------------
     * 
     * Used to specify the full name of your web application as it's usually displayed to users, such as in application lists or as a label for your application's icon.
     * 
     * @link https://w3c.github.io/manifest/#name-member
     * 
     * @var string
     */
    public string $name = 'SET_YOUR_APPLICATION_NAME';

    /**
     * ---------------------------------------------------
     * Short Name
     * ---------------------------------------------------
     * 
     * Used to specify a short name for your application, which may be used when the full name (`$name`) is too long for the available space.
     * 
     * @link https://w3c.github.io/manifest/#short_name-member
     * 
     * @var string
     */
    public string $short_name = 'SET_YOUR_APPLICATION_SHORT_NAME';

    /**
     * ---------------------------------------------------
     * Description
     * ---------------------------------------------------
     * 
     * Used to explain the core features or functionality of your application.
     * 
     * @link https://w3c.github.io/manifest-app-info/#description-member
     * 
     * @var string
     */
    public string $description = 'SET_YOUR_APPLICATION_DESCRIPTION';

    /**
     * @var string
     */
    public string $logo = 'SET_YOUR_FILEPATH_APPLICATION_LOGO';

    /**
     * ---------------------------------------------------
     * Categories
     * ---------------------------------------------------
     * 
     * Specify one or more classifications for your application. These categories help users discover your app in app stores.
     * 
     * @link https://w3c.github.io/manifest-app-info/#categories-member
     * 
     * @var array
     */
    public array $categories = ['SET_YOUR_APPLICATION_CATEGORY'];

    /**
     * ---------------------------------------------------
     * Display
     * ---------------------------------------------------
     * 
     * Used to specify your preferred display mode for the application. The display mode determines how much of the browser UI is shown to the user when the app is launched within the context of an operating system. You can choose to show the full browser interface or hide it to provide a more app-like experience.
     * 
     * A string with keyword values. If not specified, the default value browser is used. The keyword values include:
     * 
     * 'fullscreen' : Opens the app with browser UI elements hidden and uses the entirety of the available display area. Use this value for apps where fullscreen engagement is crucial and desired. For example, use it for a game app that can take up the entire screen without any browser controls visible, providing a fully immersive gaming experience.
     * 'standalone' : Opens the app to look and feel like a standalone native app. This can include the app having a different window and its own icon in the app launcher. The browser will exclude UI elements such as a URL bar but can still include other UI elements such as the status bar. For example, use it for a task manager app that opens in its own window without the browser's URL bar, while still displaying the device's status bar for battery and notifications, thereby providing an integrated experience.
     * 'minimal-ui' : Opens the app to look and feel like a standalone app but with a minimal set of UI elements for navigation. The specific elements can vary by browser but typically include navigation controls like back, forward, reload, and possibly a way to view the app's URL. Additionally, the browser may include platform-specific UI elements that provide functionality for sharing and printing content. Use this value for apps where displaying a minimal browser interface is beneficial. For example, use it for a news reading or other general reading apps that show only the essential browser controls like back and reload buttons, providing a cleaner and less distracting interface.
     * 'browser' : Opens the app in a conventional browser tab or new window, using the platform-specific convention for opening links. Use this value for apps that are designed to be used within a browser context, where full browser functionality is needed. This is the default value if no `display` mode is specified.
     * 
     * @link https://w3c.github.io/manifest/#display-member
     * 
     * @var \DyonMulya\CodeIgniter4Favicons\Enumerations\WebApplicationManifestDisplay | string
     */
    public $display = 'SET_YOUR_APPLICATION_DISPLAY';

    /**
     * @var \DyonMulya\CodeIgniter4Favicons\Enumerations\WebApplicationManifestOrientation | string
     */
    public $orientation = 'SET_YOUR_APPLICATION_ORIENTATION';

    /**
     * ---------------------------------------------------
     * Background Color
     * ---------------------------------------------------
     * 
     * Used to specify an initial background color for your application. This color appears in the application window before your application's stylesheets have loaded.
     * 
     * @link https://w3c.github.io/manifest/#background_color-member
     * 
     * @var string #hexcolor | rgb()
     */
    public string $backgroundColor = 'SET_YOUR_APPLICATION_BACKGROUND_COLOR';

    /**
     * ---------------------------------------------------
     * Theme Color
     * ---------------------------------------------------
     * 
     * Used to specify the default color for your application's user interface. This color may be applied to various browser UI elements, such as the toolbar, address bar, and status bar. It can be particularly noticeable in contexts like the task switcher or when the app is added to the home screen.
     * 
     * @link https://w3c.github.io/manifest/#theme_color-member
     * 
     * @var string #hexcolor | rgb()
     */
    public string $themeColor = 'SET_YOUR_APPLICATION_THEME_COLOR';

    /**
     * ---------------------------------------------------
     * Tile Color
     * ---------------------------------------------------
     * 
     * @var string #hexcolor | rgb()
     */
    public string $tileColor = 'SET_YOUR_APPLICATION_TILE_COLOR';
    ...
}
```

<h4>app/Config/Favicons.php</h4>

```php
class Favicons extends BaseConfig {
    /**
     * ---------------------------------------------------
     * Type
     * ---------------------------------------------------
     * 
     * 'image' : Create a favicon from the application logo that has been set in `$logo` in "app/Config/App.php"
     * 'digit' : Create a letter avatar to serve as a favicon.
     * 
     * Default is 'image'.
     * 
     * @var string
     */
    public string $type = 'SET_FAVICON_GENERATOR_TYPE';

    /**
     * ---------------------------------------------------
     * Output
     * ---------------------------------------------------
     * 
     * Favicons URI base, relative to baseURL.
     * If this is empty, then a favicon will be generated in the public folder (FCPATH).
     * 
     * @var string
     */
    public string $output = 'SET_FAVICONS_OUTPUT';

    /**
     * ---------------------------------------------------
     * Font Family
     * ---------------------------------------------------
     * 
     * If you choose the "digit" type, you can choose the font type to later generate the character style for your avatar.
     * 
     * @var string
     */
    public string $fontFamily = 'SET_FAVICON_FONT_FAMILY_FILEPATH';

    /**
     * ---------------------------------------------------
     * Icon Color
     * ---------------------------------------------------
     * 
     * If you choose the "digit" type, set the base color of your avatar.
     * 
     * @var string #hexcolor | rgb()
     */
    public string $iconColor = 'SET_ICON_COLOR_FOR_FAVICON_DIGIT';

    /**
     * ---------------------------------------------------
     * Color
     * ---------------------------------------------------
     * 
     * If you choose the "digit" type, set the character color for your avatar.
     * If you leave this configuration blank, the system will automatically adjust the character contrast according to the `$iconColor` you have set.
     * 
     * @var string #hexcolor | rgb()
     */
    public string $color = 'SET_CHARACTER_COLOR_FOR_FAVICON_DIGIT';

    /**
     * ---------------------------------------------------
     * Background Color
     * ---------------------------------------------------
     * 
     * @var string #hexcolor | rgb()
     */
    public string $backgroundColor = 'SET_BACKGROUND_COLOR_FOR_FAVICON_DIGIT';
}
```

<h2>Generate Favicons</h2>

<p>To create a favicon, you simply run a few spark commands to generate favicons from image or digit.</p>

<h3>From Image</h3>

```bash
php spark favicons:image
```

<p>Generate favicons based on the configuration set in the <code>$logo</code> property in <strong>app/Config/App.php</strong></p>

<h4>Arguments</h4>

<i>No arguments required</i>

<h4>Options</h4>

<dl>
    <dt><code>--force</code></dt>
    <dd>Force overwrite existing file.</dd>
    <dd><i>Type</i>: bool</dd>
</dl>

<h3>From Digit</h3>

```bash
php spark favicons:digit
```

<h4>Arguments</h4>

<i>No arguments required</i>

<h4>Options</h4>

<dl>
    <dt><code>--force</code></dt>
    <dd>Force overwrite existing file.</dd>
    <dd><i>Type</i>: bool</dd>
</dl>

<h2>Generate Tags</h2>

<h3>With Filter</h3>

<p></p>

```php
class Filters extends BaseFilters {
    ...
    /**
     * Configures aliases for Filter classes to
     * make reading things nicer and simpler.
     *
     * @var array<string, class-string|list<class-string>>
     *
     * [filter_name => classname]
     * or [filter_name => [classname1, classname2, ...]]
     */
    public array $aliases = [
        'csrf'          => CSRF::class,
        'toolbar'       => DebugToolbar::class,
        'honeypot'      => Honeypot::class,
        'invalidchars'  => InvalidChars::class,
        'secureheaders' => SecureHeaders::class,
        'cors'          => Cors::class,
        'forcehttps'    => ForceHTTPS::class,
        'pagecache'     => PageCache::class,
        'performance'   => PerformanceMetrics::class,

        'favicons'      => \DyonMulya\CodeIgniter4Favicons\Filters\FaviconsFilter,
    ];

    /**
     * List of filter aliases that are always
     * applied before and after every request.
     *
     * @var array{
     *     before: array<string, array{except: list<string>|string}>|list<string>,
     *     after: array<string, array{except: list<string>|string}>|list<string>
     * }
     */
    public array $globals = [
        'before' => [
            // 'honeypot',
            // 'csrf',
            // 'invalidchars',
        ],
        'after' => [
            // 'honeypot',
            // 'secureheaders',
            'favicons',
        ],
    ];
    ...
}
```

<h3>With Helper</h3>

```php
<html>
    <head>
        ...
        <?= faviconTags(); ?>
        ...
    </head>
</html>
```