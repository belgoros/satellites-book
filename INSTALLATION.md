# Setup your working environment

## For macOS
----

* [General Proxy settings](#proxy-settings)
* [Proxyfy your Terminal](#proxfy-deproxyfy)
* [Install custom Terminal](#custom-terminal)

#### General Proxy settings {#proxy-settings}

Check your network for proxy settings:
* got to `System Preferences` -> `Network` ->  `Wi-Fi`
* click on `Advanced` button
* click on `Proxies` tab
* check `Auto Proxy Discovery`, `Web Proxy (HTTP)` and `Secure Web Proxy (HTTPS)` checkboxes
* select `Web Proxy (HTTP)`
* enter the `gateway.zscaler.net` in the `Web Proxy Server` textfield and `80` in the port number textfield on the right
* select `Secure Web Proxy (HTTPS)` entry
* enter the `gateway.zscaler.net` in the `Web Proxy Server` textfield and `8080` in the port number textfield on the right
* enter the following values in the `Bypass proxy settings for these Hosts & Domains`:
```
*.NEPTUNE.dkcorp.net, *.integration.org, *.dktetrix.net, *.subsidia.org, *.preprod.org, *.withoxylane.com, localhost
```
* click `OK` button in the current window
* click `Apply` button in next window

#### Proxyfy your Terminal {#proxfy-deproxyfy}

* open `.bash_profile` (it should be in your `Home` directory)
* add the following two shell functions to activate/deactivate proxy settinsg for __Terminal__ app:

```shell
function deproxyfy
{
    unset HTTP_PROXY HTTPS_PROXY http_proxy https_proxy
    echo "deproxyfied !"
}

function proxyfy
{
    http_proxy=http://gateway.zscaler.net:80
    HTTP_PROXY=$http_proxy
    https_proxy=$http_proxy
    HTTPS_PROXY=$http_proxy
    no_proxy=127.0.0.1,localhost,10.1*.*.*,preprod.org,withoxylane.com,subsidia.org
    NO_PROXY=$no_proxy
    export http_proxy HTTP_PROXY https_proxy HTTPS_PROXY no_proxy NO_PROXY
    echo "proxyfied !"
}
```

* open your **Terminal** app and run `proxyfy`
* you should see `proxyfied !` (your proxy settinsg are activated for Terminal app)
* run `deproxyfy`
* you should see `deproxyfied !` (your proxy settings are deactivated for Terminal app)

#### Customize your Terminal {#custom-terminal}

You can install any add-on or plugin to manage you Terminal (like [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh), [iTerm](https://iterm2.com/), etc.).
Follow their corresponding guides to setup your Terminal.

#### Homebrew {#homebrew}

Install [Homebrew package manager for macOS](https://brew.sh/) as described in their [documentation](https://docs.brew.sh/Installation.html).

#### Install Java SDK {#java}

Download and install Java SDK from [Oracle download page](http://www.oracle.com/technetwork/java/javase/downloads/index.html).



