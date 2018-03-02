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

* Download and install Java SDK from [Oracle download page](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
* check the installed Java version in your Terminal:
```
java -version
```
You should get the below results (version number could be different depending on SDK version you downloaded in the step before):
```
java version "1.8.0_112"
Java(TM) SE Runtime Environment (build 1.8.0_112-b16)
Java HotSpot(TM) 64-Bit Server VM (build 25.112-b16, mixed mode)
```

#### Install Apache Maven {#maven}

The easiest way to install [Apache Maven](https://maven.apache.org/) is via `brew` command (see [Homebrew](INSTALLATION.md#homebrew) installation section).
* open your Terminal
* run `proxyfy` to enable proxy settings.
* run `brew install maven`
* after the installation finished, check the installed Maven version by running `mvn -v`
* you should get the below result (jdk version could be different depending on your Java version installed in the [Java](INSTALLATION.md#java) section):
```
Maven home: /usr/local/Cellar/maven/3.5.2/libexec
Java version: 1.8.0_112, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk1.8.0_112.jdk/Contents/Home/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.13.3", arch: "x86_64", family: "mac"
```

#### Install Yarn {#yarn}

You can install [Yarn](https://yarnpkg.com/en/) through the Homebrew package manager. This will also install Node.js if it is not already installed.

* open your Terminal
* run `proxyfy` to enable proxy settings.
* install Node JS with Homebrew: `brew install yarn`
* check the installed Node version: `yarn --version`
* you should get the following result: `1.3.2` (displayed version could be different)


