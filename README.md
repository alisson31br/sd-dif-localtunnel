# localtunnel client for sd-webui
https://user-images.githubusercontent.com/75435724/222434466-fae03e4a-aa8a-4a97-a178-e10d454d5071.mp4

[localtunnel](https://github.com/localtunnel/localtunnel) for [AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui)

## Changelog

 * 2023-03-28: Moved installation process to main.py for users running `webui.py` directly

 * 2023-03-27: Added localtunnel warm-up process. In some cases, such as on colab, the initial loading can be very slow, causing timeout issues. Therefore, it is necessary to load localtunnel beforehand by warming it up.

## Requirements

By default, the machine on which the webui is installed must have Node.js v14 installed.  
If a version higher than this is installed, localtunnel client may not work properly.

If you are using a virtual environment, such as virtualenv for Python, Node.js will be installed automatically. But, if Node.js is already installed, it will not be installed again. If the extension does not work properly, you can try uninstalling and then manually reinstalling Node.js.

**NOTE**  This document does not cover Node.js installation. (see https://nodejs.org)

## Installation and Usage

Follow these steps:

1. Go to the "Extensions" tab in the webui
2. Click on the "Install from URL" tab
3. Paste https://github.com/jnyfil/sd-webui-localtunnel-client.git into "URL for extension's git repository" and click install
4. Restart the webui with '--localtunnel' option

```shell
$ ./webui.sh --localtunnel

...
localtunnel connected to https://localtunnel.me
localtunnel is running at https://random-addr-123-123-123-123.loca.lt <-- this adress
Loading weights from /content/stable-diffusion-webui/models/Stable-diffusion/v1-5-pruned.safetensors
Creating model from config: /home/test/stable-diffusion-webui/configs/v1-inference.yaml
...
```
5. (Optional) To connect to a different host, use '--localtunnel-host' flag  
In the example below, [localtunnel-loopback](https://github.com/jnyfil/localtunnel-loopback) was used. 
```shell
$ ./webui.sh --localtunnel --localtunnel-host="http://123.123.123.123:1234"

...
localtunnel connected to http://123.123.123.123:1234
localtunnel is running at http://localhost:7860 <-- this adress
Loading weights from /content/stable-diffusion-webui/models/Stable-diffusion/v1-5-pruned.safetensors
Creating model from config: /home/test/stable-diffusion-webui/configs/v1-inference.yaml
...
```

**Note** that this extension is designed solely for use with the webui and only supports the '--port' and '--host' options. If you want to use different options, do not use this extension and instead use 
[localtunnel](https://github.com/localtunnel/localtunnel)