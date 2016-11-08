# Blynk Server Docker Image


Runs your own [Blynk Server](https://github.com/blynkkk/blynk-server) in a Docker container instead of relying on Blynk's public server.

[Blynk](http://www.blynk.cc) is the "first drag-n-drop IoT app builder for Arduino, Raspberry Pi, ESP8266, SparkFun boards, and others." Super fun.

## How To Use It

Easy peasy:

```sh
docker run -p 7443:7443 -p 8443:8443 mpherg/blynk-server:latest
```

To persist data, mount a directory into the container:

```sh
docker run -p 7443:7443 -p 8443:8443 -v $(PWD):/data mpherg/blynk-server:latest
```
You can optionally setup your own server.properties file, I have things setup to look in the config volume. Please note that blynk does not support the config file being in the data folder (good security measure). So if your data folder is /blynk/data you cant have the config file in /blynk/data/server.properties. 

```sh
docker run -p 7443:7443 -p 8443:8443 -v /someotherlocation/blynkdata:/data mpherg/blynk-server:latest -v /somelocation/config:/config
```

Or you can use a data volume in another container (check out different data volume techniques [here](https://docs.docker.com/engine/tutorials/dockervolumes/)).

Thanks to [mpherg](https://github.com/mpherg) for his initial design I forked from. 
