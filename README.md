# QRwifi
<table>
  <tr>
    <td style="text-align: center; vertical-align: middle; padding: 0;">
      <img src="https://github.com/SoMoney/qrwifi/blob/main/QRwifi/images/logo_qrwifi.jpeg" alt="QRwifi Logo" width="256" height="256"/>
    </td>
    <td style="text-align: center; vertical-align: middle; padding: 10px;">
      <div style="display: flex; flex-direction: column; justify-content: center; height: 256px;">
        <h1 style="font-size: 64px; font-weight: bold; margin: 0;">QRwifi v1.0.3</h1>
        <p style="font-size: 16px; margin: 10px 0 0 0;">A Python script that generates a WiFi QR join code and overlays it onto the background image of your choice.</p>
      </div>
    </td>
  </tr>
</table>


## Features

- Generate WiFi QR codes for easy network sharing
- Overlay QR codes on custom background images
- Grid-based positioning system (7x7 grid: 1A-7G)
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
  A B C D E F G
1 . . . . . . .
2 . . . . . . .
3 . . . . . . .
4 . . . X . . .  <- X marks true center (4D)
5 . . . . . . .
6 . . . . . . .
7 . . . . . . .
```

### Position Examples:
- `1A` = Top-Left Corner
- `1G` = Top-Right Corner
- `4D` = True Center
- `7A` = Bottom-Left Corner
- `7G` = Bottom-Right Corner

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

- **1.0.3** - Made Grid Larger, added true center
- **1.0.2** - Added a Grid System
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
