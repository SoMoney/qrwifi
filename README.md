# QRwifi

A Python script that generates WiFi QR codes and overlays them onto background images using an intuitive grid positioning system.

## Features

- Generate WiFi QR codes for easy network sharing
- Overlay QR codes on custom background images
- Grid-based positioning system (5x6 grid: 1A-5F)
- Customizable QR code size
- Both interactive and command-line modes
- Support for various WiFi encryption types (WPA, WEP, etc.)
- Cross-platform compatibility

## Prerequisites

### Ubuntu/Debian
```bash
sudo apt install -y python3 python3-pip python3-venv
```

### Python Dependencies
```bash
pip install qrcode Pillow
```

## Grid Positioning System

The script uses a 5x6 grid system for positioning QR codes on your background image:

```
  A B C D E F
1 . . . . . .
2 . . . . . .
3 . . . . . .
4 . . . . . .
5 . . . . . .
```

### Position Examples:
- `1A` = Top-Left Corner
- `1F` = Top-Right Corner
- `5A` = Bottom-Left Corner
- `5F` = Bottom-Right Corner
- `3C` = Center-Left
- `3D` = Center-Right

## Usage

### Interactive Mode
Run the script without arguments for guided setup:
```bash
python3 QRwifi
```

### Command Line Mode
Generate QR codes directly with all parameters:
```bash
python3 qrwifi.py --ssid "MyWiFi" --password "mypassword" --encryption "WPA" \
                  --input "background.png" --output "wifi_qr.png" --position "3D" --size 300
```

### Command Line Options

| Option | Description | Default |
|--------|-------------|---------|
| `--ssid` | WiFi network name | Required |
| `--password` | WiFi password | Required |
| `--encryption` | Encryption type (WPA/WEP/WPA2) | WPA |
| `--input` | Background image path | Required |
| `--output` | Output image path | Required |
| `--position` | Grid position (1A-5F) | Required |
| `--size` | QR code size in pixels | 325 |
| `--help-grid` | Show grid positioning help | - |

### Examples

#### Basic WiFi QR Code
```bash
python3 QRwifi --ssid "CoffeeShop_WiFi" --password "coffee123" \
                  --input "cafe_background.jpg" --output "cafe_wifi_qr.png" --position "1F"
```

#### Large QR Code in Center
```bash
python3 QRwifi --ssid "HomeNetwork" --password "supersecret" \
                  --input "home_photo.png" --output "home_wifi.png" \
                  --position "3D" --size 400
```

#### Show Grid Help
```bash
python3 QRwifi --help-grid
```

## Supported Image Formats

### Input Formats
- PNG
- JPEG/JPG
- BMP
- TIFF
- GIF

### Output Formats
- PNG (recommended for transparency)
- JPEG/JPG
- BMP

## Error Handling

The script includes comprehensive error handling for:
- Missing input files
- Invalid grid positions
- Unsupported image formats
- File permission issues
- Invalid QR code parameters

## Author

**Michael Zietlow**

## Version History

- **1.0.1** - Current version with grid positioning system
- **1.0.0** - Initial release

## Troubleshooting

### Common Issues

1. **"Module not found" error**
   ```bash
   pip install qrcode Pillow
   ```

2. **"Permission denied" error**
   ```bash
   chmod +x QRwifi
   ```

3. **"Image not found" error**
   - Verify the input image path exists
   - Check file permissions

4. **QR code not scanning properly**
   - Ensure sufficient contrast with background
   - Try increasing QR code size
   - Use a simpler background image

### Getting Help

- Use `python3 QRwifi --help` for command options
- Use `python3 QRwifi --help-grid` for positioning help
- Run in interactive mode for guided setup

### Pip PreRequisites 
```
qrcode==7.4.2
Pillow==10.0.0
```
