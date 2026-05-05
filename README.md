# flutter_libserialport (AppsDevTeam fork)

Fork of [`jpnurmi/flutter_libserialport`](https://github.com/jpnurmi/flutter_libserialport) maintained by [AppsDevTeam](https://github.com/AppsDevTeam).

`flutter_libserialport` is a simple wrapper around the [`libserialport`](https://pub.dev/packages/libserialport) Dart package, utilizing Flutter's build system to build and deploy the [libserialport](https://sigrok.org/wiki/Libserialport) C-library under the hood. This package does not provide any additional API, but merely helps to make the `libserialport` Dart package work "out of the box" without the need of manually building and deploying the `libserialport` C-library.

Supported platforms:
- Linux
- macOS
- Windows
- Android

## Installation

Add to your `pubspec.yaml`:

```yaml
dependencies:
  flutter_libserialport:
    git:
      url: https://github.com/AppsDevTeam/flutter_libserialport.git
      ref: v0.6.0
```

## Usage

See the [upstream documentation](https://pub.dev/packages/flutter_libserialport) and the [`example/`](example/) directory.

![screenshot](https://raw.githubusercontent.com/jpnurmi/flutter_libserialport/main/doc/images/flutter_libserialport.png)

## Releasing

```bash
./scripts/release.sh v0.6.1
```

The script bumps `version:` in `pubspec.yaml`, updates the `ref:` in this README, commits, tags, and pushes.
