# TD-Runway
A [Runway ML](https://runwayml.com) wrapper for [TouchDesigner](https://derivative.ca).

This project is builds on the previous [TD-PoseNet](https://github.com/BarakChamo/TD_PoseNet) and provides a more general-purpose module for interfacing with Runway ML, a simple machine learning model container thate allows quick setup and prototyping with various machine learning models.

It's meant to follow Runway's simplified approach and allow working with a range of classifiers using a single interface.

[Watch this brief intro and tutorial on using TD-Runway on YouTube]()

## Main highlights of this TOX:

### OSC and Socket.io connectivity
With the introduction of [Socket.io](https://socket.io) support in [TouchDesigner](https://docs.derivative.ca/SocketIO_DAT), it's now possible to interface with Runway ML using either OSC or WebSockets.

### Multiple supported Runway models
Unlike `TD-PoseNet`, this modules wraps many diffent model outputs in one allows for easier setup and quick experimentation.
Supported models are:
- `PoseNet` - single and multiple 2D pose estimation
- `Face Landmarks` - higher resolution face landmarks detection
- `YOLOv4` - fast bounding-box based object detection
- `COCO-SSD` - Another object detection network
- `DenseCap` - Rich captioning object detection

*Please note that each model has it's own output format from the DAT output*

Some of these models run locally and some are run remotely on Runway's Cloud(?), but the interface is the same.

## How to use this thing
Runway ML has an ackward networking interface, where `OSC` and `Socket.io` connections need to announce themselves once a model starts running, this is the main challenge for most people wanting to work with Runway ML using external applications. The module handles all networking handshakes and parses the JSON (Why?!?!?) responses from Runway for you.

To use the TOX simply:
- Select the protocol you want to use and make sure the port matches the one specified in Runway's interface
- Select a model that corresponds to the model you have running in Runway ML (from the supported list), run the model locally or remotely
- Click the `Connect` button on the component's parameters panel.

*It's important to only press `Connect` after the model is running, the networking server inside Runway only starts after the model is running. *

Streamed inference data will be available from the output `DAT` of the component - each model has it's own data.

## Model outputs

`To be completed`

## Sharing camera feeds
Most likely, you'll want to use this module alongside Runway ML to clasify incoming video feeds from a camera or a stream.
If you're running Mac OS you're in luck as Mac allows multiple applications to access the same camera at once, Windows does not.

If you're running Windows or want to classify video coming from a TouchDesigner TOP, you have a few options:
- [SpoutCam](https://spout.zeal.co)- A Spout-based virtual-camera that comes pre-installed with Spout
- [NDI Tools virtual camera](https://ndi.tv/tools/) - Awesome virtual camera module for NDI that works really well with the NDI Out TOP.
- [CamTwist Syphon](https://github.com/barrabinfc/camtwist-syphon) - Virtual camera for Syphon for OSX users who want to stream TouchDesigner TOPs to Runway ML.
- 
