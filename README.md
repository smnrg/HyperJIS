# HyperJIS Keyboard Layout

HyperJIS is a custom keyboard layout based on the JIS (Japanese Industrial Standard) keyboard, designed to enhance typing efficiency, ergonomics, and productivity. This layout incorporates various modifications and features, such as a dedicated hyper key, window tiling keys, and extensive remapping of modifier keys while mantaining a similarity with the US QWERTY layout.

## Features

- **Optimized for efficiency**: HyperJIS reduces finger travel and minimizes awkward key combinations, resulting in a more comfortable and efficient typing experience.
- **Familiar QWERTY base**: The layout maintains a significant similarity to the US QWERTY layout, making it easy for users to adapt while still benefiting from the enhancements.
- **Dedicated hyper key**: A first-class hyper key is available for custom launchers, triggering scripts, or executing complex actions using tools like Keyboard Maestro.
- **Window tiling keys**: Integrated window tiling keys allow for quick and easy management of windows and workspaces (powered by a tiling utility, such as Swish.)
- **Extensive modifier key remapping**: Modifier keys have been extensively remapped to optimize their placement and reduce conflicts with common shortcuts.
- **Cross-platform compatibility**: HyperJIS can be easily replicated across various keyboards, ensuring a consistent and seamless typing experience on all your devices.
- **Customizable**: Single modifications, such as the tiling keys, can be individually disabled to retain the arrow keys or use your preferred tiling utility.

## Installation

### macOS

The current installation instructions are specific to macOS and have been tested with the most recent JIS Apple Magic Keyboard wireless (with or without Touch ID) and recent Apple laptops with JIS keyboard. To install and use the HyperJIS keyboard layout on macOS, follow these steps:

1. Download the HyperJIS layout files from the [releases page](https://github.com/smnrg/hyperjis/releases).
2. Install Karabiner Elements from [https://karabiner-elements.pqrs.org/](https://karabiner-elements.pqrs.org/).
3. Copy the ```karabiner.json``` file from the HyperJIS layout files to your Karabiner Elements configuration directory (usually ```~/.config/karabiner```).
4. Open Karabiner Elements and enable the HyperJIS layout from the preferences.
5. (Optional) Install the Swish utility to enable window tiling functionality from [https://highlyopinionated.co/swish/](https://highlyopinionated.co/swish/).

### Linux and Windows

While the provided installation files are specific to macOS, it is possible to implement the HyperJIS layout on Linux and Windows using alternative tools:

- For Linux, consider using tools like xcape, xmodmap, or AutoKey to remap keys and create custom shortcuts.
- On Windows, tools such as AutoHotkey, SharpKeys, or KeyTweak can be used to achieve similar functionality.

The exact implementation steps may vary depending on the chosen tools and your specific Linux distribution or Windows version.

## Usage

Once installed, the HyperJIS layout will be active whenever you use your keyboard. You can use the dedicated hyper key in combination with other keys to trigger custom actions or scripts, such as Keyboard Maestro. The window tiling keys allow you to easily manage and arrange windows on your screen.

For a complete list of key mappings and features, please refer to the [user guide](USERGUIDE.md).

## Contributing

Contributions to the HyperJIS project are welcome! If you have any ideas, suggestions, or bug reports, please open an issue on the [GitHub repository](https://github.com/yourusername/hyperjis/issues). If you'd like to contribute code or improvements, feel free to submit a pull request.

## License

The HyperJIS keyboard layout is licensed under the [GNU General Public License v3.0](LICENSE). By using or distributing this layout, you agree to comply with the terms and conditions of this license.

## Acknowledgements

HyperJIS was inspired by various keyboard layout projects and builds upon the work of the mechanical keyboard community. Special thanks to the creator of Karabiner Elements for this invaluable tool.

## Contact

For any questions, feedback, or inquiries, please contact the project maintainer at https://simone.org/about.
