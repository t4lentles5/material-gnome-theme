# Material GTK Theme (Streamlined Fork)

A clean, decoupled fork of [SakibShahariar/material-gnome-theme](https://github.com/SakibShahariar/material-gnome-theme) stripped of GNOME Shell components, heavy static screenshot assets, and redundant theme palettes. Specially tailored for dynamic theming engines in lightweight compositors (e.g. **Hyprland** with **Quickshell**, Matugen, or custom scripts).

---

## 📂 Repository Structure

```text
material-gnome-theme/
├── gtk-3.0/         # GTK3 Stylesheets & Default Colors
│   ├── colors.css   # Dynamic / Fallback color variables (@define-color)
│   ├── gtk.css      # GTK3 widget styling
│   └── gtk-dark.css # GTK3 dark variant
├── gtk-4.0/         # GTK4 & Libadwaita Stylesheets
│   ├── colors.css   # Dynamic / Fallback color variables (:root { --... })
│   ├── gtk.css      # GTK4 widget styling
│   └── gtk-dark.css # GTK4 dark variant
├── index.theme      # Metatheme metadata descriptor
├── LICENSE          # GPL-3.0 License
└── README.md
```

---

## 🚀 How it Works with Dynamic Theming (e.g. Quickshell / Hyprland)

Both `gtk.css` and `gtk-dark.css` in `gtk-3.0` and `gtk-4.0` import `colors.css`.

Instead of relying on static pre-packaged palettes or a monolithic GNOME installer, tools like Quickshell's `apply_theme.py` can dynamically write your desktop scheme directly into `colors.css`:

### GTK 3.0 Directives (`gtk-3.0/colors.css`)
```css
@define-color primary #a77ef5;
@define-color on_primary #030107;
@define-color primary_container #120e1d;
@define-color secondary #d1d1d1;
@define-color background #030107;
@define-color on_surface #d1d1d1;
...
```

### GTK 4.0 / Libadwaita Variables (`gtk-4.0/colors.css`)
```css
:root {
  --primary: #a77ef5;
  --on_primary: #030107;
  --primary_container: #120e1d;
  --secondary: #d1d1d1;
  --background: #030107;
  --on_surface: #d1d1d1;
  ...
}
```

---

## 🛠️ Installation & Setup

1. **Clone to local themes directory**:
   ```bash
   git clone https://github.com/t4lentles5/material-gnome-theme.git ~/.themes/Material-Gnome
   ```

2. **Set as active GTK Theme**:
   ```bash
   gsettings set org.gnome.desktop.interface gtk-theme "Material-Gnome"
   ```

3. **Link for GTK4 / Libadwaita**:
   ```bash
   mkdir -p ~/.config/gtk-4.0
   ln -sf ~/.themes/Material-Gnome/gtk-4.0/gtk.css ~/.config/gtk-4.0/gtk.css
   ln -sf ~/.themes/Material-Gnome/gtk-4.0/gtk-dark.css ~/.config/gtk-4.0/gtk-dark.css
   ln -sf ~/.themes/Material-Gnome/gtk-4.0/colors.css ~/.config/gtk-4.0/colors.css
   ```

---

## 💡 Used in [Minflair](https://github.com/t4lentles5/minflair)

This fork is actively maintained and integrated into **[Minflair](https://github.com/t4lentles5/minflair)**, a custom Hyprland environment for Arch Linux built around dynamic theming and Quickshell:

- **Color Extraction**: Wallpapers are processed with a Python script utilizing ImageMagick histograms to dynamically extract dominant and accent colors.
- **Dynamic CSS Injection**: Quickshell executes an `apply_theme.py` script to generate `gtk-3.0/colors.css` and `gtk-4.0/colors.css` whenever the theme or wallpaper changes.
- **Full Desktop Cohesion**: GTK3 and GTK4 / Libadwaita applications seamlessly update alongside Hyprland borders, Neovim, Kitty, Starship, and Qt.

---

## 🙏 Acknowledgements & Upstream

- Original theme by [SakibShahariar](https://github.com/SakibShahariar/material-gnome-theme)
- Base GTK styling roots by [Fausto-Korpsvart](https://github.com/Fausto-Korpsvart)

---

## 📜 License

This project is licensed under the **GPL-3.0 License** - see the [LICENSE](LICENSE) file for details.
