# ColorGen

## Introduction

`ColorGen` is a command-line tool designed to generate color assets and code from a human-readable text file. This tool is particularly useful for designers and developers working on Xcode projects, as it simplifies the process of managing color palettes. The project is a successor to the `RMRColorTools` project, rewritten in Swift for better integration with the Swift Package Manager.

### Key Features
- Define colors in hex format, including support for dark mode.
- Create aliases for colors to promote reuse and consistency.
- Generate .xcassets catalogs and Swift code for easy integration into Xcode projects.

## Usage Example

Create a file named `MyAppColors.palette` with the following content:

```plaintext
// MyAppColors.palette
//
// Lines beginning with // are ignored by the parser, so you can add comments for your team members.
//
// Or you can make comments be generated into the output file by adding them after the color name (see below)

// Define an opaque color in RRGGBB Hex Format. e.g. #FFEE24.   (# character is required!)
#RRGGBB ColorName Add some comments that should be generated into the output file.

// Or in RRGGBBAA format if you need transparency
#RRGGBBAA ColorNameTranslucent

// Perhaps you want to support Dark Mode.  Just add a second hex value after the first one.  The first is always 'Any' and the second is for dark mode.
#FF0000 #AA0000 Red You can see that the second value is darker than the first

#010101 _almostBlack This is a private color and will not be exported.

// Create an Alias to an already defined color.  You can see the pattern: $ExistingColorname AliasName.  ($ character required!)
$ColorName MainTitleText

$_almostBlack SecondaryTextColor But private colors can be used to generate 'functional' color names without exposing the abstract name to (say) a developer

// You should ideally define your colors at the top, and all aliases below them!
```

Run the following command to generate the color assets and Swift code:

```sh
colorgen MyAppColors.palette
```

## Installation

To install `ColorGen`, you can use the Swift Package Manager or download a pre-built binary.

### Swift Package Manager

Add the following dependency to your `Package.swift` file:

```swift
dependencies: [
    .package(url: "https://github.com/mlamina/ColorGen", from: "1.0.0")
]
```

### Pre-built Binary

Download the pre-built binary from the [releases page](https://github.com/mlamina/ColorGen/releases) and place it in your desired location.

## Building and Testing

### Building

To build the project, run the following command:

```sh
swift build
```

To create a universal binary for both Intel and M1 Macs, run the `build_fat_binary.sh` script:

```sh
./build_fat_binary.sh
```

### Testing

To run the tests, use the following command:

```sh
swift test
```

This will execute the unit tests and ensure that the tool is working as expected.
