# WCAG Themes for VS Code

A collection of WCAG compliant themes for Visual Studio Code that prioritize accessibility.

## Features

- **WCAG Dark Theme**: A dark theme that meets WCAG accessibility guidelines
- **WCAG Light Theme**: A light theme that meets WCAG accessibility guidelines

## Accessibility

These themes are designed with accessibility in mind, following the Web Content Accessibility Guidelines (WCAG) to ensure:

- High color contrast with a minimum ratio of 8:1 for all text and UI elements (exceeding WCAG AAA requirements)
- Clear visual distinctions between different code elements
- Reduced eye strain during extended coding sessions
- Improved readability for users with visual impairments

## Installation

1. Open **Extensions** sidebar panel in VS Code (`Ctrl+Shift+X` / `⌘+Shift+X`)
2. Search for `WCAG Themes`
3. Click **Install**
4. Select **WCAG Dark Theme** or **WCAG Light Theme** from the menu (**File > Preferences > Color Theme** or **Code > Preferences > Color Theme**)

## Development & Testing

Want to preview the themes or contribute? Here's how to set up a development environment:

### Testing the Themes Locally

1. Clone or download this repository
2. Open the folder in VS Code
3. Press `F5` to launch a new Extension Development Host window
4. In the new window, open **Command Palette** (`Ctrl+Shift+P` / `⌘+Shift+P`)
5. Type "Color Theme" and select **Preferences: Color Theme**
6. Select **WCAG Dark Theme** or **WCAG Light Theme** to preview

### Modifying Colors

1. Edit the theme files in the `themes/` directory:
   - `wcag-dark-theme.json` for the dark theme
   - `wcag-light-theme.json` for the light theme
2. After making changes, reload the Extension Development Host window:
   - Press `Ctrl+R` / `⌘+R` in the Extension Development Host window
   - Or use **Command Palette** > **Developer: Reload Window**
3. The theme will update with your changes immediately

### Theme File Structure

Each theme file contains:

- `colors`: UI elements (editor background, sidebar, status bar, etc.)
- `tokenColors`: Syntax highlighting for code elements

Refer to the [VS Code Theme Color Reference](https://code.visualstudio.com/api/references/theme-color) for available color keys.

## Feedback

If you have suggestions or issues, please submit them to the [GitHub repository](https://github.com/iCodeForBananas/wcag-themes).

## License

MIT
