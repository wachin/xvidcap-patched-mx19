
**Parche "xvidcap-1.1.7-automake-1.13.patch"**

En el archivo:

configure.in

**Linea 8**

Quité:

```bat
AM_CONFIG_HEADER(config.h)
```

Añadí:

```bat
AC_CONFIG_HEADERS(config.h)
```

**Linea 17**

Quité:

```bat
AM_PROG_CC_STDC
```

<br> <br>

**Parche "xvidcap-patched-mx19/xvidcap-1.1.7-desktop-entry.patch"**

En el archivo:

xvidcap.desktop


Quité:

```bat
Encoding=UTF-8
```

Añadí:

```bat
Comment[es]=X11 Grabación de pantalla
```

Modifiqué:

```bat
Icon=xvidcap.png
```

por esto:

```bat
Icon=xvidcap
```


Modifiqué:

```bat
Categories=GTK;Application;AudioVideo;Video;
```

a esto:

```bat
Categories=GTK;AudioVideo;Video;
```


<br/>
**Parche "xvidcap-1.1.7-ffmpeg-options.patch"**

En el archivo:

configure.in

Modifiqué esto:

```bat
test x$ac_cv_lib_theora_theora_encode_init = xyes && ac_my_ffmpeg_cfg_lib_switch="${ac_my_ffmpeg_cfg_lib_switch} --enable-libogg --enable-libtheora"
```

Por esto:

```bat
test x$ac_cv_lib_theora_theora_encode_init = xyes && ac_my_ffmpeg_cfg_lib_switch="${ac_my_ffmpeg_cfg_lib_switch} --enable-libtheora"
```

<br/>
**Parche "xvidcap-1.1.7-fix-headers.patch"**

En el archivo:

/src/codecs.c

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

<br/>
En el archivo

/src/main.c