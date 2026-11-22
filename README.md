# Pixel Adventure

A colorful 2D platform adventure built with **Flutter** and the **Flame engine**. Guide Mask Dude through tiled levels, collect fruit, avoid moving hazards and enemies, and reach the checkpoint to continue the adventure.

[![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?logo=flutter&logoColor=white)](https://flutter.dev)
[![Flame](https://img.shields.io/badge/Flame-1.38.2-orange)](https://flame-engine.org)

## Features

- Responsive 2D platformer movement with fixed-timestep physics
- Keyboard and touchscreen controls
- Tiled level loading through `flame_tiled`
- Collectible animated fruits with sound effects
- Moving horizontal and vertical saw traps
- Patrol-and-chase chicken enemies
- Animated checkpoints that advance to the next level
- Scrolling-style pixel backgrounds
- Character, item, enemy, terrain, and HUD sprite animations
- Android, web, and Windows support

## Gameplay

- Move left or right
- Jump over obstacles and enemies
- Collect fruit throughout each level
- Avoid saw traps and chicken enemies
- Stomp chickens from above to defeat them
- Reach a checkpoint to enter the next level

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Move left | `A` or `←` | Joystick left |
| Move right | `D` or `→` | Joystick right |
| Jump | `Space` | Jump button |

### Choosing the input mode

In `lib/pixel_adventure.dart`, set:

```dart
bool showControls = true;
```

- `true` shows the joystick and jump button for **touch controls**.
- `false` hides them and enables **keyboard controls**.

For keyboard play, change the value to:

```dart
bool showControls = false;
```

> Touch controls are intended for mobile and touch devices. Keyboard play requires `showControls` to be `false`.

## Tech Stack

- [Flutter](https://flutter.dev/) — application framework
- [Dart](https://dart.dev/) — primary programming language
- [Flame](https://flame-engine.org/) — 2D game engine
- [flame_tiled](https://pub.dev/packages/flame_tiled) — loading and rendering Tiled maps
- [flame_audio](https://pub.dev/packages/flame_audio) — in-game audio
- [Tiled](https://www.mapeditor.org/) — level editor and map format

## Project Structure

```text
lib/
├── components/
│   ├── background_tile.dart
│   ├── checkpoint.dart
│   ├── chicken.dart
│   ├── collision_block.dart
│   ├── custom_hitbox.dart
│   ├── fruit.dart
│   ├── jumb_button.dart
│   ├── level.dart
│   ├── player.dart
│   ├── saw.dart
│   └── utils.dart
├── main.dart
└── pixel_adventure.dart

assets/
├── audio/
├── images/
│   ├── Background/
│   ├── Enemies/
│   ├── HUD/
│   ├── Items/
│   ├── Main Characters/
│   └── Terrain/
└── tiles/
    ├── Level-01.tmx
    └── Level-02.tmx
```

## Architecture

- `PixelAdventure` is the main Flame game and manages the camera, level loading, player, joystick, jump control, and global audio settings.
- `Level` loads `.tmx` maps and creates gameplay objects from Tiled object layers.
- `Player` handles keyboard input, movement, jump/gravity physics, collision detection, respawning, animations, and checkpoints.
- `Fruit`, `Saw`, `Chicken`, and `Checkpoint` implement collectible, hazard, enemy, and level-progress components.
- `CollisionBlock` and `CustomHitbox` provide tile and character collision boundaries.

## Getting Started

### Prerequisites

- Flutter SDK compatible with Dart `^3.13.1`
- A configured editor such as Android Studio or VS Code
- Platform-specific tools for the device you want to target

Verify your Flutter installation:

```bash
flutter doctor
```

### Run Locally

```bash
git clone https://github.com/NebulaScript3214/pixel_adventure.git
cd pixel_adventure
flutter pub get
flutter run
```

To target a specific supported platform:

```bash
flutter run -d chrome
flutter run -d windows
flutter run -d android
flutter run -d ios
flutter run -d macos
flutter run -d linux
```

Use `flutter devices` to see the available targets on your system.

## 📱 Android APK

[**Download the latest Android APK**](https://github.com/NebulaScript3214/pixel_adventure/releases/latest)



### Development

Analyze the project:

```bash
flutter analyze
```

Run tests:

```bash
flutter test
```

Format Dart source files:

```bash
dart format lib test
```

## Adding Levels

The game loads Tiled `.tmx` files from `assets/tiles/` and uses object and collision layers to build the level.

1. Create or edit a level in Tiled.
2. Save it in `assets/tiles/`.
3. Include collision objects on a layer named `Collisions`.
4. Add spawnable objects to a layer named `Spawnpoints`.
5. Assign the appropriate Tiled class or name:
   - `Player`
   - `Fruit`
   - `Saw`
   - `Checkpoint`
   - `Chicken`
6. Add the level name to `levelNames` in `lib/pixel_adventure.dart`.

### Tiled Object Properties

| Object | Properties |
|---|---|
| Saw | `isVertical`, `offNeg`, `offPos` |
| Chicken | `offNeg`, `offPos` |
| Fruit | Tiled object name determines the fruit sprite |
| Collision | `Platform` class creates a one-way platform; other classes create solid blocks |

## Acknowledgements

Special thanks to **Salem Al-Soumhi** for supervising this project.

The project was also achieved with guidance from **Spellthorn's tutorials**.

## License

MIT

## Author

Ahmad Amin  
Created by [NebulaScript3214](https://github.com/NebulaScript3214).
