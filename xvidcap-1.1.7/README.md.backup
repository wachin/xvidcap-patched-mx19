
**Parche "xvidcap-1.1.7-automake-1.13.patch"**

En el archivo:

**configure.in**

<br> <br/>
**Linea 8**

Quité:

```bat
AM_CONFIG_HEADER(config.h)
```

Añadí:

```bat
AC_CONFIG_HEADERS(config.h)
```
<br> <br/>
**Linea 17**

Quité:

```bat
AM_PROG_CC_STDC
```

<br> <br/>

**Parche "xvidcap-1.1.7-desktop-entry.patch"**

En el archivo:

**xvidcap.desktop**

<br> <br/>
Quité:

```bat
Encoding=UTF-8
```

Añadí:

```bat
Comment[es]=X11 Grabación de pantalla
```
<br> <br/>
Modifiqué:

```bat
Icon=xvidcap.png
```

por esto:

```bat
Icon=xvidcap
```

<br> <br/>
Modifiqué:

```bat
Categories=GTK;Application;AudioVideo;Video;
```

a esto:

```bat
Categories=GTK;AudioVideo;Video;
```


<br> <br/>
**Parche "xvidcap-1.1.7-ffmpeg-options.patch"**

En el archivo:

**configure.in**

<br> <br/>
Modifiqué esto:

```bat
test x$ac_cv_lib_theora_theora_encode_init = xyes && ac_my_ffmpeg_cfg_lib_switch="${ac_my_ffmpeg_cfg_lib_switch} --enable-libogg --enable-libtheora"
```

Por esto:

```bat
test x$ac_cv_lib_theora_theora_encode_init = xyes && ac_my_ffmpeg_cfg_lib_switch="${ac_my_ffmpeg_cfg_lib_switch} --enable-libtheora"
```

<br> <br/>

**Parche "xvidcap-1.1.7-fix-headers.patch"**

En el archivo:

**/src/codecs.c**

<br> <br/>
Quité esto:

```bat
#include <ffmpeg/avcodec.h>
#include <ffmpeg/avformat.h>
```

Añadí esto:

```bat
#include <avcodec.h>
#include <avformat.h>
```

<br> <br/>
En el archivo

**/src/main.c**

<br> <br/>

quité:

```bat
#include <ffmpeg/avcodec.h>
```

y puse:

```bat
#include <avcodec.h>
```

<br> <br/>

En el archivo:

**/src/xtoffmpeg.c**

<br> <br/>

Quité:

```bat
#include <ffmpeg/avcodec.h>
#include <ffmpeg/avformat.h>
#include <ffmpeg/avdevice.h>

```
y puse

```bat
#include <avcodec.h>
#include <avformat.h>
#include <avdevice.h>
```

<br> <br/>

y quité:

```bat
#include <ffmpeg/swscale.h>
#include <ffmpeg/rgb2rgb.h>
#include <ffmpeg/fifo.h>
```

y puse:

```bat
#include <swscale.h>
#include <rgb2rgb.h>
#include <fifo.h>
```

<br> <br/>

**Parche: "xvidcap-1.1.7-glib.patch"**

En el archivo:

**/src/xvidcap-client-bindings.h**

<br> <br/>

Quité:

```bat
#include <glib/gtypes.h>
#include <glib/gerror.h>
```

```bat

```

```bat

```

```bat

```

```bat

```

```bat

```