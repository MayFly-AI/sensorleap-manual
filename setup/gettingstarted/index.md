---
sort: 1
---

# Getting started

**Minimal requirements:** You have a Raspberry Pi with Raspberry Pi OS 64 bit installed (both desktop and lite version are fine). We have tested it with RPI OSkernel 6.1.21-v8+. You also have a Raspberry Pi camera (e.g. v2, v3, HQ or global shutter) attached and working with libcamera.

## On the Raspberry Pi
Start by SSH'ing into your Raspberry Pi.

Then on the Raspberry Pi, clone our code:
```bash
git clone https://github.com/MayFly-AI/mayfly.git
```

Configure with CMake:
```bash
cd mayfly;
mkdir build; cd build;
cmake ..
```

Then compile:
```bash
make mayfly
```

Now start the executable and provide the path to the simple_camera example config.json file:
```bash
./bin/mayfly ../python/examples/simple_camera/config.json
```
This config.json configures a server to stream a 640x480 @ 30 FPS camera stream on port 8999.

## On your machine 

Download the same code to the machine you wish to stream data to:
```bash
git clone https://github.com/MayFly-AI/mayfly.git
```

### Linux
On linux, from mayfly folder:
```bash
pip install .
```

Now enter examples folder:
```bash
cd python/examples/simple_camera
```

Find the IP address of your Raspberry Pi (you can use ifconfig) and run the simple_camera example providing this IP:
```bash
python simple_camera.py --ip XXX.XXX.XXX.XXX --port 8999
```

A cv2 windows should appear with the live stream.

The example simple_camera.py uses the OpenH264 decoder. If you have a NVIDIA GPU, we recommend using the nvdecode decoder. To do this, run:
```bash
python simple_camera_cuda.py --ip XXX.XXX.XXX.XXX --port 8999
```


{% include list.liquid all=true %}