### for mac

```
yarn add puppeteer
```

使用

```
const puppeteer = require('puppeteer')
puppeteer.launch()
```



### for CentOS

```
yum add pango.x86_64 libXcomposite.x86_64 libXcursor.x86_64 libXdamage.x86_64 libXext.x86_64 libXi.x86_64 libXtst.x86_64 cups-libs.x86_64 libXScrnSaver.x86_64 libXrandr.x86_64 GConf2.x86_64 alsa-lib.x86_64 atk.x86_64 gtk3.x86_64 ipa-gothic-fonts xorg-x11-fonts-100dpi xorg-x11-fonts-75dpi xorg-x11-utils xorg-x11-fonts-cyrillic xorg-x11-fonts-Type1 xorg-x11-fonts-misc

yarn add puppeteer
```

### for Docker alpine

#### puppeteer-core

使用内置chromium，需要先安装chromium

```
RUN apk add --no-cache \
    chromium
# Tell Puppeteer to skip installing Chrome. We'll be using the installed package.
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true \
    PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium-browser

yarn add puppeteer-core
```

使用

```
    const puppeteer = require('puppeteer-core')
    puppeteer.launch({
      executablePath: '/usr/bin/chromium-browser',
      // 解决cannot open display
      headless: true,
      args: [
        '--no-sandbox',
        '--disable-setuid-sandbox',
        '--disable-dev-shm-usage'
      ],
    })
```

#### puppeteer

```
apk add yum
yum add pango.x86_64 libXcomposite.x86_64 libXcursor.x86_64 libXdamage.x86_64 libXext.x86_64 libXi.x86_64 libXtst.x86_64 cups-libs.x86_64 libXScrnSaver.x86_64 libXrandr.x86_64 GConf2.x86_64 alsa-lib.x86_64 atk.x86_64 gtk3.x86_64 ipa-gothic-fonts xorg-x11-fonts-100dpi xorg-x11-fonts-75dpi xorg-x11-utils xorg-x11-fonts-cyrillic xorg-x11-fonts-Type1 xorg-x11-fonts-misc

yarn add puppeteer
```

使用

```
    const puppeteer = require('puppeteer')
    puppeteer.launch({
      headless: true,
      args: [
        '--no-sandbox',
        '--disable-setuid-sandbox',
        '--headless',
        '--disable-gpu',
        '--disable-dev-shm-usage'
      ],
    })
```



