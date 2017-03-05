# Auroramax 360
[The auroamax live cam](http://www.asc-csa.gc.ca/eng/astronomy/auroramax/) located in Yellowknife, NWT, Canada. The videos are archived as MP4 1920x1080 30 fps for time compression of 300 seconds of recorded time per second of video - about 4 minutes per evening.

This is an experiment to take the spherical 360 mp4 encoded 1920p file and view it using YouTube's 360 video feature

<img width="534" alt="screen shot 2017-03-04 at 8 00 50 pm" src="https://cloud.githubusercontent.com/assets/3287519/23583547/a01290ea-0115-11e7-97b3-4d682a704bf0.png">

*Initial spherical 180 fisheye video input*


<img width="534" alt="screen shot 2017-03-04 at 9 09 05 pm" src="https://cloud.githubusercontent.com/assets/3287519/23583891/e41a2c40-011e-11e7-92fc-621d33600d19.png">

*Equirectangular distortion*

<img width="534" alt="screen shot 2017-03-04 at 8 04 34 pm" src="https://cloud.githubusercontent.com/assets/3287519/23583566/d594b41e-0115-11e7-8381-bb6331501386.png">

*YouTube 360 video output*

## Camera system
```
Longitude: 114°21'W
Latitude: 62°26'N
Lens: 180° fisheye
ISO: 500
Aperture: 2.8
Exposure time: 5 seconds
Exposure frequency: 6/minute
```

# Conversion Procedure
The conversion is not perfect but does work. Overall the qualifty is not high since the image area actually converted to immersive 360 is `1080*1080px`

## Download
Most recent night's HD video: 
[auroramax.phys.ucalgary.ca/recent/recent_1080p.mp4](http://auroramax.phys.ucalgary.ca/recent/recent_1080p.mp4)

## Conversion
Adobe After Effects to do polar to equirectangular transform

1. import video to a `1080px*1080px` sequence called `square`
2. create a second `2160px*1080px` sequence called `HD` and insert `square` into it
3. distort the `square` layer using `effect > distort > polar coordinates` as follows
4. polar coordinate effect settings: `interpolation: 100%`, `polar to rect`
3. select `layer > transform > fit to comp` to stretch square to fit the extent of HD. 
4. add to render queue as `mp4`, `1920*1080`, `3mbps`
5. render to file, for example `auroramax360-20170303.mp4`

## Add metadata for YouTube consumption
1. Download the 360 video metadata injector from for [Mac](https://github.com/google/spatial-media/releases/download/v2.0/360.Video.Metadata.Tool.mac.zip) or [Windows](https://github.com/google/spatial-media/releases/download/v2.0/360.Video.Metadata.Tool.win.zip)
2. open the app select `open` and choose your new video file
3. only select the `My video is spherical (360) option
4. select `inject metadata` a copy of the video file will be made by the application

## Upload
Upload to YouTube, no special options need to be selected. Should work using motion sensors on a phone as any youtube 360 video

## Sample
[sample 360 conversion video](https://youtu.be/JIaGnnANCAo)
