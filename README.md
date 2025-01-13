<h1 align="center">
  <br>
  silero-vad-go
  <br>
</h1>
<h4 align="center">A simple Golang (CGO + ONNX Runtime) speech detector powered by Silero VAD</h4>
<p align="center">
  <a href="https://pkg.go.dev/github.com/cevin/silero-vad-go"><img src="https://pkg.go.dev/badge/github.com/cevin/silero-vad-go.svg" alt="Go Reference"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"></a>
</p>
<br>

### Requirements

- [Golang](https://go.dev/doc/install) >= v1.21
- A C compiler (e.g. GCC)
- ONNX Runtime (v1.18.1)
- A [Silero VAD](https://github.com/snakers4/silero-vad) model (v5)

### Development

This repository is cloned from streamer45/silero-vad-go. Based on the original version, the introduction of onnxruntime dependency is modified to be through `pkg-config`, the purpose is to make it more convenient to use.

#### Linux

##### Install

```sh

# install pkg-config tool
## rhel ( or other rpm based distro version )
dnf install pkg-config
## debian ( or other deb based distro version )
apt install pkg-config

# install onnxruntime
## download onnxruntime
OV=1.20.1
ARCH="x64"
wget https://github.com/microsoft/onnxruntime/releases/download/v${OV}/onnxruntime-linux-${ARCH}-${OV}.tgz
## install
tar xf onnxruntime-linux-${ARCH}-${OV}.tgz
mv onnxruntime-linux-${ARCH}-${OV} /usr/local/onnxruntime
## Generate pc (pkg-config) file
mkdir -p /usr/local/share/pkgconfig
cp /usr/local/onnxruntime/lib/pkgconfig/libonnxruntime.pc /usr/local/share/pkgconfig/
sed -i "s/\/usr\/local/\/usr\/local\/onnxruntime/g" /usr/local/share/pkgconfig/libonnxruntime.pc

# done
```
##### Verify

#### Darwin (MacOS)

##### Install

```sh

brew install onnxruntime pkgconfig
```

##### Verify

```sh

pkg-config --libs libonnxruntime
```

### License

MIT License - see [LICENSE](LICENSE) for full text

