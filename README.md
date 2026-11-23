# ASCII Image Converter

Convert an image into ASCII art.

A small Python script that resizes an image, maps each pixel to a character according to its brightness, and writes the result to a text file. It is meant for anyone who wants a quick text rendering of a picture.

## Table of contents

- [ASCII Image Converter](#ascii-image-converter)
	- [Table of contents](#table-of-contents)
	- [How it works](#how-it-works)
	- [Tech stack](#tech-stack)
	- [Repository structure](#repository-structure)
	- [Prerequisites](#prerequisites)
	- [Installation](#installation)
	- [Configuration](#configuration)
	- [Running locally](#running-locally)
	- [Useful scripts](#useful-scripts)
	- [License](#license)

## How it works

1. **Load**: the image is read from the `input` folder with Pillow.
2. **Resize**: the image is scaled to `WIDTH` characters. The height follows the original ratio, multiplied by 8/21 to compensate for characters being taller than they are wide.
3. **Brightness**: the value of each pixel is the average of its channels.
4. **Mapping**: the value is mapped to a character of the `ASCII` string, which is sorted from lightest to darkest. With `COLOR_INVERSION` enabled, the string is reversed.
5. **Output**: the result is printed to the console and written to `output/<image name>.txt`.

## Tech stack

| Layer | Technologies |
| --- | --- |
| Language | Python 3 |
| Image processing | Pillow |

## Repository structure

```
.
├── input/        Source images
├── output/       Generated text files
├── config.py     Conversion settings
└── main.py       Conversion script
```

The `.idea` folder contains PyCharm project files.

## Prerequisites

- [Python](https://www.python.org/) 3
- [Pillow](https://python-pillow.org/) (`pip install pillow`)

## Installation

```bash
git clone git@github.com:maxencebonamy/ASCII-Image-Converter.git
cd ASCII-Image-Converter
pip install pillow
```

## Configuration

Settings are constants in `config.py`.

| Variable | Description | Example |
| --- | --- | --- |
| `WIDTH` | Width of the output, in characters | `100` |
| `ASCII` | Characters ranked from lightest to darkest | `" .'`^\",:;Il!i>..."` |
| `IMAGE_NAME` | Name of the file to convert, located in `input` | `"example.jpg"` |
| `COLOR_INVERSION` | Invert the brightness mapping | `True` |

`IMAGE_NAME` must have a three-letter extension: the output name is built by removing its last four characters.

## Running locally

Put the image in the `input` folder, set `IMAGE_NAME` in `config.py`, then run:

```bash
python main.py
```

The text is printed to the console and saved to `output/<image name>.txt`. The repository ships with `input/example.jpg` and its result in `output/example.txt`.

## Useful scripts

| Command | Effect |
| --- | --- |
| `python main.py` | Convert the image set in `IMAGE_NAME` |

## License

This project is licensed under the [MIT License](LICENSE).
