# SFML Tetris Game

A small C++/SFML implementation of classic Tetris. This repository is intentionally compact and is a good base for incremental gameplay improvements.
## Image

<img width="983" height="1521" alt="image" src="https://github.com/user-attachments/assets/ef402fed-72a5-44ba-b386-5db92bed11a4" />

## Features

- Falling tetrominoes with left/right movement
- Piece rotation (`Up` arrow)
- Soft drop (`Down` arrow)
- Line clearing
- Lightweight sprite-based rendering (`images/` assets)

## Dependencies

- C++17-compatible compiler (GCC/Clang/MSVC)
- [CMake](https://cmake.org/) 3.16+
- [SFML](https://www.sfml-dev.org/) 2.5+ (graphics, window, system)

### Linux (example)

```bash
sudo apt update
sudo apt install -y build-essential cmake libsfml-dev
```

### Windows (PowerShell + vcpkg)

```powershell
git clone https://github.com/microsoft/vcpkg $env:USERPROFILE\vcpkg
& $env:USERPROFILE\vcpkg\bootstrap-vcpkg.bat

cmake -S . -B build `
  -DCMAKE_TOOLCHAIN_FILE=$env:USERPROFILE\vcpkg\scripts\buildsystems\vcpkg.cmake `
  -DVCPKG_TARGET_TRIPLET=x64-windows
cmake --build build --config Release
```

## Clone

```bash
git clone https://github.com/<your-username>/Tetris.git
cd Tetris
```

## Build

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release
```

## Continuous Integration

GitHub Actions builds on Ubuntu using `cmake`, `g++`, and `libsfml-dev` from `apt` to keep CI simple and reliable.

## Run

```bash
./build/tetris
```

> The game expects `images/` to be beside the executable. The CMake build copies this folder automatically after build.

## Controls

- `↑` Rotate piece
- `←` Move left
- `→` Move right
- `↓` Soft drop (faster fall while held)
- Close window to quit

## Known Limitations

- No score or level progression yet
- No next-piece preview or hold mechanic
- No hard drop
- No game-over screen/reset flow
- No pause/restart hotkeys
- Random piece generation is purely `rand()` based (not 7-bag)

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
