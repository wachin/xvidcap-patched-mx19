Hi to all, I want to make it working fine XvidCap but can't enable record with audio. If I put in a terminal after compile with:

<code>
padsp xvidcap --audio yes --cap_geometry 1280x720[+200+200] --fps 30 --quality 100 --file "Su video.mov"</code>

But Audio is not present:

![](imagen-1.png)

Is possible to launch with:

<code>
padsp xvidcap
</code>

![](imagen-2.png)

The next are the steps I do to try to make it working in:

MX Linux 19.3 x386

https://mxlinux.org/

but it doesn't work yet

************************

**DEPENDS**

<code>
sudo apt install libglade2-dev libxmu-dev docbook-utils docbook-to-man docbook2x gnome-doc-utils libxml-perl libavcodec-dev libflac-dev libdbus-glib-1-dev
</code>

Is necessary to download and install:

https://packages.debian.org/stretch/scrollkeeper

and that is inside the folder:

/03-deb-depend

In the source code folder edit:

debian/rules

in the line that said:

CFLAGS = -Wall -g

change to:

CFLAGS = -Wall -g -lX11 -ldl -lXext



**********************************************



**CHANGES I MADE:**

In the source code:

01-source-code

I made the next changes:


**Parche "xvidcap-1.1.7-automake-1.13.patch"**

in the file:

**configure.in**

<br> <br/>
**Linea 8**

change:

```bat
AM_CONFIG_HEADER(config.h)
```

for:

```bat
AC_CONFIG_HEADERS(config.h)
```
<br> <br/>
**Linea 17**

delete:

```bat
AM_PROG_CC_STDC
```

<br> <br/>

**Parche "xvidcap-1.1.7-desktop-entry.patch"**

In the file:

**xvidcap.desktop**

<br> <br/>
change to:

```bat
Encoding=UTF-8
```

Add:

```bat
Comment[es]=X11 Grabación de pantalla
```
<br> <br/>
Change this:

```bat
Icon=xvidcap.png
```

for thiso:

```bat
Icon=xvidcap
```

<br> <br/>
Change this:

```bat
Categories=GTK;Application;AudioVideo;Video;
```

for this:

```bat
Categories=GTK;AudioVideo;Video;
```


<br> <br/>
**Parche "xvidcap-1.1.7-ffmpeg-options.patch"**

In the file:

**configure.in**

<br> <br/>
Change this:

```bat
test x$ac_cv_lib_theora_theora_encode_init = xyes && ac_my_ffmpeg_cfg_lib_switch="${ac_my_ffmpeg_cfg_lib_switch} --enable-libogg --enable-libtheora"
```

for this:

```bat
test x$ac_cv_lib_theora_theora_encode_init = xyes && ac_my_ffmpeg_cfg_lib_switch="${ac_my_ffmpeg_cfg_lib_switch} --enable-libtheora"
```

<br> <br/>

**Parche "xvidcap-1.1.7-fix-headers.patch"**

In the file:

**/src/codecs.c**

<br> <br/>
Change this:

```bat
#include <ffmpeg/avcodec.h>
#include <ffmpeg/avformat.h>
```

for this:

```bat
#include <avcodec.h>
#include <avformat.h>
```

<br> <br/>
In the file

**/src/main.c**

<br> <br/>
change this:

```bat
#include <ffmpeg/avcodec.h>
```

for this:

```bat
#include <avcodec.h>
```

<br> <br/>
In the file:

**/src/xtoffmpeg.c**

<br> <br/>
change:

```bat
#include <ffmpeg/avcodec.h>
#include <ffmpeg/avformat.h>
#include <ffmpeg/avdevice.h>

```
for this:

```bat
#include <avcodec.h>
#include <avformat.h>
#include <avdevice.h>
```

<br> <br/>
Delete:

```bat
#include <ffmpeg/swscale.h>
#include <ffmpeg/rgb2rgb.h>
#include <ffmpeg/fifo.h>
```

Add:

```bat
#include <swscale.h>
#include <rgb2rgb.h>
#include <fifo.h>
```

<br> <br/>

**Parche: "xvidcap-1.1.7-glib.patch"**

In the file:

**/src/xvidcap-client-bindings.h**
<br> <br/>
Delete:
```bat
#include <glib/gtypes.h>
#include <glib/gerror.h>
```

<br> <br/>

**Parche "xvidcap-1.1.7-shmstr.patch"**

In the file:

**/src/capture.c**

Chage this:

```bat
#include <X11/extensions/shmstr.h>
```

for:

```bat
#include <X11/extensions/shmproto.h>
```
<br> <br/>

**********************


**COMPILATE THE PROGRAM**

To compile put in a terminal:

<code>
LIBS="-lXext -lX11" ./configure --with-x --enable-libmp3lame --enable-libtheora --without-forced-embedded-ffmpeg
make
sudo make install
</code>


Run with this example:


<code>
padsp xvidcap --audio yes --cap_geometry 1280x720[+200+200] --fps 30 --quality 100 --file "Su video.mov"
</code>


But audio is not enabled:

xvidcap audio support is not present in this binary


I some of you can make it working please said me at:

wachin.id@gmail.com

********************************

BASED IN:

Bug #1113263 “./configure fails with cannot run /bin/bash ./conf...” : Bugs : Guitar Tuner
https://bugs.launchpad.net/guitartuner/+bug/1113263

axiak/xvidcap-pulseaudio: Xvidcap support for native pulseaudio and maybe alsa
https://github.com/axiak/xvidcap-pulseaudio
